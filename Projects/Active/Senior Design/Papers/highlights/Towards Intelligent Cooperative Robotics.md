# Terms
RAM - Robotic Additive Manufacturing
C-RAM - Cooperative robotic additive manufacturing
Digital twin - Integrates physical world feedback with digital representations
$C$ - the set of all valid arm configurations $\textbf{q}$
Tool path planning - determination of the desired path of motion of the tool center point (TCP), is defined according to the geometry of the part (calculated during slicing)

$n$ - number of robotic arms
$V_{i}$ - build volume of arbitrary robot 

antistropic properties - different mechanical properties depending on the direction of measure (ex: wood)

Conformal printing - ==Not sure== Printing along the outside surface?

Deep learning (DL)

**Digital twins**
Digital model (DM) - represents a physical system with no sensor feedback
Digital Shadow (DS) - physical system with real time system feedback but no control modifications
Digital Twin - use real time sensor feedback to control physical system
# Questions
What is a manifold?

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=16&selection=58,41,61,27&color=yellow|Towards Intelligent Cooperative Robotics, p.16]]
> >  To improve process planning within WAAM systems, a corner detection algorithm is implemented such that the robot feed rate is increased during sharp corner
- Does increasing feedrate decrease the amount of material deposited? 

# Introduction
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=1&selection=108,0,111,16&color=yellow|Towards Intelligent Cooperative Robotics, p.1]]
> > Recent research has turned to the development of AM systems that leverage robotic arms to facilitate the motion of toolheads, commonly referred to as robotic additive manufacturing (RAM) 

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=1&selection=113,48,116,4&color=yellow|Towards Intelligent Cooperative Robotics, p.1]]
> > RAM systems affords both multi-plane and non-planar slicing methods which can improve mechanical strength and reduce support

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=1&selection=129,0,133,14&color=yellow|Towards Intelligent Cooperative Robotics, p.1]]
> > ME processes such as fused filament fabrication (FFF)/fused deposition modeling (FDM) suffer from defects including internal porosity, often known as voids, which form in between deposition tracks within layers 

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=2&selection=102,0,105,36&color=yellow|Towards Intelligent Cooperative Robotics, p.2]]
> > Cooperative robotic additive manufacturing (C-RAM) platforms comprised of multiple robotic arms enable improved fabrication speeds [33], enhanced sensing capabilities [34], and heterogeneous tooling

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=2&selection=131,2,133,7&color=yellow|Towards Intelligent Cooperative Robotics, p.2]]
> >  digital twins which enable the harmonious integration of physical world feedback from sensors with digital representations


# 2. Robotic Additive Manufacturing
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=3&selection=16,32,18,34&color=yellow|Towards Intelligent Cooperative Robotics, p.3]]
> > Pre-process operations such as segmentation or transformation are applied to the part according to the slicing method used

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=3&selection=18,36,20,14&color=yellow|Towards Intelligent Cooperative Robotics, p.3]]
> > High degrees of freedom afford advanced path planning strategies such as multiaxis slicing, 

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=3&selection=26,31,29,35&color=yellow|Towards Intelligent Cooperative Robotics, p.3]]
> > such high degrees of freedom found in RAM systems require sufficient inverse kinematic solutions, or motion plans, to determine what set of joint configurations should be used ... which also avoid collisions and singularities

## 2.1 C-RAM Systems
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=4&selection=24,3,31,51&color=yellow|Towards Intelligent Cooperative Robotics, p.4]]
> > From this subset of the configuration space, a single-arm RAM system has a build volume $V$ defined by the region in which the arm can deposit material given its geometric constraint



> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=4&selection=45,0,55,4&color=yellow|Towards Intelligent Cooperative Robotics, p.4]]
> > $𝑉_{𝑒(𝑛)}$, the exclusive build volume which can only be reached by the 𝑛th arm,

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=4&selection=57,0,69,2&color=yellow|Towards Intelligent Cooperative Robotics, p.4]]
> > $𝑉_{𝑗(𝑛,𝑚)}$, the joint build volume between overlapping arms 𝑛 and 𝑚

 > [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=4&selection=78,12,87,2&color=yellow|Towards Intelligent Cooperative Robotics, p.4]]
