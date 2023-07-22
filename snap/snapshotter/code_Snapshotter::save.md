#1.Snapshotter::save

```
Snapshotter::save
--fname := fmt.Sprintf("%016x-%016x%s", snapshot.Metadata.Term, snapshot.Metadata.Index, snapSuffix)
	b := pbutil.MustMarshal(snapshot)
	crc := crc32.Update(0, crcTable, b)
	snap := snappb.Snapshot{Crc: crc, Data: b}
	d, err := snap.Marshal()
--err = pioutil.WriteAndSyncFile(filepath.Join(s.dir, fname), d, 0666)

```