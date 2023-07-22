#1.raft::maybeCommit

```
raft::maybeCommit
--mis := make(uint64Slice, 0, len(r.prs))
	for id := range r.prs {
		mis = append(mis, r.prs[id].Match)
	}
	sort.Sort(sort.Reverse(mis))
	mci := mis[r.quorum()-1]
--return r.raftLog.maybeCommit(mci, r.Term)
----if maxIndex > l.committed && l.zeroTermOnErrCompacted(l.term(maxIndex)) == term {
		l.commitTo(maxIndex)
		return true
```