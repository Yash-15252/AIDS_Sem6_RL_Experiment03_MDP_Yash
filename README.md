# AIDS_Sem6_RL_Experiment03_MDP

## ***YASH KHAMKAR - 221A030***
## ***Markov Decision Process (MDP)***

---

## Aim
To study and implement Markov Decision Process (MDP) concepts for a recycling robot navigating battery-constrained environment states.

## Problem Statement
```
A recycling robot wanders around in environment to collect empty soda cans. 
It has a purpose to collect soda cans and recycle them in the nearby dustbin. 
There are some features on which the robot works such as Low battery and High Battery.

1. Low Battery - Search, Wait and Recharge
2. High Battery - Search and Wait
```

## Brief Theory
**Markov Decision Process (MDP)**: Stochastic decision-making framework modeling dynamic systems with sequential decisions under randomness or control. Used in probabilistic planning where agents learn optimal behavior to achieve goals.

**Key Components**:
- **S**: States (LowBat_Search, LowBat_Wait, LowBat_Recharge, HighBat_Search, HighBat_Wait)
- **A**: Actions (Search, Wait, Recharge)
- **P**: State transition probabilities P(s'|s,a)
- **R**: Rewards R(s,a,s')
- **γ**: Discount factor

**Solution Algorithms**:
- **Value Iteration**: V(s) ← max_a Σ [P(s'|s,a)(R(s,a,s') + γV(s'))]. Iterate until convergence
- **Policy Iteration**: Policy Evaluation + Policy Improvement cycles

## Implementation Explanation
`RL_EXP_3.ipynb` contains the MDP implementation for recycling robot:

```
1. Environment Setup:
   - 5 discrete states based on battery level + task
   - Action space per state
   
2. Value Iteration:
   - Initialize V(s)=0 for all states
   - Bellman backup until ||ΔV|| < ε
   
3. Policy Iteration:
   - Evaluate policy: v_π = r_π + γP_π v_π
   - Improve: π(s) = argmax_a Q^π(s,a)
   - Converge when π unchanged
   
4. Results Visualization:
   - Optimal policy per state
   - Value function convergence
   - Algorithm comparison
```

**Key Findings**:
```
Value Iteration: Converges in ~200 iterations  
Policy Iteration: ~10 iterations (faster)
Optimal Policy: HighBat-Search → LowBat-Recharge cycle  
Demonstrates battery-aware decision making
```

## Sample Output
```
Optimal Policy:
HighBat-Search: SEARCH
HighBat-Wait: SEARCH  
LowBat-Search: RECHARGE
LowBat-Wait: RECHARGE
LowBat-Recharge: RECHARGE

Max Value V*[HighBat-Search] ≈ 2.15 (γ=0.9)
```

## Conclusion
**Classical MDP solving verified**: Value/Policy Iteration solve finite MDPs optimally  
**Battery management**: Robot learns to recharge when low, search when high  
**Algorithm comparison**: PI faster despite evaluation overhead  
**Foundation for RL**: Dynamic programming methods enable optimal control  

## References
1. Sutton & Barto, "Reinforcement Learning: An Introduction" (Ch. 3 Finite MDPs, Ch. 4 DP)
2. Puterman, "Markov Decision Processes"  
3. AIDS Sem8 RL Course Materials

## Setup & Run
```bash
cd AIDS_Sem6_RL_Experiment03_MDP
pip install -r requirements.txt
jupyter notebook RL_EXP_3.ipynb
```

---

