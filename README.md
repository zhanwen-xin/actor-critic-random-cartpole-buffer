# actor-critic-random-cartpole-buffer
Datasets collected by actor critic agent and random agent in a discrete Cartpole environment.

## Agents performance
![Alt text](https://github.com/zhanwen-xin/actor-critic-random-cartpole-buffer/blob/main/pic/returns.png)

Data are collected after 500 episodes of pretraining for both agents. After 500 episode, training on Actor-critic agent stopped.

## 9 datasets
- 100 episodes from Actor-Critic agent
- 100 episodes from Random agent
- 100 episodes, in which 50 episodes are from Actor-Critic agent, 50 episodes are from Random agent. Episodes are shuffled.
- 250 episodes from Actor-Critic agent
- 250 episodes from Random agent
- 250 episodes, in which 125 episodes are from Actor-Critic agent, 125 episodes are from Random agent. Episodes are shuffled.
- 500 episodes from Actor-Critic agent
- 500 episodes from Random agent
- 500 episodes, in which 250 episodes are from Actor-Critic agent, 250 episodes are from Random agent. Episodes are shuffled.

## Data structure
- Each dataset.json file contains a dictionary with keys `states`, `actions`, and `rewards`. 
- Lists are stored under each key. Note that the each discretized state here has dimension of 40, so the dimension of the dictionary[states] is (#episode, #time steps in each episode, 40).
- Example of one episode: $$S_0, A_0, R_1, ..., S_{T-1}, A_{T-1}, R_T$$

## How to run in your notebook
Copy the below code to import the datasets
```
!git clone https://github.com/zhanwen-xin/actor-critic-random-cartpole-buffer.git public
import json
with open('./public/datasets/ds_ac_500ep.json', 'r') as f:
    buffer_ac_500 = json.load(f)
```

Visualize one dataset example: 500 episodes from Actor-Critic agent
```
import pandas as pd
buffer_ac500_df = pd.DataFrame(buffer_ac_500)
print(buffer_ac500_df)
```
Output:
```
                                                states  \
0    [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1,...   
1    [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0,...   
2    [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0,...   
3    [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1,...   
4    [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0,...   
..                                                 ...   
495  [[0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,...   
496  [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1,...   
497  [[0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,...   
498  [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1,...   
499  [[0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0,...   

                                               actions  \
0    [0, 0, 1, 0, 1, 1, 0, 0, 0, 0, 1, 0, 1, 0, 0, ...   
1              [0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 1]   
2                    [1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1]   
3    [0, 0, 1, 1, 0, 1, 0, 1, 0, 0, 1, 0, 1, 0, 1, ...   
4                 [1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1]   
..                                                 ...   
495  [0, 1, 0, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, ...   
496  [0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, ...   
497  [0, 1, 0, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, ...   
498  [0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, ...   
499  [0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, ...   

                                               rewards  
0    [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
1    [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
2    [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
3    [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
4    [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
..                                                 ...  
495  [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
496  [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
497  [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
498  [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  
499  [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, ...  

[500 rows x 3 columns]
```

## Function to discretize state in CartPole-v1
```
def map_bin(state, bin_division):
  """
  Input: 
    state (float): state to map, (1,)
    bin_division (list): (9, )
  output: map_index, (1, )
  """
  for i, max_val in enumerate(bin_division):
    if state < max_val:
      map_idx = i
      break
    map_idx = 9
  return map_idx
 
def discretize_state(state):
    """
    Input: state (list): state from gym environment, (4, )
    output: discrete_state (list): one-hot encoded state, (40, )
    """
    discretize_mesh = np.zeros((40, ), dtype=int)

    # map state to bins
    position_idx = map_bin(state[0], np.linspace(-4.8, 4.8, num = 11)[1:-1])
    velocity_idx = map_bin(state[1], [-0.58, -0.36, -0.2, -0.13, 0, 0.13, 0.2, 0.36, 0.58])
    angle_idx = map_bin(state[2], np.linspace(-0.418, 0.418, num = 11)[1:-1])
    angular_velocity_idx = map_bin(state[3], [-0.3, -0.2, -0.12, -0.05, 0.01, 0.07, 0.14, 0.22, 0.32])

    discretize_mesh[position_idx] = 1
    discretize_mesh[velocity_idx + 10] = 1
    discretize_mesh[angle_idx + 20] = 1
    discretize_mesh[angular_velocity_idx + 30] = 1

    discretize_state = discretize_mesh

    return discretize_state
```
