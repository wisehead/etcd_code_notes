#1.newRaft

```
newRaft
--raftlog := newLog(c.Storage, c.Logger)
--hs, cs, err := c.Storage.InitialState()
----MemoryStorage::InitialState
------return ms.hardState, ms.snapshot.Metadata.ConfState, nil
--peers := c.peers
	if len(cs.Nodes) > 0 {
		if len(peers) > 0 {
			// TODO(bdarnell): the peers argument is always nil except in
			// tests; the argument should be removed and these tests should be
			// updated to specify their nodes through a snapshot.
			panic("cannot specify both newRaft(peers) and ConfState.Nodes)")
		}
		peers = cs.Nodes
	}
--r := &raft{
		id:               c.ID,
		lead:             None,
		raftLog:          raftlog,
		maxMsgSize:       c.MaxSizePerMsg,
		maxInflight:      c.MaxInflightMsgs,
		prs:              make(map[uint64]*Progress),
		electionTimeout:  c.ElectionTick,
		heartbeatTimeout: c.HeartbeatTick,
		logger:           c.Logger,
		checkQuorum:      c.CheckQuorum,
		preVote:          c.PreVote,
		readOnly:         newReadOnly(c.ReadOnlyOption),
	}
--for _, p := range peers {
		r.prs[p] = &Progress{Next: 1, ins: newInflights(r.maxInflight)}
	}
--if !isHardStateEqual(hs, emptyState) {
----r.loadState(hs)	
--if c.Applied > 0 {
		raftlog.appliedTo(c.Applied)
--r.becomeFollower(r.Term, None)
--var nodesStrs []string
--for _, n := range r.nodes() {
		nodesStrs = append(nodesStrs, fmt.Sprintf("%x", n))
	}
```