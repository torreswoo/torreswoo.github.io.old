# RAFT 분산처리 알고리즘
- 합의 알고리즘 / 리더 선출 알고리즘
- 오픈소스만 40여개.. 적용된 서비스들도 많이 늘어나고있는 추세
- http://raft.github.io/

## Server State 서버상태
- Leader : handles all client interactions, log replication
- Follower
- Candidate

## Normal operation
- 1 Leader + N-1 Follower

## Term
- Election / Normal operation under single leader

## Leader Election

## Request Vote & AppendEntry
- Arguments / Result / Implementation
## Election Conditions
- safety / Liveness
## Log Structure

## Paxos VS RAFT

---

ctrlp
