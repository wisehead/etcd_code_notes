#1.MemoryStorage::Snapshot

```
MemoryStorage::Snapshot
--ms.Lock()
	defer ms.Unlock()
	return ms.snapshot, nil
```