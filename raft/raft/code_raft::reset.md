#1.raft::reset

```
raft::reset
--if r.Term != term {
		r.Term = term
		r.Vote = None
	}
--r.lead = None

--r.electionElapsed = 0
--r.heartbeatElapsed = 0
--r.resetRandomizedElectionTimeout()

--r.abortLeaderTransfer()

--r.votes = make(map[uint64]bool)
--for id := range r.prs {
		r.prs[id] = &Progress{Next: r.raftLog.lastIndex() + 1, ins: newInflights(r.maxInflight)}
		if id == r.id {
			r.prs[id].Match = r.raftLog.lastIndex()
		}
	}
--r.pendingConf = false
--r.readOnly = newReadOnly(r.readOnly.option)

```