> > capabilities of a C-RAM system are well described by the proportion of the total exclusive build volume 𝑉𝑒 and total joint build volume 𝑉𝑗

$$
r_{V} = \frac{V_{e}}{V_{j}}
$$
- $r_{V}<1$ when there is high overlapping build volume
	- Common in systems with multi-material and cooperative sensing
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=5&selection=16,0,21,14&color=yellow|Towards Intelligent Cooperative Robotics, p.5]]
> > Bhatt et al. integrated two RAM systems with varying nozzle sizes (0.4mm and 0.8mm) to improve surface quality while retaining high fabrication speed

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=5&selection=24,0,27,6&color=yellow|Towards Intelligent Cooperative Robotics, p.5]]
> > Secondary arms can also be used for multi-material printing for improved material properties. This includes fiber reinforced material extrusion where a secondary robotic arm lays fiber 

# 3. System Control for RAM
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=5&selection=35,11,38,37&color=yellow|Towards Intelligent Cooperative Robotics, p.5]]
> > Toolpath planning, or the determination of the desired path of motion of the tool center point (TCP), is defined according to the geometry of the part and is conducted before the motion planning of the arm

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=6&selection=11,18,15,18&color=yellow|Towards Intelligent Cooperative Robotics, p.6]]
> > Motion planning, or the determination of the inverse kinematic solution to afford motion to a desired point or end effector orientation, is conducted after a toolpath plan has been established to execute the desired motion of the end effecto

- Path plan - the configurations of the are necessary to complete the path
- Trajectory plan - time dependent transition between configurations

## 3.1 Slicing
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=6&selection=41,53,43,39&color=yellow|Towards Intelligent Cooperative Robotics, p.6]]
> > task motions call for the deposition of material whereas transfer motions do not and are for repositioning 

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=6&selection=50,42,51,64&color=yellow|Towards Intelligent Cooperative Robotics, p.6]]
> > The path generated during slicing for the end effector is specified as the toolpath

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=6&selection=55,18,57,61&color=yellow|Towards Intelligent Cooperative Robotics, p.6]]
> > Authors such as Borish et al. have proposed the use of "on-demand" slicing where slicing is conducted in partial sub-sections for closed-loop feedback capabilities

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=6&selection=68,32,71,60&color=yellow|Towards Intelligent Cooperative Robotics, p.6]]
> > For C-RAM systems that integrate multiple RAM systems, the decomposition of parts into sub-sections must be determined. These sections then undergo typical slicing processes to enable parallel cooperative printing
> 

### 3.1.1 Multi Plan Slicing
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=7&selection=25,0,27,36&color=yellow|Towards Intelligent Cooperative Robotics, p.7]]
> > Approaches for multi-plane slicing fall into two categories, discrete and continuous plane shifting.

Discrete axis shifting
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=7&selection=38,60,46,33&color=yellow|Towards Intelligent Cooperative Robotics, p.7]]
> > the original STL was first decomposed using a custom Matlab script into individual segments according to the plane from which they were sliced. These individual sections were then sliced in a conventional 2D planar manner using Repetier software in the default normal plane orientation; the subsequent g-code was then transformed back to the desired plane orientation with respect to global coordinates and recomposed into a single tool path cod

Continuous axis shifting
- Look into this one more
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=7&selection=59,0,62,46&color=yellow|Towards Intelligent Cooperative Robotics, p.7]]
> > Continuous axis shifting utilizes planes generated at arbitrary orientations to reduce support material usage which subsequently improves surface quality, and reduces waste material as well as post-processing operations


> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=7&selection=87,16,90,29&color=yellow|Towards Intelligent Cooperative Robotics, p.7]]
> > hese implementations rely on the readjustment of the build plate to be normal to the direction of gravity to eliminate the effect of overhangs while the extruder is in a stationary configuration

### 3.1.2 Non-planar slicing
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=8&selection=24,7,27,27&color=yellow|Towards Intelligent Cooperative Robotics, p.8]]
> > The maximum convex angle is limited by the geometry of the end effector and the flexibility of the system, lending greater advantages of non-planar slicing to RAM systems over gantry-style platforms


> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=8&selection=27,29,29,5&color=yellow|Towards Intelligent Cooperative Robotics, p.8]]
> > Non-planar slicing methods are categorized in two primary approaches: conformal and arbitrary

#### Conformal

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=8&selection=30,0,33,14&color=yellow|Towards Intelligent Cooperative Robotics, p.8]]
> > Conformal non-planar slicing methods use a top reference surface to slice parts which improves surface finish by removing the stepping effect observed with conventional 2D planar slicing

- Conformal non-planar slicing is like a top covering

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=8&selection=39,33,43,9&color=yellow|Towards Intelligent Cooperative Robotics, p.8]]
> > The most common means of generating conformal toolpaths is by projecting a planar toolpath onto a reference surface, creating a 3D conformal toolpath that can then be registered to the top layer of a part


> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=3,35,6,6&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > The application of these kinds of conformal toolpath strategies which rely primarily on projection have limited application to complex geometries.

#### Arbitrary
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=9,0,11,29&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > Arbitrary non-planar slicing methods define a 3D surface from which slicing is conducted that is not defined by a reference surface of the part



> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=15,1,24,37&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > Arbitrary slicing methods commonly use affine and non-affine transformations for regions to then be sliced in a planar manner; these sliced paths then undergo an inverse transformation to regain the original shape with a transformed non-planar toolpath plan. The basis for the transformation is typically defined by the user or according to the coordinate system utilized
> 
> 

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=46,18,48,32&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > Mechanical strength of FFF parts that use continuous fiber reinforcement can be greatly enhanced using arbitrary non-planar slicing

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=49,26,51,49&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > CFRTPCs) utilize in-nozzle or out-of-nozzle [74] impregnation of fibers to enhance mechanical strength axially along fiber orientation

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=55,0,60,10&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > Fang et al. [62] developed a slicing method to generate toolpaths for a cooperative fabrication RAM system to optimally orient fibers according to the stress fields of printed components

### 3.1.3 Considerations for C-RAM
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=104,40,106,58&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > Fabrication must occur while avoiding collision between arms which can be accomplished during toolpath planning or during motion planning

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=112,0,116,58&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > Decomposition of CAD models into separate segments is a critical requirement of all C-RAM systems ... meaning areas of the part can only be created by a subset of arms within the system.

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=117,10,118,28&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > there will always be some intersection or boundary between parts fabricated

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=127,44,130,25&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> > the selection of boundary location to create sections and its interface surface plays a critical role in the quality of the final component and its mechanical properties

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=9&selection=131,19,133,36&color=yellow|Towards Intelligent Cooperative Robotics, p.9]]
> >  Shen et al., a segmentation algorithm is introduced to minimize the difference in layer completion between each fabrication robotic arm

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=10&selection=16,0,19,27&color=yellow|Towards Intelligent Cooperative Robotics, p.10]]
> > The resulting decomposition is sufficient to ensure near-equal layer competition times, but is dependent on the position of the part with respect to the build volume

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=10&selection=27,43,30,43&color=yellow|Towards Intelligent Cooperative Robotics, p.10]]
> > Manoharn et al. [76] in a preliminary work proposed a methodology to create components using a C-RAM system with an interlocking interface structure to increase bond strength

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=10&selection=33,11,41,59&color=yellow|Towards Intelligent Cooperative Robotics, p.10]]
> > Stone et al. [79] utilized nonplanar interface layers to define decomposition regions to evaluate the performance of a novel mid-process collision avoidance algorithm. These studies do not investigate the impact of these interface patterns on mechanical properties

I have no idea what this is saying
> [!PDF|red] [[Towards Intelligent Cooperative Robotics.pdf#page=10&selection=52,0,57,51&color=red|Towards Intelligent Cooperative Robotics, p.10]]
> > Segmentation for C-RAM can also be conducted on a discrete point basis rather than entire sub-sections of the part. Arbogast et al. developed a bead scoring system for discrete deposition points within a C-RAM DED process to determine the ordered list of beads to assign to each of the three robots within the cooperative system [82]

#### Segmentation
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=10&selection=83,28,87,9&color=yellow|Towards Intelligent Cooperative Robotics, p.10]]
> > Depending on the system configuration, such as a low-overlap C-RAM platform, scheduling algorithms can be used to prevent the opportunity of collision during printing without the need for in-situ collision assessmen

