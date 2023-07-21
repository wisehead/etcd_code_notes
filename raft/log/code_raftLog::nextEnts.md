#1.raftLog::nextEnts

```
// nextEnts returns all the available entries for execution.
// If applied is smaller than the index of snapshot, it returns all committed
// entries after the index of snapshot.

raftLog::nextEnts
--off := max(l.applied+1, l.firstIndex())
--if l.committed+1 > off {
----ents, err := l.slice(off, l.committed+1, noLimit)
		if err != nil {
			l.logger.Panicf("unexpected error when getting unapplied entries (%v)", err)
		}
----return ents
```