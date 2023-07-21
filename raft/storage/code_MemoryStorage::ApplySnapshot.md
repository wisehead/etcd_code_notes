#1.MemoryStorage::ApplySnapshot
```
MemoryStorage::ApplySnapshot
--msIndex := ms.snapshot.Metadata.Index
--snapIndex := snap.Metadata.Index
--if msIndex >= snapIndex {
----return ErrSnapOutOfDate
--ms.snapshot = snap
--ms.ents = []pb.Entry{{Term: snap.Metadata.Term, Index: snap.Metadata.Index}}
```