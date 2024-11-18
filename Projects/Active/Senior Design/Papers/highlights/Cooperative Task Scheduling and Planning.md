> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=3&selection=38,88,39,66&color=yellow|Cooperative Task Scheduling and Planning, p.3]]
> > Firstly, given the multi-robot tasks, how to coordinate the operation of each single robot is determined

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=3&selection=39,76,40,106&color=yellow|Cooperative Task Scheduling and Planning, p.3]]
> > achieved by searching the shortest path in the graph where the tasks are organized in the optimal order without the consideration of resource constraints

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=3&selection=40,118,41,98&color=yellow|Cooperative Task Scheduling and Planning, p.3]]
> > resource allocation is modeled as a constrained assignment problem with the objective of minimal cycle time

# Terms
**Cycle time** - time required to accomplish a given task
# 1) Introduction
> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=3&selection=58,29,62,23&color=yellow|Cooperative Task Scheduling and Planning, p.3]]
> > n many applications, multiple robots sharing the same workspace perform a series of repetitive tasks. The time required to accomplish given tasks (cycle time) has to be optimized for the expectation of improving productivity.

- Look into source \[4\]
> [!PDF|red] [[Cooperative Task Scheduling and Planning.pdf#page=3&selection=66,0,68,3&color=red|Cooperative Task Scheduling and Planning, p.3]]
> > robot-task-sequencing (RTS) planning problem [4]

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=3&selection=77,57,79,18&color=yellow|Cooperative Task Scheduling and Planning, p.3]]
> > RTS problem would become more challenging when multi-robot tasks are involved

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=3&selection=85,8,85,42&color=yellow|Cooperative Task Scheduling and Planning, p.3]]
> > tools, sensors, storage, and parts

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=5,27,8,35&color=yellow|Cooperative Task Scheduling and Planning, p.4]]
> > Robots may share the resources within their reach (depending on the cell layout). Hence the resources should be scheduled because each resource can only be used by one robot at a time

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=15,26,17,32&color=yellow|Cooperative Task Scheduling and Planning, p.4]]
> >  the resources (3, 4, 7, 8) are helpful in performing task 1 and the resources (5, 6, 7, 9) are helpful in performing task 2

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=42,15,48,18&color=yellow|Cooperative Task Scheduling and Planning, p.4]]
> > obot B does not need to change resources after completing task 1 since resource 7 is shared by task 1 and task 2.

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=73,10,74,43&color=yellow|Cooperative Task Scheduling and Planning, p.4]]
> > the RTS problem herein investigated is actually a coupling of several NP-hard problems

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=75,52,79,54&color=important|Cooperative Task Scheduling and Planning, p.4]]
> > Several methods decouple the entire problem into smaller ones to obtain high-quality solutions within reasonable time [3, 9–11]. Most of these optimization methods, however, deal with the RTS problems consisting of single-robot tasks

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=90,50,94,51&color=yellow|Cooperative Task Scheduling and Planning, p.4]]
> > how to assign robots to complete the single-robot operation in each multi-robot task with the consideration of optimizing production cycle time. Furthermore, due to resource constraints, the scheduling of resources is pivotal

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=101,0,102,59&color=yellow|Cooperative Task Scheduling and Planning, p.4]]
> > We try to reduce the complexity of the problem by decoupling it into smaller ones and then solving them separately

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=104,54,107,32&color=important|Cooperative Task Scheduling and Planning, p.4]]
> > we search for the shortest path in the graph containing unallocated single-robot operations after determining the task execution sequence in task space

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=110,4,113,44&color=important|Cooperative Task Scheduling and Planning, p.4]]
> > best-fit robot configurations for task execution are selected according to a heuristic optimality metric, and then the task execution sequence is optimized in configuration space (C-space) by solving a correlative TSP

- It very well may be the first! I couldn't find anything either.
> [!PDF|red] [[Cooperative Task Scheduling and Planning.pdf#page=4&selection=118,0,120,53&color=red|Cooperative Task Scheduling and Planning, p.4]]
> > To the best of our knowledge, this paper is the first to give an efficient approach to the RTS problem involving a combination of multi-robot tasks and resource scheduling

# 2) Related Literature
> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=18,3,19,28&color=yellow|Cooperative Task Scheduling and Planning, p.5]]
> > multi-robot systems, avoiding mutual collisions between robots is essential 

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=21,25,23,9&color=yellow|Cooperative Task Scheduling and Planning, p.5]]
> > 13–15], which may seem similar to our main issue such as task sequencing and collision avoidance

- TSP problem algorithm solves it by relying on initial motion planning and the assumption no collisiosn occur
- Refined by planning subset of motions to get complete collision free trajectories
- Computationally inefficient when n_tasks > 100
> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=23,22,25,4&color=important|Cooperative Task Scheduling and Planning, p.5]]
> > [10], the problem is modeled as a min-max Generalized Multiple Traveling Salesman Problem.

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=34,10,38,5&color=important|Cooperative Task Scheduling and Planning, p.5]]
> > Touzani et al. [3] model the multi-robotic task sequencing problem in the form of a new min (summax) Multiple Generalized Traveling Salesman Problem and then develop an approach based on the genetic algorithm

