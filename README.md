libab
=====

embed atomic broadcast local library



%%define variable

-lastZxid :the last transaction in peer history
-curZxid  :the peer current accepted zxid
-lastEpoch:the former leader instance,from epoch(lastZxid)
-curEpoch :the peer current accepted epoch, from epcho(zxid)
-state    :peer state,one of list[LOOKING,FOLLOWING,LEADING]
-quorum        :the quorum of all peers
-history  :the transaction log
-round    :the round of election with one peer
-id       :the peer identity 



Fast elect leader
	set peer as p;
	CODE_INIT:
		p.round = 0;
		p.state = LOOKING;
		p.lastZxid = Last(p.history);
		p.curZxid = p.lastZxid;
		p.lastEpoch = Epoch(p.lastZxid);
		p.curEpoch = p.lastEpoch;
	END
	
	CODE_LOOKING:
		Send VOTE(p.id,p.curZxid,p.round) to all peers;
		
	END
	
Peer P :
timeout ← T0
// use some reasonable timeout value
ReceivedVotes ← ∅; OutOfElection ← ∅
// key-value mappings where keys are server ids
P.state ← election; P.vote ← (P.lastZxid, P.id); P.round ← P.round + 1
Send notification (P.vote, P.id, P.state, P.round) to all peers
while P.state = election do
n ←(null if P.queu
	
	
	
		
	
	

