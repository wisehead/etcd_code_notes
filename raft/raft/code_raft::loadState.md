#1.raft::loadState

```
raft::loadState
--if state.Commit < r.raftLog.committed || state.Commit > r.raftLog.lastIndex() {
		r.logger.Panicf("%x state.commit %d is out of range [%d, %d]", r.id, state.Commit, r.raftLog.committed, r.raftLog.lastIndex())
	}
--r.raftLog.committed = state.Commit
--r.Term = state.Term
--r.Vote = state.Vote
```