- \[11\] Partitions the workspace into private/disjoint workspaces (which is the approach that Sean outlined in his paper)
> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=39,28,41,57&color=important|Cooperative Task Scheduling and Planning, p.5]]
> > Åblad et al. [11] propose an intersection-free geometrical partitioning method for allocating tasks of assembly cells in a way that no collision

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=42,39,45,36&color=yellow|Cooperative Task Scheduling and Planning, p.5]]
> > key of collision avoidance in this article is partitioning the entire workspace to generate robot’s private workspace which geometrically disjoint from each other.
> 
> 

> [!PDF|red] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=45,46,46,51&color=red|Cooperative Task Scheduling and Planning, p.5]]
> > sometimes it is impossible to completely disjoint robot paths

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=49,0,50,55&color=yellow|Cooperative Task Scheduling and Planning, p.5]]
> > task sequencing and collision avoidance of multiple robots can be considered simultaneously in a unified framework


- Related to Job-shop Scheduling problem!
> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=56,1,58,50&color=yellow|Cooperative Task Scheduling and Planning, p.5]]
> > ur problem also shares some characteristics with the job-shop scheduling problem (JSSP), the goal of which is on-time delivery using limited capability machines

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=66,28,68,14&color=yellow|Cooperative Task Scheduling and Planning, p.5]]
> > none of these algorithms model spatial constraints and consider the impact of robot configurations

- This is a very similar problem to ours. No collision avoidance though

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=70,9,74,34&color=important|Cooperative Task Scheduling and Planning, p.5]]
> > quite a resemblance between our problem and multi-robot task allocation (MRTA) problems. Given a set of tasks, the goal of MRTA is to determine the capable performers for each task from a set of robots with the aim of accomplishing the global objective

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=5&selection=86,21,88,4&color=yellow|Cooperative Task Scheduling and Planning, p.5]]
> > emphasize task allocation but neglect the importance of collision avoidance in industrial manufacture

# 3 Problem Formulation
1) **Inputs**

|                                             | **Definition**                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| $G=\{ g_{1},\dots,g_{N_{g}} \}$             | Set of $N_g$ available resources in the workspace                                                                                                                                                                                                                                                                                                                                                |
| $R=\{ r_{1},\dots,r_{N_{r}} \}$             | Set of $N_{r}$ robots which works the multi-robot tasks together                                                                                                                                                                                                                                                                                                                                 |
| $T=\{ t_{1},\dots,t_{N_{t}} \}$             | Set of $N_t$ multi-robot tasks $t_i$                                                                                                                                                                                                                                                                                                                                                             |
| $P_{i}=\{ p_{i, 1}, \dots, p_{i, N_{r}} \}$ | Tasks can be divided among working points $P_i$, which an be visited by individual robots<br><br>$i$ - represents the task number <br>**English:** A task has a set of points that a describe where each robot needs to be at. <br><br>For instance, Robot A might need to be in one corner while Robot B is in the other corner for this task to be complete $\{ p_{0, r_{a}}, p_{0, r_{b}} \}$ |

==Not sure what a working point means==

2) Determine $p_{i}^{k}$ (working point in $P_i$ assigned to robot $r_k$)
	1) Each working point needs a resource $g \in G$
	2) Robot must visit assigned resource before working point 
		1) **This isn't necessary for us**
	3) Define $u_{i}^{k} = (g_{i}^{k}, p_{i}^{k})$ as **"united resource points"** 
		1) Basically the pair of working point and resource needed for working point


- $q^{k}$ configuration of robot 
- $q_{g_{i}}^{k}$ and $q_{p_{i}}^{k}$ are robot configurations associated with $g_{i}$ and $p_{i}$
- $Q_{i}^{k}=(q_{g_{i}}^{k}, q_{p_{i}}^{k})$ the configuration associated with **"united resource point"** 

**Important!** $q_{0}^{k}, p_{0}^{k}$ are assumed to be the home locations of robot $r_{k}$

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=6&selection=153,0,175,1&color=yellow|Cooperative Task Scheduling and Planning, p.6]]
> > $q_{_{0}^{k}}$ represents the predefined home configuration of $r_{k}$ and $p_{0}^{k}$ is the home location of $r_{k}$

**Objective:** Determine $p_{i}^{k}, u_i ^{k}, Q_{i}^{k}$ and task execution sequences that minimize cycle time
- **English**: For each task and robot, find the working point, the resources needed for the working point, and the configuration associated with those resources/working point

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=6&selection=223,16,254,11&color=yellow|Cooperative Task Scheduling and Planning, p.6]]
> > the solution must satisfy $\bigcap_{\forall k} g_{i}^{k} = \emptyset$ and $\bigcup_{\forall k} p_{i}^{k} = P_{i}$ and respect the robotic constraints (such as no collisions)
- **English:** resources used by robots are independent of each other for a given task. Working points for all robots make up the points needed for task $i$

