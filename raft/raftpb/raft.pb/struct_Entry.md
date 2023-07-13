#1.struct Entry

```go
type Entry struct {
	Term             uint64    `protobuf:"varint,2,opt,name=Term" json:"Term"`
	Index            uint64    `protobuf:"varint,3,opt,name=Index" json:"Index"`
	Type             EntryType `protobuf:"varint,1,opt,name=Type,enum=raftpb.EntryType" json:"Type"`
	Data             []byte    `protobuf:"bytes,4,opt,name=Data" json:"Data,omitempty"`
	XXX_unrecognized []byte    `json:"-"`
}
```