## 3.2 Motion Planning
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=11&selection=61,20,68,2&color=yellow|Towards Intelligent Cooperative Robotics, p.11]]
> > The configuration 𝑞 is an element of the configuration space 𝐶

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=11&selection=116,29,131,16&color=yellow|Towards Intelligent Cooperative Robotics, p.11]]
> > valid solutions of the calculated motion plan must be located in the subset of the configuration space 𝐶 which does not collide with obstacles 𝐶𝑓 𝑟𝑒𝑒 with all other non-valid solutions which do collide being under subspace 𝐶𝑜𝑏𝑠𝑡𝑎𝑐𝑙𝑒

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=11&selection=134,46,137,39&color=yellow|Towards Intelligent Cooperative Robotics, p.11]]
> > Gilbert-JohnKeerthi (GJK) algorithm [86], are used to determine collisions with spherical approximations of objects commonly used to reduce computational complexity

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=11&selection=145,53,150,29&color=yellow|Towards Intelligent Cooperative Robotics, p.11]]
> > much of recent research has sought to improve the search of 𝐶-space through the use of ML methods

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=11&selection=181,0,183,8&color=yellow|Towards Intelligent Cooperative Robotics, p.11]]
> > Motion planning can be conducted in an offline or online manner depending on the computation efficiency of the approach

### 3.2.1 Motion Planning methods
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=24,49,27,46&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > Motion planning conventionally seeks optimal solutions according to cost functions which aim to minimize criteria such as computational time, path length, and path jerk

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=36,0,39,22&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > Conventional motion planning algorithms for industrial robotic arms primarily fall into three main categories [38]: artificial potential field (APF), bio-inspired heuristic, and sampling-based methods

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=48,1,51,19&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > Its primary advantage lies in dynamic environment applications [38], but suffers from local minimums

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=57,25,59,52&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > Bio-inspired heuristic methods include approaches such as genetic algorithms [95], particle swarm optimization [96], and ant colony optimization


> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=62,41,65,24&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > Variations of A* include Theta* [99], which propagates information along edges, and D* [100], a dynamic variation that is able to handle changing environment

> [!PDF|note] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=65,34,67,12&color=note|Towards Intelligent Cooperative Robotics, p.12]]
> > euristic methods have good overall performance they generally require long execution times

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=70,0,72,14&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > Sampling-based methods include probabilistic roadmap method (PRM) and rapidly-exploring random trees (RRT

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=95,13,97,29&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > DL is most commonly used to improve the random sample generation of sampling-based motion planning methods to improve efficiency

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=103,36,104,56&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > DL methods have also been applied to constrained motion planning applications

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=111,22,115,9&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > Reinforcement learning (RL) methods have also been widely investigated which use virtual training environments to teach behaviors to agents, which conduct actions within the environment to optimize reward functions

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=117,53,119,33&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > These approaches are most commonly applied to complex transfer motion tasks such as manipulation

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=12&selection=126,25,131,29&color=yellow|Towards Intelligent Cooperative Robotics, p.12]]
> > ML models suffer from challenges of data acquisition. ML models require sufficient training points either through simulation or physical trials which can be incredibly time consuming 

**Motion planning constraints**
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=13&selection=12,15,23,61&color=yellow|Towards Intelligent Cooperative Robotics, p.13]]
> > ngston et al. identified five methodological approaches to handling constraints for sampling-based motion planning: 1) relaxation, where a tolerance is added to the constraint function from which sampling is conducted, 2) projection, where a configuration is projected onto the surface of the implicit manifold and stepped backward into a satisfactory configuration, 3) tangent space, where a tangent space is generated from the constraint function, 4) atlas, where a piecewise linear approximation of the manifold is created using tangent spaces, and 5) reparameterization, where the robot configuration is reparameterized to allow for direct sampling of a satisfactory configuration space


> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=13&selection=30,10,32,34&color=yellow|Towards Intelligent Cooperative Robotics, p.13]]
> > complex planning environments found in C-RAM systems can be represented as constraint manifolds to improve motion planning capabilities

