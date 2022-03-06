# MAPPO

# A Multi-agent Deep Reinforment Learning case study : Unity Tennis environment

<p align="center">
  <img src= "https://github.com/GabrielLinear/MAPPO/blob/main/Images/Environment.jpg" />
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

You can re-train the agent with the algorithm by launching the notebook PPO_actor_critic, then on the terminal in the cloned git hub folder you can check your learning compared to the second part of this one from this git:
```
tensorboard --logdir=Tensorboard-files
```

### Environment
In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.
The observation space and the action space is continuous.The 28 varaibles corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.  Every entry in the action vector should be a number between -1 and 1.

The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.

### Results of the algorithm
With two different set of hyperparameters to stabilize the training at half the trajectory with achieve the +0.5 score wanted for 35300 episodes.
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

For more information you can check the [report](https://github.com/GabrielLinear/MAPPO/blob/main/Report.md). 


Source : Mappo paper
https://sites.google.com/view/mappo
