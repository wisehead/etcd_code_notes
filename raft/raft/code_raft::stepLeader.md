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
```