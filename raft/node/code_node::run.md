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

```