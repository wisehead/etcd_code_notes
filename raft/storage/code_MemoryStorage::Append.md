#1.MemoryStorage::Append

```
MemoryStorage::Append
--first := ms.firstIndex()
--last := entries[0].Index + uint64(len(entries)) - 1
--if first > entries[0].Index {
----entries = entries[first-entries[0].Index:]
--offset := entries[0].Index - ms.ents[0].Index
	switch {
	case uint64(len(ms.ents)) > offset:
		ms.ents = append([]pb.Entry{}, ms.ents[:offset]...)
		ms.ents = append(ms.ents, entries...)
	case uint64(len(ms.ents)) == offset:
		ms.ents = append(ms.ents, entries...)
	default:
		raftLogger.Panicf("missing log entry [last: %d, append at: %d]",
			ms.lastIndex(), entries[0].Index)
	}
```