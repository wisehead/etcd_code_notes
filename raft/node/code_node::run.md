#1.node::run

```
node::run
--prevSoftSt := r.softState()
--prevHardSt := emptyState
--for
----if advancec != nil {
			readyc = nil
----} else {
			rd = newReady(r, prevSoftSt, prevHardSt)
			if rd.containsUpdates() {
				readyc = n.readyc
			} else {
				readyc = nil
			}
		}
----if lead != r.lead {
------if r.hasLeader() {
--------if lead == None {
----------r.logger.Infof("raft.node: %x elected leader %x at term %d", r.id, r.lead, r.Term)
--------} else {
----------r.logger.Infof("raft.node: %x changed leader from %x to %x at term %d", r.id, lead, r.lead, r.Term)
--------propc = n.propc
------} else {
--------r.logger.Infof("raft.node: %x lost leader %x at term %d", r.id, lead, r.Term)
--------propc = nil
------}
------lead = r.lead

----select {
------case m := <-propc:
--------m.From = r.id
--------r.Step(m)
------case m := <-n.recvc:
			// filter out response message from unknown From.
			if _, ok := r.prs[m.From]; ok || !IsResponseMsg(m.Type) {
				r.Step(m) // raft never returns an error
			}	
```