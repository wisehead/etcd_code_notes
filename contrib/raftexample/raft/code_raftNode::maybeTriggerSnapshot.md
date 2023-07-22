#1.raftNode::maybeTriggerSnapshot

```
raftNode::maybeTriggerSnapshot
--if rc.appliedIndex-rc.snapshotIndex <= rc.snapCount {
		return
--data, err := rc.getSnapshot()//kvengine interface
--err := rc.saveSnap(snap); 
```