### 3.2.2 Software
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=13&selection=84,23,87,56&color=yellow|Towards Intelligent Cooperative Robotics, p.13]]
> > anufacturer software offers great ease of use at the cost of customization and is most frequently used for fundamental RAM applications which typically use robotic arms from well-established robotics manufacturer

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=13&selection=123,41,126,39&color=yellow|Towards Intelligent Cooperative Robotics, p.13]]
> > This framework was later improved upon in ROS2 which was redesigned with production applications in mind to improve major shortcomings in ROS (e.g. not real-time capable

# 4. Process Control for RAM
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=14&selection=28,46,31,51&color=yellow|Towards Intelligent Cooperative Robotics, p.14]]
> > arious types of ML models have been employed for defect detection and quality characterization including hyperdimensional computing [129] and neural network-based architectures

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=15&selection=9,0,11,33&color=yellow|Towards Intelligent Cooperative Robotics, p.15]]
> > The speed at which inference is conducted affords real time monitoring of defects and control to greatly improve the quality of AM processes

> [!PDF|note] [[Towards Intelligent Cooperative Robotics.pdf#page=15&selection=12,0,20,41&color=note|Towards Intelligent Cooperative Robotics, p.15]]
> > Feedback control from sensor feedback can occur in three main stages of the AM process: 1) pre-process, where previous sensor feedback is used to inform future processes and adjust parameters before manufacturing, 2) inter-layer, where sensor feedback is used to adjust the manufacturing process in between the creation of layers before the subsequent layer is started, and 3) mid-layer, where sensor feedback is used to adjust the manufacturing process while material is being deposited within a layer.

## 4.1 Pre-Process Calibration
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=15&selection=35,8,40,16&color=yellow|Towards Intelligent Cooperative Robotics, p.15]]
> > Slicing parameters impact the generation of the toolpath and include variables such as road width, layer height, infill percentage, and infill pattern. These parameters are typically static

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=15&selection=40,18,44,20&color=yellow|Towards Intelligent Cooperative Robotics, p.15]]
> > Manufacturing parameters refer to parameters of the extruder and the AM system and include variables such as feed ratio, feed rate, and extruder temperature. These parameters are set during pre-process but are often modified on the fly.

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=15&selection=54,20,57,40&color=yellow|Towards Intelligent Cooperative Robotics, p.15]]
> >  FFF/FDM which use hot-end nozzles have process parameters including nozzle temperature, bed temperature, and extrusion multiplier (e.g. ratio between extrusion feed rate and rate of TCP motion


> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=16&selection=22,0,24,52&color=yellow|Towards Intelligent Cooperative Robotics, p.16]]
> > Determining the optimal pose of the workpiece is paramount to ensuring high quality RAM manufacturing of parts in both single and multi-arm systems

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=16&selection=58,41,61,27&color=yellow|Towards Intelligent Cooperative Robotics, p.16]]
> >  To improve process planning within WAAM systems, a corner detection algorithm is implemented such that the robot feed rate is increased during sharp corner


### 4.1.1 C-RAM Frame Calibration
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=16&selection=78,0,82,12&color=yellow|Towards Intelligent Cooperative Robotics, p.16]]
> > C-RAM systems operate within a global frame to work on a common part which requires accurate registration of each arm’s position. The base frame of each individual robot must be registered within a base frame through a calibration process

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=16&selection=85,15,134,8&color=yellow|Towards Intelligent Cooperative Robotics, p.16]]
> > The calibration process can be formulated as 𝐴𝑋𝐵 = 𝑌 𝐶𝑍 as proposed by Wu et al. [142] where all variables are homogeneous transforms, specifically the arm 1 base to hand transform 𝐴, hand to eye (sensor) transform 𝑋, eye to tool (of arm 2) transform 𝐵, flange (as opposed to hand) of arm 2 to tool transform 𝑍, arm 2 base to flange transform 𝐶, and arm base 1 to arm base 2 transform 𝑌 . By knowing transforms of variables 𝐴, 𝐵, and 𝐶 from data acquisition, unknown transforms 𝑋, 𝑌 , 𝑍 can be solved simultaneousl

