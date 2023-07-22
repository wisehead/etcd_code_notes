#1.raft::appendEntry

```
raft::appendEntry
--li := r.raftLog.lastIndex()
	for i := range es {
		es[i].Term = r.Term
		es[i].Index = li + 1 + uint64(i)
	}
--r.raftLog.append(es...)
----l.unstable.truncateAndAppend(ents)
	r.prs[r.id].maybeUpdate(r.raftLog.lastIndex())
	// Regardless of maybeCommit's return, our caller will call bcastAppend.
	r.maybeCommit()
```