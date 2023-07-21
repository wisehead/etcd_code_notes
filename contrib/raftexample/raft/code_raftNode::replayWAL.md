#1.raftNode::replayWAL

```
raftNode::replayWAL
--snapshot := rc.loadSnapshot()
----rc.snapshotter.Load()
------Snapshotter::Load
--------loadSnap
----------Read(fpath)
------------ioutil.ReadFile(snapname)
------------serializedSnap.Unmarshal(b)
------------snap.Unmarshal(serializedSnap.Data)
--w := rc.openWAL(snapshot)
```