$$
AXB = YCZ
$$
$A$ - arm 1 base to hand transform
$X$ - hand to eye (sensor) transform
$B$ - eye to tool transform

$Z$ - flange (as opposed to hand) of arm 2 to tool transform
$C$ - arm base 1 to arm base 2 transform


> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=16&selection=139,0,144,33&color=yellow|Towards Intelligent Cooperative Robotics, p.16]]
> > Wang et al. proposed a projection-based arm-to-arm calibration method offering an improved maximum error of calibration to previous work using only two calibration points

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=17&selection=18,20,24,53&color=yellow|Towards Intelligent Cooperative Robotics, p.17]]
> > optical and calibration target [148, 149], optical and ArCo marker target [150], and binocular vision [151]. While these methods successfully solve arm-to-arm calibration they require piece-wise solutions to handle more than two arms in a single system

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=17&selection=34,33,44,1&color=yellow|Towards Intelligent Cooperative Robotics, p.17]]
> > Each arm then scans a calibration block using the structured light scanner; these point clouds are then processed using the proposed algorithm to register all point clouds together. From this solution, the corresponding transformation matrices can then be determined to give the final calibration solution for the robotic arms within the system which achieved an orientation accuracy of 0.091°

## 4.2 Inter-Layer Control
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=17&selection=70,0,77,48&color=yellow|Towards Intelligent Cooperative Robotics, p.17]]
> > Ultrasonic testing is a class of sensing techniques widely used for DED processes where the porosity of fabricated parts is a pressing challenge. Chabot et al. investigated implementation of phased array ultrasonic testing

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=17&selection=91,37,99,24&color=yellow|Towards Intelligent Cooperative Robotics, p.17]]
> > Magnoni et al. [154] implemented an Omron laser triangulation sensor onto the end effector of a 6-DoF FFF IRB-2600 robot arm. After a layer is completed, a post-layer inspection process takes place which follows the original path at an offset height. The measured height is then used to adjust the commanded layer height of the next layer

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=17&selection=104,0,106,10&color=yellow|Towards Intelligent Cooperative Robotics, p.17]]
> > The method implemented results in geometric deviation from the original CAD design

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=18&selection=2,10,6,54&color=yellow|Towards Intelligent Cooperative Robotics, p.18]]
> >  Rebaioli et al. [155] to include online re-slicing of the original CAD model to retain the original geometry. According to the corrected layer height used in subsequent layers, the remaining region of the CAD model was resliced to ensure that the correct overall height was retained

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=18&selection=98,40,103,12&color=yellow|Towards Intelligent Cooperative Robotics, p.18]]
> > artificial defects were successfully detected by the ECT sensing method while natural porosity defects were not captured. Ultrasonic scanning successfully identified both artificial pocket and natural porosity defects which ranged from 0.1mm to 0.2mm diameter in size

## 4.3 Mid-Layer Control

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=18&selection=119,0,122,11&color=yellow|Towards Intelligent Cooperative Robotics, p.18]]
> > Real-time process correction can allow for the mitigation and correction of defects during the manufacturing process. To realize such control equally fast sensing techniques must be employed

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=19&selection=26,0,30,14&color=yellow|Towards Intelligent Cooperative Robotics, p.19]]
> > Laser scanning is best suited for high-fidelity quantitative characterization of defects which can then be used to infer mechanical properties or correct errors mid process. Data analysis methods must be robust due to the high bandwidth of data,

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=19&selection=32,0,34,13&color=yellow|Towards Intelligent Cooperative Robotics, p.19]]
> > Real-time infrared imaging offers valuable insight into thermal dynamics which can be linked to phenomena such as melt pools

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=19&selection=95,26,98,48&color=yellow|Towards Intelligent Cooperative Robotics, p.19]]
> > mages captured in-situ are filtered using canny edge detection, then input into a convolutional neural network (CNN) architecture to detect valley or hump defects during the manufacturing process

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=20&selection=14,0,16,55&color=yellow|Towards Intelligent Cooperative Robotics, p.20]]
> > The use of multiple different sensors in a heterogeneous manner can offer enhanced sensing capabilities able to capture a wide range of dynamics across varying fidelities

