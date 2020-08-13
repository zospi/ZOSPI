# Zeroth-Order Supervised Policy Improvement

![image](./Figures/cover.png)
This repo contains the PyTorch implementation of the Zeroth-Order Supervised Policy Improvement (ZOSPI).

The ZOSPI method is tested on [MuJoCo](http://www.mujoco.org/) continuous control tasks in [OpenAI gym](https://github.com/openai/gym). 
Our implementation is based on the [TD3](https://github.com/sfujim/TD3) code implementation. 

### Usage

The paper results can be reproduced by running the jupyter notebooks, or running the corresponding files directly by running, e.g.,

```
python main.py
```

To run the code with different environments or methods, users can revise the args *--env_name* and *--policy* (from 'SPI', 'TD3', 'DDPG', etc.).

### Results

#### Four-Solution-Maze

We evaluate the proposed method first on a toy environment named *Four-Solution-Maze*. The Four-Solution-Maze environment is a diagnostic environment where four positive reward regions with a unit side length are placed in the middle points of 4 edges of a N x N map. An agent starts from a uniformly initialized position in the map and can then move in the map by taking actions according to the location observations (current coordinates x and y). Valid actions are limited to [-1,1] for both x and y axes. Each game consists of 2N timesteps for the agent to navigate in the map and collect rewards. In each timestep, the agent will receive a +10 reward if it is inside one of the 4 reward regions or a tiny penalty otherwise. For simplicity, there are no obstacles in the map, the optimal policy thus will find the nearest reward region, directly move towards it, and stay in the region till the end. Figure below visualizes the environment and the ground-truth optimal solution.

![image](./Figures/exp1.png)

Experiments on the Four-Solution-Maze environment. (a) the Four-Solution-Maze environment and its optimal solution, where an optimal policy should learn to find the nearest reward region and step into it; (b) learning curves of different approaches; (c)-(h) visualize the learned policies and their corresponding value functions.

The sample efficiencies of ZOSPI and ZOSPI with UCB exploration are much higher than that of other methods. Noticeably ZOSPI with UCB exploration is the only method that can find the optimal solution.


#### MuJoCo

Then we run large scale experiment on the MuJoCo locomotion tasks. We demonstrate its high sampling efficiency, where ZOSPI achieves competitive performance compared to SOTA policy gradient methods on continuous control tasks.

![image](./Figures/exp2.png)
