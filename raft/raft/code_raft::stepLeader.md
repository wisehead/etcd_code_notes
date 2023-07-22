#1.raft::stepLeader

```
raft::stepLeader
--switch m.Type {
----case pb.MsgBeat:
		r.bcastHeartbeat()
		return
----case pb.MsgCheckQuorum:
		if !r.checkQuorumActive() {
			r.logger.Warningf("%x stepped down to follower since quorum is not active", r.id)
			r.becomeFollower(r.Term, None)
		}
		return
----case pb.MsgProp:
		for i, e := range m.Entries {
			if e.Type == pb.EntryConfChange {
				if r.pendingConf {
					r.logger.Infof("propose conf %s ignored since pending unapplied configuration", e.String())
					m.Entries[i] = pb.Entry{Type: pb.EntryNormal}
				}
				r.pendingConf = true
			}
		}
		r.appendEntry(m.Entries...)
		r.bcastAppend()
		return
----case pb.MsgReadIndex:
------if r.quorum() > 1 {
--------
------} else {
--------r.readStates = append(r.readStates, ReadState{Index: r.raftLog.committed, RequestCtx: m.Entries[0].Data})
```