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
--_, st, ents, err := w.ReadAll()
--rc.raftStorage = raft.NewMemoryStorage()
--if snapshot != nil {
----rc.raftStorage.ApplySnapshot(*snapshot)
--rc.raftStorage.SetHardState(st)
--// append to storage so raft starts at the right place in log
--rc.raftStorage.Append(ents)
--// send nil once lastIndex is published so client knows commit channel is current
	if len(ents) > 0 {
		rc.lastIndex = ents[len(ents)-1].Index
	} else {
		rc.commitC <- nil
	}
```