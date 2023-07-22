#1.raftNode::maybeTriggerSnapshot

```
raftNode::maybeTriggerSnapshot
--if rc.appliedIndex-rc.snapshotIndex <= rc.snapCount {
		return
--data, err := rc.getSnapshot()//kvengine interface
--snap, err := rc.raftStorage.CreateSnapshot(rc.appliedIndex, &rc.confState, data)
--err := rc.saveSnap(snap); 
--compactIndex := uint64(1)
--if rc.appliedIndex > snapshotCatchUpEntriesN {
----compactIndex = rc.appliedIndex - snapshotCatchUpEntriesN
--rc.raftStorage.Compact(compactIndex);//compact log的时候留几条，以防万一，默认留10000条。
--rc.snapshotIndex = rc.appliedIndex//snapshotIndex维护
```