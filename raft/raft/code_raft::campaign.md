#1.raft::campaign

```
raft:campaign
--if t == campaignPreElection {
		r.becomePreCandidate()
		voteMsg = pb.MsgPreVote
		// PreVote RPCs are sent for the next term before we've incremented r.Term.
		term = r.Term + 1
--} else {
		r.becomeCandidate()
		voteMsg = pb.MsgVote
		term = r.Term
--}
```