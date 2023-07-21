#1.raftNode::startRaft

```
raftNode::startRaft
--rc.snapshotter = snap.New(rc.snapdir)
--rc.snapshotterReady <- rc.snapshotter
--oldwal := wal.Exist(rc.waldir)
--rc.wal = rc.replayWAL()
--
```