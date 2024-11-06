# Configuration Space
[[Lecture3-Cspace.pdf]]

1. **Defining Configuration Space**  
   - How does the concept of configuration space simplify the motion planning problem for complex robots?  
   - In what scenarios might using configuration space be more challenging or limiting?  

2. **Degrees of Freedom and Configuration Space Dimension**  
   - How does the number of degrees of freedom impact the complexity of the configuration space?  
   - What are the pros and cons of higher-dimensional configuration spaces in terms of computational efficiency and accuracy in representing real-world scenarios?

3. **Obstacle Representation in Configuration Space**  
   - What are the advantages of using configuration space obstacles when planning paths?  
   - How does obstacle complexity (e.g., polygonal vs. non-convex shapes) affect the feasility and accuracy of collision avoidance in configuration space?

4. **Minkowski Difference in Obstacle Computation**  
   - How does the Minkowski difference help in defining configuration space obstacles for a polygonal robot?  
   - What are some challenges in computing the Minkowski difference, especially for complex or non-convex obstacles?

5. **Numerical vs. Explicit Construction of Configuration Space Obstacles**  
   - What are the benefits of using numerical sampling methods to approximate free space instead of explicitly constructing configuration space obstacles?  
   - What trade-offs are involved in using a sampling-based approach in terms of accuracy, computational cost, and ease of implementation?

6. **Path and Trajectory Planning Constraints**  
   - How do collision-free, bounded curvature, and minimum length constraints affect path planning in configuration space?  
   - What are potential drawbacks of adding too many constraints in trajectory planning?

7. **Homotopic Paths**  
   - How does understanding homotopic paths contribute to efficient path planning in complex environments?  
   - In what situations might the concept of homotopy not significantly affect path planning?

8. **Choosing Distance Metrics**  
   - What are the pros and cons of using \( L_1 \)-norm (Manhattan), \( L_2 \)-norm (Euclidean), and \( L_\infty \)-norm (Chessboard) distances in configuration space?  
   - How does the choice of distance metric impact the path planning process, especially in terms of accuracy and computational efficiency?

