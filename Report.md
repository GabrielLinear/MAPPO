## Abstract

The pairing of deep neural network and Reinforcment Learning and its improvements has outperformed the historical methods on a large panel of environment.  In this work we applied a state-of the art policy-based method to directly learn the optimal policy in the context of Multi-Agent framework.  We adapted the proximal policy optimization technique actor-critic style for the benchmark Unity game environment Tennis. We  have  demonstrated  great  performances  and  but a  great  instability  with  this  method that need to be improved. Nevertheless, the game environment is considered solved with a slow learning curve.

## Theory

During this work, we made several attempts to find the optimal policy for the Reacher environment. We describe here the PPO actor-critic algorithm we used and its underlying theory.
\\
We consider a smart agent that take an action \textbf{$A_t$} in an environment at each time step \textbf{$t$}. The agent interact with this environment that return an observation \textbf{$O_t$}, which we consider for simplification to be its internal states \textbf{$S_t$}. The environment is formally described by a Markov Decision Process where the current state \textbf{$S_t$} completely characterize the process.
The goal is to find the optimal policy $\pi^* (s|a)$ by maximizing the expected total reward. We consider in this work, that we sample a stochastic policy from a normal law $a_t ~ \pi(s_t|a_t)$ with $\pi(s_t|a_t) \sim \mathcal{N}(\mu,\,\sigma^{2})$. We describe the problem as an gradient optimization algorithm and a policy-based method as an episodic-return objective of the form:
$$ g = \mathbb{E}[ \sum_{t=0}^{\inf} At \nabla_{\theta} \pi_{\theta}(s_t|a_t)] $$

## Experiments

<p align="center">
  <img src= "https://github.com/GabrielLinear/MAPPO/blob/main/Images/MAPPO_Scheme.jpg" />
</p>

Table1) Set of hyperparameters used for training the MAPPO algorithm.
|Hyperparameter | Values |
| ------------- | ------------- |
|Epsilon | 0.1 |
|Beta |    1e-3    |
|Learning rate  |    2e-4   |
| Network hidden size 1 | 512 |
| Network hidden size 2 | 256 |
| Continuous samping distribution | Normal |
| Variance | 0.5 |
| tmax | 2500 |
| batch size | 128 |
| Sample shuffling | False |


## Results

## Discussion
During our experiments, we have noticed a great difficulty to find the accurate hyperameters that lead to a correct policy optimization. Indeed, after several weeks  of uncessful learning, we finally found a set of working hyperparameter as in the table1. The learning led to a score convergence of the agents close to 0.08. This thresold seemed to be insurmountable barrier before finding the good set.

Moreover, even when we found the great set of hyperparameter, a low learning curve has been shown. Indeed, the environment has been solved after 20 000 episodes rather than other method seems to achieve similar performances under 6000 episodes. A great instability could be the cause of this difficult learning that should lead to further exploration and studies.

Finally, we suggest for further study to find alternative to this method or used the newest research that seems to improve stability of this algorithm. We can for exemple suggest the PopArt from ( )  that seems to perform well in practice.
