#1.raftLog::snapshot

```
raftLog::snapshot
--if l.unstable.snapshot != nil {
		return *l.unstable.snapshot, nil
--return l.storage.Snapshot()
```