# Bug Algorithms
[[Lecture5-BugAlgorithms.pdf#page=7|Lecture5-BugAlgorithms, p.7]]
- What information is necessary for bug algorithms
- In what situations are bug algorithms used? What are the benefits and drawbacks

## Bug 0
[[Lecture5-BugAlgorithms.pdf#page=8|Lecture5-BugAlgorithms, p.8]]
- What are the steps for bug 0 algorithm?
- Where does bug0 fail

## Bug 1
[[Lecture5-BugAlgorithms.pdf#page=9|Lecture5-BugAlgorithms, p.9]]
- What are the steps for bug 1 algorithm?
- Where does bug1 fail? 
- Define **completeness**

## Bug 2
- What are the steps for bug 2 (the fixed version)
- Is bug 2 complete?

## Comparison
[[Lecture5-BugAlgorithms.pdf#page=15|Lecture5-BugAlgorithms, p.15]]
- How do bug 1 and bug 2 differ?
- How do they perform compared to each other?

# Artificial Potential Fields
[[Lecture6-Potential field.pdf]]
Here are the open-ended study questions on the content covered in your presentation:

1. **Artificial Potential Fields**  
   - What are the advantages of using artificial potential fields for robot motion planning?
   - What are the main limitations of artificial potential fields, particularly regarding local minima, and how do these affect practical implementation?
   - How does the attractive potential influence robot movement toward the goal? Contrast this with the role of the repulsive potential around obstacles.

2. **Gradient Descent Method**  
   - How does the gradient descent method function in the context of motion planning?
   - Why might the gradient descent method lead a robot to a critical point that is not necessarily the goal, and what types of critical points might occur?

3. **Brushfire Algorithm**  
   - What is the purpose of using the Brushfire algorithm in artificial potential field planning?
   - How does connectivity (e.g., 4-connectivity vs. 8-connectivity) influence the output of the Brushfire algorithm?
   - What are the pros and cons of using a discrete vs. a continuous approach to distance computation?

4. **Wavefront Planner**  
   - How does the wavefront planner differ from the Brushfire algorithm in terms of distance computation and path planning?
   - What are some of the trade-offs between using a wavefront planner and potential fields in complex environments?

5. **Repulsive Potentials and Multiple Obstacles**  
   - How does the repulsive potential function change in the presence of multiple obstacles, and what are the implications for robot navigation?
   - In what scenarios might a simple repulsive potential model fail, and how could these be mitigated?

6. **Handling Local Minima**  
   - Why do local minima pose a problem for potential field-based methods?
   - What are navigation functions, and how do they address the local minima problem?
   - Are there alternative strategies or algorithms that can effectively handle local minima issues?

7. **Application and Scalability**  
   - How scalable are artificial potential fields and wavefront planners for high-dimensional configuration spaces?
   - In what types of real-world scenarios could artificial potential fields be practically applied, and where might they fall short?
   - Discuss possible methods to improve the performance and reliability of potential fields in dynamic environments.


# Graph Search 
Here are open-ended study questions based on the topics in your new presentation:

1. **Planning as a Graph Search Problem**  
   - What are the key advantages of representing motion planning problems as graph search problems?
   - Why might it be necessary to interleave graph construction and search, and in what types of problems is this approach most effective?

2. **Explicit vs. Implicit Graphs**  
   - How do explicit and implicit graphs differ in memory usage and computational efficiency?
   - Why are explicit graphs typically suited for low-dimensional problems in robotics, and what are the challenges of using them in high-dimensional spaces?

3. **Graph Construction Techniques**  
   - What are the benefits and drawbacks of skeletonization techniques like visibility graphs and Voronoi diagrams in path planning?
   - How might the choice of graph construction method influence the efficiency and safety of robot motion planning in real-world scenarios?

4. **Visibility Graphs**  
   - How does a visibility graph ensure that paths are obstacle-free, and what challenges arise when obstacles are non-polygonal?
   - What are the main limitations of visibility graphs in higher-dimensional planning spaces?

5. **Voronoi Graphs**  
   - How does a Voronoi graph help a robot maintain a safe distance from obstacles?
   - In what situations might the Voronoi graph lead to highly suboptimal paths, and how can these issues be mitigated?

6. **Grid-based Graphs**  
   - How does grid resolution (e.g., 4-connectivity, 8-connectivity) affect pathfinding efficiency and accuracy in grid-based graphs?
   - What are the trade-offs of using finer grid discretization in complex environments with high-dimensional spaces?

7. **Lattice-based Graphs and Motion Primitives**  
   - How do motion primitives work in lattice-based graphs, and why are they particularly useful for nonholonomic vehicles?
   - What are some challenges in implementing lattice-based graphs, especially for vehicles with complex dynamics?

8. **Dijkstra’s Algorithm**
- Perform dijkstras on an example:
![[Pasted image 20241105145731.png]]

   - Why is Dijkstra’s algorithm considered a greedy search, and how does it ensure finding the shortest path?
   - In what scenarios would Dijkstra’s algorithm be less efficient or even unsuitable, and what alternative algorithms could address these limitations?

10. **Complexity of Dijkstra’s Algorithm**  
   - How does the complexity of Dijkstra’s algorithm impact its applicability in large-scale or real-time applications?
   - How do edge weights influence the performance of Dijkstra’s algorithm, and what methods can optimize its use with different cost functions?

11. **Practical Applications and Adaptations**  
   - In real-world robotic applications, how might Dijkstra’s algorithm be adapted to accommodate dynamic obstacles or changing costs?
   - How could graph-based methods and Dijkstra’s algorithm be combined with other planning techniques to address high-dimensional or rapidly changing environments?

# A* 

- **Run A* on this example**
![[Pasted image 20241105150050.png]]

Here are open-ended study questions based on the A* Algorithm presentation:

1. **Limitations of Dijkstra’s Algorithm**  
   - What are the main inefficiencies of Dijkstra’s algorithm when used for pathfinding, and how does this affect its performance in complex environments?
   - In what scenarios might the exploration of non-promising paths become particularly detrimental to the efficiency of Dijkstra’s algorithm?

2. **Introduction to A* Algorithm**  
   - How does the A* algorithm improve upon Dijkstra’s algorithm in terms of computational efficiency?
   - Why is it important for the A* algorithm to prioritize paths that appear to lead closer to the goal, and how does this affect the overall search process?

3. **Key Notations in A***  
   - What role do the terms openSet, pre(n), h(n), g(n), and f(n) play in the functioning of the A* algorithm?
   - How does the distinction between actual cost (g(n)) and heuristic cost (h(n)) influence the decision-making process in A*?

4. **Heuristic Function Characteristics**  
   - What does it mean for a heuristic function h(n) to be admissible, and why is this property crucial for the optimality of the A* algorithm?
   - How does the triangle inequality relate to the consistency of the heuristic function, and what implications does this have for the algorithm’s performance?

5. **Comparison with Other Algorithms**  
   - How does the A* algorithm compare to other pathfinding algorithms (e.g., greedy best-first search) in terms of efficiency and optimality?
   - In what situations might you prefer to use the A* algorithm over Dijkstra’s algorithm, and why?

6. **Practical Applications of A***  
   - What are some real-world applications of the A* algorithm in robotics or other fields, and how does its performance impact these applications?
   - How can the choice of heuristic function in A* influence its efficiency in various environments?

7. **Challenges in Heuristic Design**  
   - What are some common challenges in designing effective heuristic functions for A*, and how might these challenges be addressed?
   - How does the choice of heuristic affect the trade-off between accuracy and computation time in pathfinding?

8. **Performance Analysis of A***  
   - How can the performance of the A* algorithm be evaluated in terms of time complexity and space complexity?
   - In what ways can modifications to the A* algorithm improve its performance in dynamic environments where obstacles may change?

9. **Optimizations and Variants of A***  
   - What optimizations can be implemented in the A* algorithm to enhance its efficiency in specific applications, such as robotics or video games?
   - How do variations of the A* algorithm, such as Weighted A* or Iterative Deepening A*, address the limitations of the standard version?

10. **Future Developments and Research**  
    - What are some emerging research areas related to the A* algorithm and pathfinding in robotics and artificial intelligence?
    - How might advancements in computing power and algorithm design influence the future development of the A* algorithm?

# A* Variants

1. **Understanding A* Optimality**  
   - What are the key assumptions that must be met for A* to guarantee optimality, and how does the admissibility of the heuristic function play a role in this?
   - How does the proof by contradiction support the claim that the path found by A* is optimal under the right conditions?

2. **Exploring A* Variants**  
   - What are the main differences between standard A* and Weighted A*, and in what scenarios might one be preferred over the other?
   - How does changing the weighting factor \( \epsilon \) in Weighted A* influence the trade-off between solution optimality and search efficiency?

3. **Anytime Algorithms**  
   - How does the Anytime Repairing A* (ARA*) algorithm approach the problem of motion planning, and what advantages does it provide over standard A*?
   - What implications does the ability to return a solution at any time have on the usability of ARA* in real-time applications?

4. **Parameter Selection in ARA***  
   - What challenges arise from selecting the parameters \( \epsilon_0 \) and \( \Delta \epsilon \) in the ARA* algorithm, and how can they affect the convergence of the algorithm?
   - Why is it important to manage the parameters carefully to avoid slow convergence, and what strategies can be employed to optimize this?

5. **Anytime Nonparametric A* (ANA*)**  
   - In what ways does ANA* improve upon the traditional A* algorithm, especially in terms of parameter management?
   - What characteristics of states does ANA* prioritize during its search process, and how does this affect the efficiency of the algorithm?

6. **Benchmark Testing**  
   - How were the 6-DOF and 20-DOF robot arms evaluated in the context of ARA*, and what specific metrics were used to determine performance?
   - What insights can be drawn from the benchmark tests involving grid maps with and without obstacles regarding the efficacy of the various A* variants?

7. **Applications in Autonomous Driving**  
   - What unique challenges does autonomous driving present for motion planning algorithms like A*, and how can these challenges be addressed?
   - How does the two-step solution proposed for autonomous driving leverage heuristic search and gradient descent to find feasible paths?

8. **Hybrid A* Approach**  
   - What advantages does the Hybrid A* algorithm provide in terms of pathfinding in continuous state spaces compared to traditional A*?
   - How does Hybrid A* ensure that the paths it generates are drivable while still maintaining a close approximation to optimal solutions?

9. **Heuristic Function Design**  
   - Why is the design of the heuristic function crucial for the performance of pathfinding algorithms, and what factors should be considered when developing it?
   - How do different heuristic functions (e.g., \( h_1 \), \( h_2 \), \( h_3 \)) balance the trade-off between exploration efficiency and the risk of leading to dead-ends?

10. **Future Research Directions**  
    - What are potential future research avenues related to A* variants, particularly in the context of robotics and autonomous systems?
    - How might advancements in machine learning influence the development of heuristic functions for algorithms like A* in dynamic environments?

# PRMs

### Limitations of Discrete Planning
- What are the key limitations of discrete planning methods in high-dimensional motion planning?
- How do these limitations impact the efficiency and feasibility of planning?

### Probabilistic Completeness
- Explain the concept of probabilistic completeness in the context of motion planning.
- How does it differ from traditional completeness?
- What implications does it have for real-world applications?

### Collision-Free Configurations
- Discuss the various methods for generating collision-free configurations in sampling-based planning.
- What are the advantages and disadvantages of uniform random sampling versus other techniques?

### Graph Representation in PRM
- How does the graph representation created by a probabilistic roadmap (PRM) enable efficient pathfinding?
- What characteristics of the graph are critical for ensuring successful path planning?

### Near Neighbors Selection
- Why is the selection of near neighbors important in the PRM algorithm?
- Compare the two popular methods for determining near neighbors:
  - k-nearest neighbors
  - Distance-based methods

### Comparison of sPRM and PRM*
- Compare and contrast the Simplified Probabilistic Roadmap (sPRM) with the Optimal Probabilistic Roadmap (PRM*).
- What are the main differences in their approaches to edge creation?
- How do these differences affect the quality of the resulting paths?

### Asymptotic Optimality
- Describe the concept of asymptotic optimality in the context of PRM*.
- Why is this property important for planners working in complex environments?
- How does it influence the choice of planning algorithm?

### Application of PRM
- Consider a specific application in robotics that could benefit from using a probabilistic roadmap for motion planning.
- What specific challenges might this application face?
- How could PRM help address these challenges?

# RRTs
Review how the algorithm works
[[Lecture11-RRTs.pdf#page=4]]


- Explain the RRT algorithm
![[Pasted image 20241105151528.png]]
- What does nearest_neighbor() no?
- What does select_input()
- What does new_state() do?

## RRT-Connect
[[Lecture11-RRTs.pdf#page=21|Lecture11-RRTs, p.21]]
How does RRT connect work?
What is the main improvement with RRT-Connect?

## RRT*

## Path shortcuts

## RRT vs PRM
- Explain how PRM and RRT encode paths and how you can get solutions


# Reactive planning
