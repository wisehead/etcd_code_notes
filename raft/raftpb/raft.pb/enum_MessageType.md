#1.MessageType

```go
type MessageType int32

const (
	MsgHup            MessageType = 0
	MsgBeat           MessageType = 1
	MsgProp           MessageType = 2
	MsgApp            MessageType = 3
	MsgAppResp        MessageType = 4
	MsgVote           MessageType = 5
	MsgVoteResp       MessageType = 6
	MsgSnap           MessageType = 7
	MsgHeartbeat      MessageType = 8
	MsgHeartbeatResp  MessageType = 9
	MsgUnreachable    MessageType = 10
	MsgSnapStatus     MessageType = 11
	MsgCheckQuorum    MessageType = 12
	MsgTransferLeader MessageType = 13
	MsgTimeoutNow     MessageType = 14
	MsgReadIndex      MessageType = 15
	MsgReadIndexResp  MessageType = 16
	MsgPreVote        MessageType = 17
	MsgPreVoteResp    MessageType = 18
)

var MessageType_name = map[int32]string{
	0:  "MsgHup",
	1:  "MsgBeat",
	2:  "MsgProp",
	3:  "MsgApp",
	4:  "MsgAppResp",
	5:  "MsgVote",
	6:  "MsgVoteResp",
	7:  "MsgSnap",
	8:  "MsgHeartbeat",
	9:  "MsgHeartbeatResp",
	10: "MsgUnreachable",
	11: "MsgSnapStatus",
	12: "MsgCheckQuorum",
	13: "MsgTransferLeader",
	14: "MsgTimeoutNow",
	15: "MsgReadIndex",
	16: "MsgReadIndexResp",
	17: "MsgPreVote",
	18: "MsgPreVoteResp",
}
var MessageType_value = map[string]int32{
	"MsgHup":            0,
	"MsgBeat":           1,
	"MsgProp":           2,
	"MsgApp":            3,
	"MsgAppResp":        4,
	"MsgVote":           5,
	"MsgVoteResp":       6,
	"MsgSnap":           7,
	"MsgHeartbeat":      8,
	"MsgHeartbeatResp":  9,
	"MsgUnreachable":    10,
	"MsgSnapStatus":     11,
	"MsgCheckQuorum":    12,
	"MsgTransferLeader": 13,
	"MsgTimeoutNow":     14,
	"MsgReadIndex":      15,
	"MsgReadIndexResp":  16,
	"MsgPreVote":        17,
	"MsgPreVoteResp":    18,
}

```