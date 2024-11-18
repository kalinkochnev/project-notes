# 11/15/24
- I started reading/taking notes on the Cooperative Task Scheduling and Planning paper and I think this may completely remove the need to decompose the part into separate sections for each robot. 
	- Notify team of this update (specifically vihaan)
	- This may also allow us to solve the problem of allowing robots to print at different heights relative to one another and not wait for completion
[[Cooperative Task Scheduling and Planning]]
[[Cooperative Task Scheduling and Planning.pdf]]
# 11/12/24
## Notes
- The Marlin firmware has gcode documentation that is helpful: [[GCode]]
	- https://marlinfw.org/docs/gcode/G000-G001.html

- I need to make unit tests that check that the order of the gcode parameters does not affect the 
- Also test that a task will always have a minimum of two points
- Test for case where the last set of commands do not have any more `G1`s

![[Pasted image 20241112115209.png]]
- This diagram shows the individual tasks for a `FILL` and any Gcode command `G1/G0`
- However for some reason if I only display for tasks that have `G1` it 
- 

# 11/11/24
https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9636119
## Notes
- Cura inserts comments to indicate what kind of operation is being done
	- A list can be found here: https://community.ultimaker.com/topic/31671-what-are-the-possible-type-comments-inserted-by-cura-into-the-gcode-output/
## Recap
I was in the process of implementing gcode processing for Cura, which takes advantage of several conventions. There are comments that indicate the type of operation being done by the gcode. Layer changes are also exclusively controlled by `Z` changes. There is no hopping by default. 


## Next steps
 - [ ] What does the `G0 F<number here>` command mean?
 - [ ] Handle the different cases for task decomposition based on `MotionType`
# 11/9/24
## Plans for today
- [x] Implement simple display of gcode and robot following it
## Next time
- [x] There is some kind of bug that is causing the robots to teleport. 
	- This had to do with
## Notes
- Run code by 
```
cmake -B build
cmake --build build
```

