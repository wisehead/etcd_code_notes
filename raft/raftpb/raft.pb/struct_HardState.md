#1.struct HardState

```go
type HardState struct {
	Term             uint64 `protobuf:"varint,1,opt,name=term" json:"term"`
	Vote             uint64 `protobuf:"varint,2,opt,name=vote" json:"vote"`
	Commit           uint64 `protobuf:"varint,3,opt,name=commit" json:"commit"`
	XXX_unrecognized []byte `json:"-"`
}

```