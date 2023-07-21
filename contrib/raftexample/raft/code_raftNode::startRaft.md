#1.raftNode::startRaft

```
raftNode::startRaft
--rc.snapshotter = snap.New(rc.snapdir)
--rc.snapshotterReady <- rc.snapshotter
--oldwal := wal.Exist(rc.waldir)
--rc.wal = rc.replayWAL()
--rpeers := make([]raft.Peer, len(rc.peers))
--for i := range rpeers {
		rpeers[i] = raft.Peer{ID: uint64(i + 1)}
--c := &raft.Config{
		ID:              uint64(rc.id),
		ElectionTick:    10,
		HeartbeatTick:   1,
		Storage:         rc.raftStorage,
		MaxSizePerMsg:   1024 * 1024,
		MaxInflightMsgs: 256,
	}
--if oldwal {
		rc.node = raft.RestartNode(c)
--} else {
		startPeers := rpeers
		if rc.join {
			startPeers = nil
		}
		rc.node = raft.StartNode(c, startPeers)
	}		
```