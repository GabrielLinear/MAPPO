# Collaboration and Competition Projet
<h2> A collaborative continuous multi-agent Reinforcement Learning study : Unity Tennis environment. </h2>

## Abstract

The pairing of deep neural network and Reinforcment Learning and its improvements has outperformed the historical methods on a large panel of environment.  In this work we applied a state-of the art policy-based method to directly learn the optimal policy in the context of Multi-Agent framework.  We adapted the proximal policy optimization technique actor-critic style for the benchmark Unity game environment Tennis. We  have  demonstrated  great  performances  and  but a  great  instability  with  this  method that need to be improved. Nevertheless, the game environment is considered solved with a slow learning curve.

## Introduction
Reinforcement learning is a framework that allows a smart agent to act with a provided environment and find the optimal policy within the environment. Since we don't know the intrinsic dynamic of the Markov Decision Process we discover the policy by sampling its dynamic. Thus, the historical idea derived from dynamic programming is based on the famous recursive Bellman Equation that led to a variety of algorithms commonly used for a learning agent **O’Donoghue 2018**.

However, there is also a more direct way to learn an optimal policy. Rather than focusing on learning a state values or states action values could we straight learned the policy ? This is at the heart branch field in RL named Policy-based methods where we learn directly an optimization-based optimal policy. Many algorithms have been suggested by combinatorial optimization as Hill-climbing, Cross entropy method or evolutionary strategies. But gradient-descent based algorithm have made the success of this field as a faster way to learn a good policy, more robust and easy to use with back-propagation or graph based optimization methods widely used for Neural Network. The REINFORCE algorithm from 1992 **Williams 1992** has been a profound achievement before more data-efficient method has been created.

On an other hand, dealing with large continuous states and actions has been a tough barrier that has been tackle first by **Mnih DQN 2015**, with the power of Neural Network generalization. Combining a deep neural network and the usual Q-learning algorithm has considerably enhanced the benchmark scores on the suite of controlling ATARI games and outperformed significantly human-based performance. Since the kick-start of this new Deep-RL field many improvement and variant have been suggested and outperformed the DQN algorithm.

In this case study, we will implement the core of the Proximal Policy Optimization algorithm **Schulman PPO 2015** more data-efficient than the REINFORCE algorithm with minor changes to deal with the continuous action spaces of the Unity Reacher environment

## Experiments
For these experiments the algorithm run on a laptop with a GPU GTX 1050. We learned our neural networks with Torch and the GPU for python 3.6. We give open access to the python code in this Git-Hub.

The environment provides a continuous vector observation of space size 24 for 3 aggreagated timesteps of Tennis play. Each tennis racket is controlled by 2 continuous actions in the range [-1,1] that represent its x and y position. We built two neural network for each agent as non-linear function approximation respectively the actor network for continuous action and the critic network to learn value estimate.

The algorithm is shared on two steps. First we collect the parallel trajectories by using our approximate optimal policy by  sampling the Gaussian law from the actor network, we calculate the old probability from this behavior and the advantage estimate from the evaluation of the critic network. Then we applied the training process described during the first section and shown here :
During this work, we follow several improvement of the PPO algorithm suggested over the year and in the context of multi-agent learning.

<p align="center">
  <img src= "https://github.com/GabrielLinear/MAPPO/blob/main/Images/MAPPO_Scheme.jpg" />
</p>

Table 1. Set of hyperparameters used for training the first half trajectory of the MAPPO algorithm.
|Hyperparameter | Values |
| ------------- | ------------- |
|Epsilon | 0.1 |
|Beta |    1e-3    |
|Learning rate  |    2e-4   |
| Network hidden size 1 | 512 |
| Network hidden size 2 | 256 |
| Continuous samping distribution | Normal |
| Variance | 0.25 |
| tmax | 2500 |
| batch size | 256 |
| Sample shuffling | False |
| SGD Importance samping epoch | 6 |

Table 2. Set of hyperparameters used for training the second half trajectory of the MAPPO algorithm.
|Hyperparameter | Values |
| ------------- | ------------- |
|Epsilon | 0.1 |
|Beta |    1e-3    |
|Learning rate  |    2e-4   |
| Network hidden size 1 | 512 |
| Network hidden size 2 | 256 |
| Continuous samping distribution | Normal |
| Variance | 0.25 |
| tmax | 5000 |
| batch size | 1024 |
| Sample shuffling | False |
| SGD Importance samping | 3 |

## Results
We sucessed to achieve great performance with the algorithm used but with some difficult adjustements. Indeed we found that there is an inversly proportionnal relation between stability and the slop at some point in the learning process. We find that the parameter that led this behaviour is the Batch_Size.
At the beginning of the training a batch size to big can lead to a difficult learning, even impossible but great stability whereas a small one achieve to get a performance of at least 0.2. At this point the learning process unstabilize and oscilate between 0.2 and 0.4 unable to learn more (at about 24000 episodes where we stop the first learning). Thus, we stabilized the tranning with a bigger batch size and a few epoch.

<p align="center">
  <b>Training over the 36000 episodes  </b>
</p>

<p align="center">
  <img src= "https://github.com/GabrielLinear/MAPPO/blob/main/Images/Scores_mean.jpg" />
</p>

<p align="center">
  <b>Zoom over the end of the training</b>
</p>

<p align="center">
  <img src= "https://github.com/GabrielLinear/MAPPO/blob/main/Images/Scores_mean_zoom.jpg" />
</p>



## Discussion
During our experiments, we have noticed a great difficulty to find the accurate hyperameters that lead to a correct policy optimization. Indeed, after several weeks  of uncessful learning, we finally found a set of working hyperparameter as in the table1. The learning led to a score convergence of the agents close to 0.08. This thresold seemed to be insurmountable barrier before finding the good set.

Moreover, even when we found the great set of hyperparameter, a small learning slope has been shown. Indeed, the environment has been solved after 34 000 episodes rather than other methods seems to achieve similar performances under 6000 episodes and without our re-parametrization trick of the hyperparameters. A great instability could be the cause of this difficult learning that should lead to further exploration and studies.

The great performances and stability shown by the original paper of MAPPO from **Chao Yu 2021** has not been shown in our exemple. So we suggest, for further study to used the newest implementations tricks in the paper from that seems to improve stability of this algorithm. We can for exemple suggest PopArt values normalization from **Hado van Hasselt 2016** that seems improve the learning in practice. Also we could tried to used reccurent policy that achieve better performance in practice than ou current naive MLP. We could also look at the impact of batch_normalization on the larning. Finally as suggested on algorithm COMA, the use of hypernetwork to learn the values estimate could add some values to the learning slope
