#1.raft::Step

```
raft::Step
--switch {
----case m.Term == 0:
		// local message
----case m.Term > r.Term:
------lead := m.From
------if m.Type == pb.MsgVote || m.Type == pb.MsgPreVote {
--------force := bytes.Equal(m.Context, []byte(campaignTransfer))
--------inLease := r.checkQuorum && r.lead != None && r.electionElapsed < r.electionTimeout
--------if !force && inLease {
		 // If a server receives a RequestVote request within the minimum election timeout
		 // of hearing from a current leader, it does not update its term or grant its vote
----------r.logger.Infof("%x [logterm: %d, index: %d, vote: %x] ignored %s from %x [logterm: %d, index: %d] at term %d: lease is not expired (remaining ticks: %d)",
----------return nil			
--------}
--------lead = None
------}
------switch {
--------case m.Type == pb.MsgPreVote:
			// Never change our term in response to a PreVote
--------case m.Type == pb.MsgPreVoteResp && !m.Reject:
			// We send pre-vote requests with a term in our future. If the
			// pre-vote is granted, we will increment our term when we get a
			// quorum. If it is not, the term comes from the node that
			// rejected our vote so we should become a follower at the new
			// term.
--------default:
			r.logger.Infof("%x [term: %d] received a %s message with higher term from %x [term: %d]",
				r.id, r.Term, m.Type, m.From, m.Term)
			r.becomeFollower(m.Term, lead)
		}
```