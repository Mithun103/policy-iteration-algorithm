# POLICY ITERATION ALGORITHM

## AIM
To develop a Python program to find the optimal policy for the given MDP using the policy iteration algorithm.
## PROBLEM STATEMENT
The bandit slippery walk problem is a reinforcement learning problem in which an agent must learn to navigate a 7-state environment in order to reach a goal state. The environment is slippery, so the agent has a chance of moving in the opposite direction of the action it takes.

## POLICY ITERATION ALGORITHM
The policy iteration algorithm is a dynamic programming method for determining the optimal policy in a Markov Decision Process (MDP). The process involves repeatedly evaluating and refining a policy until it stabilizes.

The algorithm begins with an initial arbitrary policy. It then alternates between two key steps:

Policy Evaluation: In this step, the algorithm calculates the value of each state under the current policy. The value represents the expected reward the agent will receive when starting in that state and consistently following the given policy.

Policy Improvement: This step updates the policy by selecting actions that yield the highest expected value for each state. If no better policy can be found, the algorithm terminates.

The process continues until the policy converges, meaning further improvements are no longer possible.

## POLICY IMPROVEMENT FUNCTION
### Name : MITHUN M S
### Register Number : 212222240067
```
def policy_improvement(V, P, gamma=1.0):
    Q = np.zeros((len(P), len(P[0])), dtype=np.float64)
    for s in range(len(P)):
      for a in range(len(P[s])):
        for prob, next_state, reward, done in P[s][a]:
          Q[s][a] += prob * (reward + gamma * V[next_state] * (not done))
    new_pi = lambda s:{s:a for s,a in enumerate(np.argmax(Q,axis=1))}[s]

    return new_pi
```

## POLICY ITERATION FUNCTION
### Name : MITHUN M S
### Register Number : 212222240067
def policy_iteration(P, gamma=1.0, theta=1e-10):
    random_actions = np.random.choice(tuple(P[0].keys()), len(P))
    pi = lambda s: {s:a for s,a in enumerate(random_actions)}[s]
    while True:
      old_pi={s:pi(s) for s in range(len(P))}
      V=policy_evaluation(pi,P,gamma,theta)
      pi=policy_improvement(V,P,gamma)
      if old_pi=={s:pi(s) for s in range(len(P))}:
        break
    return V, pi

## OUTPUT:
### optimal policy
![image](https://github.com/user-attachments/assets/2b4b6e65-cc19-4313-bf81-c553ddb9ecd7)

### success rate
![image](https://github.com/user-attachments/assets/984500db-a7a4-4b60-b4c3-9d5907051cd1)
### state value function
![image](https://github.com/user-attachments/assets/892c3ade-29d1-4792-a292-3f3354099302)


## RESULT:
Thus, Python program is developed to find the optimal policy for the given MDP using the policy iteration algorithm.

