#1.raftLog::firstIndex

```
raftLog::firstIndex
--if i, ok := l.unstable.maybeFirstIndex(); ok {
----return i
--index, err := l.storage.FirstIndex()
```