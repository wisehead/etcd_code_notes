#1.newLog

```
newLog
--log := &raftLog{
		storage: storage,
		logger:  logger,
	}
--firstIndex, err := storage.FirstIndex()
--lastIndex, err := storage.LastIndex()
--log.unstable.offset = lastIndex + 1
--log.unstable.logger = logger
	// Initialize our committed and applied pointers to the time of the last compaction.
--log.committed = firstIndex - 1
--log.applied = firstIndex - 1	
```