## 3.2 Problem Decomposition
> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=6&selection=260,0,262,40&color=yellow|Cooperative Task Scheduling and Planning, p.6]]
> > The problem is interdisciplinary, integrating together combinatorial optimization and path planning issues, and is too complex to be solved directly

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=6&selection=267,0,273,50&color=important|Cooperative Task Scheduling and Planning, p.6]]
> > For instance, the assignment of working points to the robots depends on the choice of the task execution sequence, and the allocation of the resources depends on the assignment of working points. In addition, usually, the robot can perform the same task with several configurations at the particular working point.The choice of the robot configuration can influence the production cycle time

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=6&selection=278,19,281,23&color=yellow|Cooperative Task Scheduling and Planning, p.6]]
> > the proposed approach is based on a strategy decoupling the entire problem into four stages: working-points assignment, resources allocation, optimization and robot path planning

![[Cooperative Task Scheduling and Planning.pdf#page=6&rect=303,526,547,734&color=yellow|Cooperative Task Scheduling and Planning, p.6]]


# 4 Solution Approach
## 4.1 Working Point Assignment
> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=6&selection=295,30,297,56&color=yellow|Cooperative Task Scheduling and Planning, p.6]]
> > This step does not consider resource conflicts for simplification, which are re-considered in the following steps to guarantee the feasibility

- The schedule is represented as a graph $(V^{k}, E^{k})$
	- $V^{k}$ set of the working points
	- $E^{k}$ edges that connect to working points together
		- Edge represents the path moving from one working point to next
	- Edge cost $c_{e}(u, v): E^{k} \to \mathbb{R}^{+}$ models time required for $r_k$ to visit edge
- A tour is a sequence of working points that start and end at the home location $S^{k} = \{ p_{0}^{k}, s_{1}^{k}, \dots, s_{N_{t}}^{k}, p_{0}^{k} \}$
	- $s_{j}^{k}$ is an intermediary point the robot visits on its way to complete the task. It could be a working point or it could be a point it passed through along the way
		- ==Fact check this==
- Cost of a tour is the sum of the edges along the tour starting from the home position
![[Cooperative Task Scheduling and Planning.pdf#page=6&rect=305,136,551,178&color=yellow|Cooperative Task Scheduling and Planning, p.6]]
- A feasible solution is a set $S=(S^{1}, .., S^{N_{r}})$ whose elements are a tour for each robot
- Cost of $S$ is the maximum out of the cost for each robot tour
![[Cooperative Task Scheduling and Planning.pdf#page=7&rect=48,369,294,396&color=yellow|Cooperative Task Scheduling and Planning, p.7]]
- **Goal**: Find optimal set of tours that minimizes $Cost_{S}(S)$

> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=7&selection=33,25,36,56&color=yellow|Cooperative Task Scheduling and Planning, p.7]]
> > It is evident that the task execution sequence will affect the assignment of working points and vice-versa. Moreover, some assignments will lead to inevitable collisions when robots execute tasks together

**Algorithm:**
1) Find optimal order of tasks based on metric (like euclidian distance between task center)
	1) They use 2-Opt TSP solver
> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=7&selection=47,1,50,54&color=yellow|Cooperative Task Scheduling and Planning, p.7]]
> > Find an optimal visit order of the tasks in a tasklevel metric (e.g. Euclidean distance between task centers). The problem is modeled as a traveling salesman problem

2) Given the order in (1), find optimal assignment of robots for each task so total path length through working points is minimized.
	1) Create a graph whose layers correspond to a task
	2) Vertices in same layer are unconnected. Vertices in adjacent layers are connected.
	3) Calculate costs of edges between nodes (the working points of task)
	4) Find shortest path to find assignment of working points of one robot. 
	5) Remove vertices that were already assigned to be inaccessible
	6) The start and end positions must be set for each robot, since their home positions are different.
3) Check for collisions
> [!PDF|yellow] [[Cooperative Task Scheduling and Planning.pdf#page=7&selection=90,18,102,13&color=yellow|Cooperative Task Scheduling and Planning, p.7]]
> > graph consisting of Nt layers corresponding to the Nt tasks is constructed. The tasks are ordered according to Step 1
> 
> 

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=7&selection=126,57,128,39&color=important|Cooperative Task Scheduling and Planning, p.7]]
> > the shortest path between the StartNode and EndNode is found to obtain the working-points assignment

> [!PDF|important] [[Cooperative Task Scheduling and Planning.pdf#page=7&selection=134,0,136,36&color=important|Cooperative Task Scheduling and Planning, p.7]]
> > After assigning working points for one robot, the graph is updated (modify the vertices that have been visited to be inaccessible

> [!PDF|red] [[Cooperative Task Scheduling and Planning.pdf#page=7&selection=148,0,153,62&color=red|Cooperative Task Scheduling and Planning, p.7]]
> > Step 3 Check for collisions and adjust the allocation. The allocations leading collisions will be modified. The adjustment of working points allocation is limited to the the same task and does not affect other tasks. (Line 13 in Algorithm 2)
> 
> Confusing

