#[An Analysis of Acceptance Policies For Blockchain Transactions](https://eprint.iacr.org/2018/040.pdf "An Analysis of Acceptance Policies For Blockchain Transactions")
## Parameters: 
- λ  : poisson rate at which blocks are added to main chain (0.1 in bitcoin) 
- α : fraction of network controlled by attacker. 
- p_i : probability attacker is i blocks ahead of main chain immediately before tx was broadcast
- p_i* : probability attacker is exactly i blocks ahead/behidn the main chain at time T. 
- T : length of time from broad cast to acceptance 
- N : number of blocks added by main chain between time of broadcast and acceptance of txs 

## Setting/ Model: 
From the perspective of the receiver of the tx, # of blocks attacker has mined since tx broadcast has a poisson distribution. 

## Assumptions: 
attacker persistently attempts to double spend a particular transaction regardless of time and cost or if the attacker’s chain falls many blocks behind.

## Process: 
1. Determine how many blocks ahead the attacker is before tx is
-	broadcast p_i is determined 
2. Determine how many blocks attacker is behind or ahead of the main chain after the tx is accepted and settled
-	Eq 1 from paper
- **Explanation:** (probability attacker was j + N blocks behind/ahead at time of broadcast) * (probability attacker made i - j blocks after transaction was broadcast in time T) , i.e attacker would have had to make i + N blocks in total. 

3. Determine probability the attacker can create a chain longer than main chain after tx is settled: 
-		CTMCs (continuous time markov chains)
-		Eq 2 from paper
-**Explanation**: Probability the attacker was behind * probability he managed to come ahead  + probability the attacker was ahead 

## Results: 
- Graph of confirmations required vs Time since Tx Broadcast
- 		Setup: p_DoubleSpend < 1.337, α = 0.2, Dynamic Acceptance policy
-		 Compare Static acceptance policy (5 confirmations) to their Dynamic Acceptance policy (p_DoubleSpend < 1.337, α = 0.2):
**Graphs:**
- Double spend probability vs Time from broadcast to Tx acceptance (T)
- Number of Confirmations Required Vs. Time Since Transaction Broadcast
- Setup: E[p_DoubleSpend] = 0.8754% , Static (6 confs)
- CDF of Time To Transaction Acceptance vs time since tx broadcast 
- Setup: E[p_DoubleSpend] = 0.8754% , Static (6 confs)
- CDF of p_DoubleSpend At Transaction Acceptance vs  p_DoubleSpend At Transaction Acceptance
- Setup: E[p_DoubleSpend] = 0.8754% , Static (6 confs)
-  E[Time To Transaction Acceptance] vs. 99th percentile of pDouble Spend
- Expected Probability a Double Spend Has Occured vs. Time Since Transaction Broadcast
- Setup: E[p_DoubleSpend] = 0.8754% , Static (6 confs)
