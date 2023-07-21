#1.StartNode

```
StartNode
--r := newRaft(c)
--.becomeFollower(1, None)
--for _, peer := range peers {
		cc := pb.ConfChange{Type: pb.ConfChangeAddNode, NodeID: peer.ID, Context: peer.Context}
		d, err := cc.Marshal()
		if err != nil {
			panic("unexpected marshal error")
		}
		e := pb.Entry{Type: pb.EntryConfChange, Term: 1, Index: r.raftLog.lastIndex() + 1, Data: d}
		r.raftLog.append(e)
	}
--r.raftLog.committed = r.raftLog.lastIndex()
--for _, peer := range peers {
		r.addNode(peer.ID)
	}
```