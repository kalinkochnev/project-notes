- Nodes should do one logical thing
- Communicate with other nodes
- Nodes can publish or subscribe to "topics"
	- Used to send/receive data to other nodes
- Nodes have parameters to configure in real time

Service client - another node performs computation on behalf
Service server - provide functionality to other nodes

**Long running computations**
Action client/server - same as service clients, but for long running computations

# Discovery
1. Upon startup node advertises to other nodes on network (same `ROS_DOMAIN_ID`)
2. Nodes periodically advertise so connections can be made after initial discovery
3. Nodes advertise when they go offline



## Topics
- Used for continuous data streams (state, sensor data, etc)
- A publisher needs a "topic" name so subscribers can find it
## Services
- Request/response to a server to do a computation and return a result
- Described with `.srv` files
- A "service server" is the node that accepts a procedure request
- Only one *service server* should be provided per service name
- There can be as many *service clients* with the same name

## Actions
- Long running request/responses
- Can provide feedback while happening (ex: progress percentage)


# Parameters
- Used to configure individual nodes at startup and/or runtime
- Lifetime of parameter is tied to lifetime of the node


- Nodes need to declare parameters during its lifetime
- Callbacks can be created when parameters are changed ("pre-set", "on-set", "post-set")
- Initial parameters can be set with CLI args or YAML files

# Command line tools
`ros2 --help`
Available sub-commands

| **sub-command** | **Description**                                                                   |
| --------------- | --------------------------------------------------------------------------------- |
| `action`        | Introspect/interact with ROS actions                                              |
| `bag`           | Record/play a rosbag                                                              |
| `component`     | Manage component containers                                                       |
| `daemon`        | Introspect/configure the ROS 2 daemon                                             |
| `doctor`/`wtf`  | Check ROS setup for potential issues                                              |
| `interface`     | Show information about ROS interfaces                                             |
| `launch`        | Run/introspect a launch file                                                      |
| `lifecycle`     | Introspect/manage nodes with managed lifecycles                                   |
| `multicast`     | Multicast debugging commands                                                      |
| `node`          | Introspect ROS nodes                                                              |
| `param`         | Introspect/configure parameters on a node                                         |
| `pkg`           | Introspect ROS packages                                                           |
| `run`           | Run ROS nodes                                                                     |
| `security`      | Configure security settings                                                       |
| `service`       | Introspect/call ROS services                                                      |
| `test`          | Run a ROS launch test                                                             |
| `topic`         | Introspect/publish ROS topics                                                     |
| `trace`         | Tracing tools to get information on ROS nodes execution (only available on Linux) |

## Launch file
https://design.ros2.org/articles/roslaunch.html
- Specifies which programs to run, where to run them, and what args to pass
- Used to automate process instead of launching nodes by hand