#1.struct raftNode

```go
type raftNode struct {
	// Cache of the latest raft index and raft term the server has seen.
	// These three unit64 fields must be the first elements to keep 64-bit
	// alignment for atomic access to the fields.
	index uint64
	term  uint64
	lead  uint64

	mu sync.Mutex
	// last lead elected time
	lt time.Time

	// to check if msg receiver is removed from cluster
	isIDRemoved func(id uint64) bool

	raft.Node

	// a chan to send/receive snapshot
	msgSnapC chan raftpb.Message

	// a chan to send out apply
	applyc chan apply

	// a chan to send out readState
	readStateC chan raft.ReadState

	// utility
	ticker <-chan time.Time
	// contention detectors for raft heartbeat message
	td          *contention.TimeoutDetector
	heartbeat   time.Duration // for logging
	raftStorage *raft.MemoryStorage
	storage     Storage
	// transport specifies the transport to send and receive msgs to members.
	// Sending messages MUST NOT block. It is okay to drop messages, since
	// clients should timeout and reissue their messages.
	// If transport is nil, server will panic.
	transport rafthttp.Transporter

	stopped chan struct{}
	done    chan struct{}
}
```