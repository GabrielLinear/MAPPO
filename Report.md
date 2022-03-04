## Abstract

The pairing of deep neural network and Reinforcment Learning and its improvements has outperformed the historical methods on a large panel of environment.  In this work we applied a state-of the art policy-based method to directly learn the optimal policy in the context of Multi-Agent framework.  We adapted the proximal policy optimization technique actor-critic style for the benchmark Unity game environment Tennis. We  have  demonstrated  great  performances  and  but a  great  instability  with  this  method that need to be improved. Nevertheless, the game environment is considered solved with a slow learning curve.

## Theory



## Experiments

<p align="center">
  <img src= "https://github.com/GabrielLinear/MAPPO/blob/main/Images/MAPPO_Scheme.jpg" />
</p>


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

Table of the hyperparameters used for training the algorithm.

## Results
