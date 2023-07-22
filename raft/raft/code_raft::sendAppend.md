#1.raft::sendAppend

```
raft::sendAppend
--term, errt := r.raftLog.term(pr.Next - 1)
--ents, erre := r.raftLog.entries(pr.Next, r.maxMsgSize)
--if errt != nil || erre != nil { // send snapshot if we failed to get term or entries
----m.Type = pb.MsgSnap
----snapshot, err := r.raftLog.snapshot()
----
```