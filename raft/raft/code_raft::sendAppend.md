#1.raft::sendAppend

```
raft::sendAppend
--term, errt := r.raftLog.term(pr.Next - 1)
--ents, erre := r.raftLog.entries(pr.Next, r.maxMsgSize)
--if errt != nil || erre != nil { // send snapshot if we failed to get term or entries
----m.Type = pb.MsgSnap
----snapshot, err := r.raftLog.snapshot()
----m.Snapshot = snapshot
----sindex, sterm := snapshot.Metadata.Index, snapshot.Metadata.Term
		r.logger.Debugf("%x [firstindex: %d, commit: %d] sent snapshot[index: %d, term: %d] to %x [%s]",
			r.id, r.raftLog.firstIndex(), r.raftLog.committed, sindex, sterm, to, pr)
----pr.becomeSnapshot(sindex)
----r.logger.Debugf("%x paused sending replication messages to %x [%s]", r.id, to, pr)
--} else {
		m.Type = pb.MsgApp
		m.Index = pr.Next - 1
		m.LogTerm = term
		m.Entries = ents
		m.Commit = r.raftLog.committed
		if n := len(m.Entries); n != 0 {
			switch pr.State {
			// optimistically increase the next when in ProgressStateReplicate
			case ProgressStateReplicate:
				last := m.Entries[n-1].Index
				pr.optimisticUpdate(last)
				pr.ins.add(last)
			case ProgressStateProbe:
				pr.pause()
			default:
				r.logger.Panicf("%x is sending append in unhandled state %s", r.id, pr.State)
			}
		}
	}
```