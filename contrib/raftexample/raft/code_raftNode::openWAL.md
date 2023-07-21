#1.raftNode::openWAL

```
raftNode::openWAL
--walsnap := walpb.Snapshot{}
--if snapshot != nil {
		walsnap.Index, walsnap.Term = snapshot.Metadata.Index, snapshot.Metadata.Term
--w, err := wal.Open(rc.waldir, walsnap)
----openAtIndex(dirpath, snap, true)
```