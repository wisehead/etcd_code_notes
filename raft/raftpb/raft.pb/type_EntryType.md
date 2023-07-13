#1.type EntryType

```go
type EntryType int32

const (
	EntryNormal     EntryType = 0
	EntryConfChange EntryType = 1
)

var EntryType_name = map[int32]string{
	0: "EntryNormal",
	1: "EntryConfChange",
}
var EntryType_value = map[string]int32{
	"EntryNormal":     0,
	"EntryConfChange": 1,
}

```