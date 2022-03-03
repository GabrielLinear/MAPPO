# MAPPO

# A Multi-agent Deep Reinforment Learning case study : Unity Tennis environment

<p align="center">
  <img src= "https://github.com/GabrielLinear/MADDPG/blob/main/Images/Env_solved.gif" />
</p>

Clone this Git:
```
git clone https://github.com/GabrielLinear/MAPPO.git
```
Set-up your environment like this [GitHub Pages](https://github.com/udacity/Value-based-methods#dependencies).
Previous to the operation ***pip install .*** , you will have to install torch 0.4 then uninstall it and install the torch version you want.

Then you will have to install tensorboard to access to the log files.
```
pip uninstall tensorboard
pip uninstall tensorboardX
conda install tensorboard
```

You can re-train the agent with the algorithm by launching the notebook PPO_actor_critic, then on the terminal in the cloned git hub folder :
```
tensorboard --logdir=Tensorboard-files
```

### Environment
In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.
The observation space and the action space is continuous.The 28 varaibles corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.  Every entry in the action vector should be a number between -1 and 1.

The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.

### Results of the algorithm

For more information you can check the [report](https://github.com/GabrielLinear/MADDPG/blob/main/Report.pdf). 


Source : Mappo paper
https://sites.google.com/view/mappo
