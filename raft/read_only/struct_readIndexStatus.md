#1.struct readIndexStatus

```go
type readIndexStatus struct {
	req   pb.Message
	index uint64
	acks  map[uint64]struct{}
}

```