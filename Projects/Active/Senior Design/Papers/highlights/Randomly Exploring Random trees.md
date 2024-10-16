# Intro
> [!PDF|yellow] [[rrts.pdf#page=1&selection=70,0,73,29&color=yellow|rrts, p.385]]
> > As autonomous systems are deployed in increasingly complex scenarios, it is essential for a team of agents to be able to work in parallel and perform far more complicated tasks than an agent operating alone

> [!PDF|yellow] [[rrts.pdf#page=1&selection=78,46,80,39&color=yellow|rrts, p.385]]
> > agents must also avoid collisions with objects in the environment and other agents while executing these task

> [!PDF|yellow] [[rrts.pdf#page=2&selection=17,15,18,59&color=yellow|rrts, p.386]]
> > is widely recognized that any decentralized planner must be careful to avoid conflicting local decisions

> [!PDF|yellow] [[rrts.pdf#page=2&selection=21,46,23,26&color=yellow|rrts, p.386]]
> > minimizing a global cost function in a decentralized setting is itself a challenging problem


> [!PDF|yellow] [[rrts.pdf#page=2&selection=31,16,34,13&color=yellow|rrts, p.386]]
> > The agents are assumed to have constrained, nonlinear dynamics, as seen in any practical system, and as a result, may be unable to follow paths generated by simple path planners

> [!PDF|yellow] [[rrts.pdf#page=2&selection=39,7,40,18&color=yellow|rrts, p.386]]
> > the typical path planning objective of minimizing a given cost metric,

> [!PDF|yellow] [[rrts.pdf#page=2&selection=41,48,44,56&color=yellow|rrts, p.386]]
> > The approach presented here is not only able to quickly identify paths that satisfy these constraints but also reuses this path information to avoid conflicting decisions between agents



# Related work
## 2.1 Path planning
> [!PDF|yellow] [[rrts.pdf#page=2&selection=55,6,61,49&color=yellow|rrts, p.386]]
> >  techniques such as A and variants thereof (Koenig and Likhachev 2002; Likhachev and Stentz 2008) have been used to find paths through discretized environments. However, these techniques typically do not scale wel


> [!PDF|yellow] [[rrts.pdf#page=2&selection=64,18,69,45&color=yellow|rrts, p.386]]
> > Several optimization-based planners have been developed, including the Mixed Integer Linear Program (MILP) formulation in Richards et al. (2002) and techniques based on Model Predictive Control (MPC) as in Dunbar and Murray (2006). While these methods can typically find minimum cost paths, they also scale poorl

> [!PDF|yellow] [[rrts.pdf#page=2&selection=82,9,88,20&color=yellow|rrts, p.386]]
> >  Random Trees (RRT) (LaValle 1998), have gained popularity in recent years. These algorithms quickly build a set of feasible paths by connecting points sampled from the environment. The sampling process allows these techniques to handle increasingly complex problems, but as a result, they only provide weaker guarantees, such as probabilistic completenes

> [!PDF|yellow] [[rrts.pdf#page=2&selection=99,0,100,13&color=yellow|rrts, p.386]]
> > The work presented in this paper builds upon the CLRRT algorithm

## 2.2 Decentralized planning
> [!PDF|yellow] [[rrts.pdf#page=3&selection=29,0,31,18&color=yellow|rrts, p.387]]
> > Consensus based approaches allow agents to coordinate actions by exchanging information on the state of each member of the team

> [!PDF|yellow] [[rrts.pdf#page=3&selection=38,39,41,13&color=yellow|rrts, p.387]]
> > propose a related cooperation strategy where agents operate in reserved regions of the map and must reach consensus on any changes to these regions
> 
> 

> [!PDF|note] [[rrts.pdf#page=3&selection=41,15,44,26&color=note|rrts, p.387]]
> > This allows for some asynchronous planning but is conservative since any potential intersection between regions triggers a consensus check, even if it does not correspond to a conflict in time

> [!PDF|yellow] [[rrts.pdf#page=3&selection=48,17,51,7&color=yellow|rrts, p.387]]
> > reachability analysis is used to predict potential trajectories of moving objects. In general, these methods are concerned with agents that are not necessarily cooperative

> [!PDF|yellow] [[rrts.pdf#page=3&selection=73,0,85,49&color=yellow|rrts, p.387]]
> > Prioritized planning techniques also avoid conflicts through sequential planning, where the planning order is determined by the priority assigned to each agent

**Important!**
> [!PDF|note] [[rrts.pdf#page=3&selection=86,23,88,3&color=note|rrts, p.387]]
> >  A search over different priority orders can be used to find an ordering that reduces the global cos

> [!PDF|yellow] [[rrts.pdf#page=3&selection=92,8,95,44&color=yellow|rrts, p.387]]
> >  it is also known that in distributed computer systems that require ordered task execution (such as processor coordination and load balancing), having a fixed execution order can limit system performance

## 2.3 Overview
- This algorithm extends the closed-loop RRT algorithm
	- Uses a simulation to grow the number of feasible paths

> [!PDF|red] [[rrts.pdf#page=3&selection=112,36,117,35&color=red|rrts, p.387]]
> > This coordination strategy draws inspiration from the single subsystem update technique in Trodden and Richards (2006) but takes advantage of the underlying CL-RRT planner to quickly find improved paths and produce a dynamic planning order based on each agent’s incentive to replan

> [!PDF|yellow] [[rrts.pdf#page=3&selection=123,0,125,54&color=yellow|rrts, p.387]]
> > Cooperative DMA-RRT algorithm retains the advantages of the DMA-RRT algorithm, while also allowing agents to modify their teammates’ plans in order to select paths

> [!PDF|yellow] [[rrts.pdf#page=4&selection=3,45,5,46&color=yellow|rrts, p.388]]
> > paths generated by both algorithms are guaranteed to satisfy all interagent constraints, such as collision avoidance


# 3 Path planning with complex constraints: CL-RRT
 The algorithm consists of three components: (1) the tree expansion process, (2) the main execution loop, and (3) the lazy check for feasibility.
 
> [!PDF|General 2] [[rrts.pdf#page=4&selection=18,31,21,26&color=yellow|rrts, p.388]]
> >  CL-RRT does not aim to generate optimal paths. Instead, the primary objective is to quickly identify a set of feasible paths that are guaranteed to satisfy all constraints

> [!PDF|general] [[rrts.pdf#page=4&selection=21,32,25,23&color=general|rrts, p.388]]
> > secondary objective is then to select the path from this set with the lowest cost. Other incremental planners could be used in place of CL-RRT as the core of the DMA-RRT algorithm, as long as they guarantee dynamic feasibility

> [!PDF|general] [[rrts.pdf#page=4&selection=35,9,37,11&color=general|rrts, p.388]]
> > Aoude et al. (2010) also demonstrated that the algorithm can be extended to handle other agents moving in the environment


## 3.1 Tree expansion
1) Randomly sampling a point $x_{sample}$ from the set of all feasible configurations $X_{\text{free}}$ 
2) Picks the closest node $N_{near}$ in the tree

> [!PDF|general] [[rrts.pdf#page=4&selection=330,0,341,46&color=general|rrts, p.388]]
> > This path expansion continues until ˆx reaches xsample or becomes infeasible by violating the constraint

> [!PDF|general] [[rrts.pdf#page=4&selection=372,29,375,47&color=general|rrts, p.388]]
> >  Nodes serve as waypoints when executing the path, and each path is uniquely characterized by its waypoints in conjunction with the dynamics and reference law used to grow it between those points

## 3.2 Execution loop

> [!PDF|general] [[rrts.pdf#page=4&selection=377,3,382,4&color=general|rrts, p.388]]
> >  execution loop of the CL-RRT, outlined in Algorithm 2, uses Algorithm 1 to find paths that take the agent to some predefined goal region Xgoal

> [!PDF|general 2] [[rrts.pdf#page=4&selection=388,1,399,30&color=general 2|rrts, p.388]]
> >  Then, during each iteration of the execution loop, the state estimate ˆx(t + Δt) is used to compute additional potential paths using the tree expansion process

> [!PDF|general] [[rrts.pdf#page=5&selection=168,0,172,1&color=general|rrts, p.389]]
> > Once the new potential paths are added to the tree, the minimum-cost path p∗

> [!PDF|general] [[rrts.pdf#page=5&selection=176,27,184,33&color=general|rrts, p.389]]
> > constraints may change over time. To avoid selecting paths that have become infeasible, the lazy check described in Algorithm 3 is performed on p∗ before confirming it as the new path

> [!PDF|general] [[rrts.pdf#page=5&selection=202,0,219,22&color=general|rrts, p.389]]
> > The lazy check mimics the tree expansion process, but instead of generating new nodes, it re-simulates the agent’s trajectory through the nodes defining p∗. If the re-simulated state ˆx(t + k) violates a constraint, the path is pruned beyond the last feasible node














> [!PDF|general] [[rrts.pdf#page=5&selection=407,0,413,58&color=general|rrts, p.389]]
> > Agents 1 and 2 begin with feasible plans but find alternate plans that appear to be safe given their current knowledge of the other agent. Since this is fully asynchronous, the agents can update their plans at any time. However, if both update at the same time, the new paths are not guaranteed to be safe since the constraints imposed while selecting the paths do not match the constraints that exist when the agents begin


# 5 Decentralized multi-agent RRT
> [!PDF|general] [[rrts.pdf#page=7&selection=9,27,19,42&color=general|rrts, p.391]]
> > The individual component handles the path planning, while the interaction component handles all information received from other agents

> [!PDF|general] [[rrts.pdf#page=7&selection=25,0,28,8&color=general|rrts, p.391]]
> > Network: The agents are assumed to form a fully connected network, allowing for fast information transfer across the team

> [!PDF|general] [[rrts.pdf#page=7&selection=41,0,43,47&color=general|rrts, p.391]]
> > Agent models: Each agent is assumed to have a model of its own dynamics, as in the CL-RRT algorithm

- The obstacles do not change significantly during a single layer increment so it might be safe to assume this is satisfied
> [!PDF|red] [[rrts.pdf#page=7&selection=52,0,54,60&color=red|rrts, p.391]]
> > Environment: The environment that the agents operate in is assumed to be known and only contain static obstacles.
> 
> 

> [!PDF|general] [[rrts.pdf#page=7&selection=61,1,66,17&color=general|rrts, p.391]]
> > Inter-agent constraints: Finally, the set of constraints imposed between agents, such as collision avoidance or rendezvous requirements, are assumed to be symmetric between agent pairs