- [[Constructors#Move constructor]] if you only have a move constructor defined but not a copy constructor, vectors may not work. This is because when a vector is resized the elements must be copied over 

- I really need to start testing this code... This seems like a good framework
https://boost-ext.github.io/ut/

- Moving explained [[Constructors#Move constructor]] 
https://stackoverflow.com/questions/3413470/what-is-stdmove-and-when-should-it-be-used
# 11/8/24
## Plans for today
- [ ] Read task ordering paper in depth
- [ ] Rewrite code to be modular
- [ ] Detect hops
- [ ] Write update for Sean
# 11/7/24
## Recap
I began implementing the diagram I specified here [[Code diagram.canvas|Code diagram]]. Unfortunately since I am on my laptop I couldn't do incremental testing when I made my changes. So this is functionally a brand new rewrite. 

Todos:
- [ ] Proper error handling of gcode parsing
- [ ] Create function that determines the range of indices in the motion plan trajectory that correspond to a certain time step
- [ ] Display extruder point and collision radius separately
- [ ] Consider adding annotations to motion plan class to indicate which action is being performed
- [ ] Need to detect hops to not confused that with different layers
	- [ ] The parse gcode file should only generate the robot states, not attempt to try and parse it.
	- [ ] Maybe create a new class for gcode segmentation?
- [ ] In future optimization, draw all lines with a single draw call

# 11/3/24
[Task Constrained Motion Planning in Robot Joint Space](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=4399305)
[Novel Potential Guided Bidirectional RRT∗ With Direct Connection Strategy for Path Planning of Redundant Robot Manipulators in Joint Space](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10110311)
# 11/2/24
https://nbfigueroa.github.io/multi-arm-coordination/
# 10/30/24
## Today's plans
- [ ] Display single layers
	- [ ] Detect layer change in gcode
	- [ ] Display lines that are not travels
- [ ] Create robot state class
	- [ ] Robot radius, Contains position, collision evaluation method, path plan for robot
	- [ ] Create artificial delay for collision detection
	- [ ] Create ring to indicate collision region around robot point
- [ ] Display multiple robots on screen
- [ ] Each robot should follow their own path plan
- [ ] Robot stops if a collision would occur
- [ ] Integrate IMGUI
## Plans for next time
- [ ] Display all lines in layer as gray
- [ ] Display black line for paths already traversed
- [ ] Draw travel lines as blue

## Recap
# Documents worked on

# Notes
# Questions



# 10/22/24
Idea: what if for every pair of arms we calculated the trajectories that would result in a collision instead of the trajectories that wouldn't .

Then we plan with the explicit goal of avoiding those configurations

# 10/21/24
[RRT Redundant manipulators](https://ieeexplore.ieee.org/document/10110311)
[Cooperative path planners RRT Quadrotors](https://journals.sagepub.com/doi/10.1177/09544100211016615)
[Multi agent path plan RRT](https://www.mdpi.com/2076-3417/13/22/12114)

https://ieeexplore.ieee.org/abstract/document/1641979
https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=4813913
- These 3 papers look into combined motion planning and inverse kinematics

# 10/18/24
[A hybrid approach for complete motion planning](https://ieeexplore.ieee.org/abstract/document/4399064)
[A scalable distributed RRT for motion planning](https://ieeexplore.ieee.org/abstract/document/6631304)

https://arxiv.org/abs/2402.01502
# 10/17/24
https://chatgpt.com/share/67113dd6-67ac-8012-8d2b-44a45569cd40

- Maybe I can somehow integrate this with a motion planning RRT solution to generate paths that are feasible as well as alternative configurations

[Path planning in 1000+ dimensions using a task-space Voronoi bias](https://ieeexplore.ieee.org/abstract/document/5152638?casa_token=BVVzUAwkzUIAAAAA:8k3NsPAafD06p5yfdVjH8R10WH1ruojoRiHaxCUDlpQDtGNdw-5bVLHEFFr09GGTqhldGZP71A)
[Posture Optimization in Robot Machining with Kinematic Redundancy for High-Precision Positioning](https://www.jstage.jst.go.jp/article/ijat/17/5/17_494/_article/-char/ja/)
- This seems interesting. This could be used to improve print quality.
- 
# 10/16/24
## Things to look into
Multi-Agent Path Finding (MAPF)
robot arms in common workspace
distributed manufacturing
multi agent shared resources
- We need to consider planning and control as one
[Decentralized multi-agent path finding framework and strategies based on automated negotiation](https://link.springer.com/article/10.1007/s10458-024-09639-8)
[Review of velocity obstacle paradigm](https://www.sciencedirect.com/science/article/abs/pii/S0921889024000289)
[Velocity obstacle paradigm](https://arxiv.org/pdf/2409.10117)
[Adaptive Robot Coordination: A Subproblem-Based Approach for Hybrid Multi-Robot Motion Planning](https://ieeexplore.ieee.org/abstract/document/10577245)
[Decentralized Multi-Agent Planning Using Model Predictive Control and Time-Aware Safe Corridors](https://ieeexplore.ieee.org/abstract/document/9851518?casa_token=pCZUbFRADtcAAAAA:g38UYH6uKHd4cGNiNbDjq4ICFG0KlBukbtWyY0mlg1Ad4r9sT65Sm_WOgMC-KSZDFutRNORvCA)

[Motion Path Planning of Two Robot Arms in a Common Workspace](https://ieeexplore.ieee.org/document/9283018)


[Predictive Control of Cooperative Robots Sharing Common Workspace](https://ieeexplore.ieee.org/abstract/document/10322775)
- This has a nice review

[Push and rotate](https://aamas.csc.liv.ac.uk/Proceedings/aamas2013/docs/p87.pdf)
- This might be promising

## Questions
What is the problem called if I already know that path I need to go on but need to decide how to coordinate it?
- The only thing you can change is how you speed up items over time
This may be related? [RLSS: real-time, decentralized, cooperative, networkless multi-robot trajectory planning using linear spatial separations](https://link.springer.com/article/10.1007/s10514-023-10104-w)


## Summary of findings:

Hi everyone. I found what I think is a very promising method to solve the collaborative aspect of the motion planning problem. It uses Rapidly Exploring Random Trees. I believe this might be a very good method to use for motion planning

I will update this post as I do more research. And feel free to ask me questions or ask for clarification because I didn't have time to elaborate on all the topics.

Rescsanski, Sean attached is the paper for the DMA-RRT algorithm. Please skim it and let me know if this is something you think I should investigate further.

**The problem**  
Given the toolpath generated by the slicer, find the trajectory that   
1) Is non-colliding with the part and the other arm  
2) Covers the entire toolpath  
3) Is smooth/continuous (as much as possible)  
4) Minimizes pauses due to collision avoidance  
5) Roughly equal layer completion time

**Potential assumptions we can make**

1) We do not need an optimal path but one that satisfies all constraints.
2) Certain operations have higher priority than others (support first, walls second, infill third, etc)
3) At certain points the robot may be able to switch between operations if it would prevent collision (ex: begin printing at a different section while the other robot finishes their part)
4) _"there are many ways to skin a cat"_ - the tool path plan created by the slicer does not need to be followed exactly to have the same result.
    - For instance during infill, the path needs to cover the specified area. It doesn't matter too much as long as the filament is deposited at the proper location in a smooth manner.

**Findings**
[[RRT literature review.pdf]]

- Artificial potential fields are unattractive due to local minima solutions. 
- Algorithms like A* find optimal paths but do not scale well with large search space
- Optimization based planners struggle as constraints increase.
- Swarm/bio inspired path planning are not as effective at searching

**Potential ideas**
Some of these are pretty out there but I think they might be possible so lets try to debate them before we reject them.

- We may be able to use the slicer output to make informed "live-reslicing" to account for potential collisions
    - We can potentially exploit the "many ways to skin a cat" idea to find an alternative path that has practically the effective same result as the path planned by the slicer.
    - We can accomplish this by allowing alternative paths that can resolve a potential collision issue
    - The DMA-RRT algorithm (in the paper attach) allows agents to modify each others paths to avoid collisions to achieve minimize global costs while guaranteeing constraints are met
    - We do not need to re-slice in the literal sense. We can use the slicer output for each layer to determine which paths/points need to be extruded on but the live-planner decides which paths can be modified (like infill) and when to execute them.
## Criticisms
- Assumptions 3 and 4 may not be true depending on the process, for FFF we can be almost certain that they are true but we should verify both assumptions and be able to to implement constraints on them otherwise, just to note.
- adjustments to the path have to be in regards to either the configuration of the arm or the orientation of the end effector w/ some constraints. For instance you can adjust the angle of the end effector to be in a better configuration to avoid a collision
- we don't need RRT at all because we have the set of poses we need to solve the IK solution for just as an example
- There are more details we can talk about later, but infill selection is something that we need to design carefully and there are some good ways to do it


# 10/11/24
- [ ] Read motion planning book - Modern Robotics