## 4.4 Digital Twin
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=20&selection=43,52,47,39&color=yellow|Towards Intelligent Cooperative Robotics, p.20]]
> > While digital twins for AM is still a developing field, the general approach for digital twins focuses on the use of sensor feedback to inform ML models which simulate physical phenomena using both real-time and historical dat

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=20&selection=50,29,54,18&color=yellow|Towards Intelligent Cooperative Robotics, p.20]]
> > Digital models of the physical system are then used to monitor system quality, control processes to improve process quality and predict physical phenomena and their impact on the mechanical properties of the finished component

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=3,10,5,16&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > AM process modeling can be subdivided according to the micro, meso, and macro-level physical processes that are modeled

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=5,18,7,15&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > Micro-level physical modeling estimates physical processes such as microstructures, residual stress, and coalescence

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=9,0,10,57&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > Meso-level physical modeling estimates features including cracks, voids, and geometric deviation

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=11,0,13,16&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > Macro-level physical modeling captures part-level characteristics such as Young’s modulus, fatigue life, and ultimate tensile strength

# 5. Challenges and Opportunities
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=60,23,64,26&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > From this review of recent literature, the authors note 5 specific gaps that can be expanded upon in future research: unified slicing software, informed slicing, intelligent C-RAM systems, informed part decomposition, and digital twin software.

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=75,0,79,38&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > Conventional slicing software follows paradigms that were originally developed for single-extruder 3 DoF platforms, which require further modification to support multi-plane, non-planar, or multi-extruder printing

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=94,0,100,39&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > particularly for RAM systems, software such as the 𝑆3 slicer by Zhang et al. [188] have been developed by researchers as open-source solutions

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=21&selection=114,0,118,53&color=yellow|Towards Intelligent Cooperative Robotics, p.21]]
> > Advanced slicing methods including non-planar and multi-plane have been investigated in DED and especially ME processes, but few studies have investigated their impact on the mechanical properties of the slicing method selected.

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=22&selection=10,28,13,52&color=yellow|Towards Intelligent Cooperative Robotics, p.22]]
> > Handling the motion planning of multiple arms requires fabrication while also preventing collisions which can alter the ideal toolpath plan and cause varying cooling rates within the part

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=22&selection=36,0,48,24&color=yellow|Towards Intelligent Cooperative Robotics, p.22]]
> > C-RAM fabrication platforms necessarily have segment boundaries located within overlapping build regions for large-scale system configurations. These boundaries present an additional point of failure in both DED processes, where thermal distributions result in residual stresses and warping, and in ME processes, where discontinuous deposition leads to anisotropic properties. Therefore, the determination of segment interfaces and the selection of segment locations is critical to maintaining mechanical propertie

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=22&selection=104,0,107,50&color=yellow|Towards Intelligent Cooperative Robotics, p.22]]
> > For manufacturing systems (e.g., CNC, FFF, DED) with trivial inverse kinematic solutions (e.g., gantry) toolpath planning implicitly solves the motion planning problem

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=22&selection=120,0,125,51&color=yellow|Towards Intelligent Cooperative Robotics, p.22]]
> > Motion planning is then solved separately as an afterthought giving no bearing to the toolpath that is generated. It is known that factors such as stiffness of the robot arm [190] and approach direction of the TCP [140] can affect the repeatability and manufacturing quality of the system

> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=22&selection=134,0,138,45&color=yellow|Towards Intelligent Cooperative Robotics, p.22]]
> > The conventional slicing procedure for robotic arms should incorporate the motion planning step such that the impact of the toolpath generation considers the impact on motion planning to realize optimized toolpaths for RAM system

# 6 Conclusion
> [!PDF|yellow] [[Towards Intelligent Cooperative Robotics.pdf#page=23&selection=15,36,24,54&color=yellow|Towards Intelligent Cooperative Robotics, p.23]]
> > System control encompasses the generic control of RAM systems, including slicing methods used to generate toolpaths and motion planning methods for high degrees of freedom robotic arms. Process control focuses on specific AM processes, involving sensorbased feedback during pre-process, inter-layer, or mid-layer stages. This feedback can be integrated with digital twin software, enabling predictive control of AM processes.

