#1.struct Snapshot

```go
type Snapshot struct {
	Crc              uint32 `protobuf:"varint,1,opt,name=crc" json:"crc"`
	Data             []byte `protobuf:"bytes,2,opt,name=data" json:"data,omitempty"`
	XXX_unrecognized []byte `json:"-"`
}
```