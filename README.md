# ECE 172A - Winter 2022
## Potential Field Traversal
<p align="center">
  <img src="images/3dContour.png" />
</p>

### 1 Plotting the Potential and Vector Fields
<p align="center">
  <img src="images/descentQuivers.png" />
</p>
The starting position is at [0,0], the goal is at position[99, 99], and the obstacles are located at [10,40] and [60, 50].
Real world obstacles are represented as repulsors in the potential field. This adds gradients to the plot where the objects are and will cause the bot to move around them when performing gradient descent. 

### 2 Applying gradient descent and plotting bot position at every iteration
<p align="center">
  <img src="images/descent1.png" />
</p>

### 3 Changing the initial position of the bot and running gradient descent
<p align="center">
  <img src="images/descent2.png" />
</p>

### 4 Changing obstacle positions and running gradient descent
<p align="center">
  <img src="images/descent3.png" />
</p>

### 5 Summary
This method of traversal is better than sense-act traversal because it allows you to plan your path before you begin moving. Sensing and acting on the fly can get you stuck or produce a suboptimal path. Gradient descent also keeps the robot equidistant from all obstacles as opposed to other algorithms that have wall hugging heuristics or don't take obstacle distance into account.

This algorithm works much like gravity does on objects. Here the objective is placed at the bottom of the hill and the robot at the top. The bot will therefore have a natural tendency to roll towards the objective. Obstacles are also represented as hills(repulsors) but smaller in scope. These hills cause the robot to naturally roll around obstacles as it descends.


## Robot Swarms
<p align="center">
  <img src="images/swarm.png" />
</p>
This algorithm generates n robots and a mxm map for them to explore. Positions on the map can either be labeled as unmapped, planned, mapped, or wall. All bots share the same destination selection algorithm and utilize A* search to find a path. The bots keep track of all explored areas and continue exploring until all positions have been mapped. The goal of the algorithm is not to keep the swarm together but instead explore the map in the fewest iterations possible. In order to prevent robots from moving in a clump and walking the same path, a list of the closest positions is kept and a random option is chosen.

### 1 Map explorition with 5 Robots
<p align="center">
  <img src="images/swarm5.png" />
</p>
Performance with 5 robots was 629 iterations

### 2 Map explorition with 10 Robots
<p align="center">
  <img src="images/swarm10.png" />
</p>
Performance with 10 robots was 343 iterations

### 3 Map explorition with 15 Robots
<p align="center">
  <img src="images/swarm15.png" />
</p>
Performance with 15 robots was 249 iterations


## Robot Kinematics

### 1 Forward kinematics
<p align="center">
  <img src="images/forward1.png" />
</p>
Robot arm given joint angles ??1=??/3, ??2=??/12, ??3=?????/6 and arm lengths L1=3, L2=5, L3=7
<p align="center">
  <img src="images/forward2.png" />
</p>
Robot arm given joint angles ??1=??/3, ??2=??/12, ??3=?????/6 and arm lengths L1=3, L2=5, L3=7

### 2 Inverse kinematics
<p align="center">
  <img src="images/inverse1.png" />
</p>
Final robot arm position given target (6,2), initial joint angles ??1=??/6, ??2=0, ??3=0, and arm lengths L1=L2=L3=10
<p align="center">
  <img src="images/inverse2.png" />
</p>
Final robot arm position given target (6,2), initial joint angles ??1=??/3, ??2=0, ??3=0, and arm lengths L1=L2=L3=10


## Path Finding
<p align="center">
  <img src="images/maze.png" />
</p>
This algorithm implements two basic search algorithms, Breadth First Search (BFS) and Depth First Search (DFS). BFS searches through all of the starting node's children, updates their parent variable to the current node, and adds them to the stack. Then BFS pops the node at the front of the stack (FIFO) and adds all of its children to the stack. This process is repeated until the goal is reached. Then the path is extracted by starting at the end and following all of the parent pointers. DFS is similar to BFS except it pops from the top of the stack (LIFO). Performance between the two implementations is decided via for loop iterations.

### 1 Breadth first search
<p align="center">
  <img src="images/path.png" />
</p>
Performance for BFS was 1,258 iterations.

### 1 Depth first search
<p align="center">
  <img src="images/path.png" />
</p>
Performance for DFS was 2,487 iterations. Even though the resulting path for both algorithms is the same, DFS was the least efficient of the two.
