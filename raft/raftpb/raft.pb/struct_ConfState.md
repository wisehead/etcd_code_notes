#1.struct ConfState

```go
type ConfState struct {
	Nodes            []uint64 `protobuf:"varint,1,rep,name=nodes" json:"nodes,omitempty"`
	XXX_unrecognized []byte   `json:"-"`
}
```