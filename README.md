# actor-critic-random-cartpole-buffer
Datasets generated by actor critic agent and random agent in a discrete Cartpole environment

## Agents performance
![Alt text](https://github.com/zhanwen-xin/actor-critic-random-cartpole-buffer/blob/main/pic/returns.png)

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
