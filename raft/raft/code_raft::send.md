#1.raft::send

```
raft::send
--// send persists state to stable storage and then sends to its mailbox.
--m.From = r.id
--if m.Type == pb.MsgVote || m.Type == pb.MsgPreVote {
		if m.Term == 0 {
			// PreVote RPCs are sent at a term other than our actual term, so the code
			// that sends these messages is responsible for setting the term.
			panic(fmt.Sprintf("term should be set when sending %s", m.Type))
		}
--} else {
		if m.Term != 0 {
			panic(fmt.Sprintf("term should not be set when sending %s (was %d)", m.Type, m.Term))
		}
		// do not attach term to MsgProp, MsgReadIndex
		// proposals are a way to forward to the leader and
		// should be treated as local message.
		// MsgReadIndex is also forwarded to leader.
		if m.Type != pb.MsgProp && m.Type != pb.MsgReadIndex {
			m.Term = r.Term
		}
--}
--r.msgs = append(r.msgs, m)
```