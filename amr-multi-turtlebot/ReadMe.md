# Multi Turtlebot

This package launches 4 turtlebots on gazebo with amcl and move base capabilities.

## Instructions to launch

Clone this repo and run `catkin_make` and `source devel/setup.bash`

Then run,

```bash
roslaunch multi_turtlebot main.launch
```
## Information on how to use this package (Robot Operation and Changing world or map).

**Each robot has a separate namespace for topics and a namespace for frames**

| Robot     | Topic Namespace | Frame Namespace | Topic Example                  | Frame Example            |
| --------- |:---------------:|:---------------:|:------------------------------:| ------------------------:|
|Turtlebot 1| /robot1         | /robot1_tf      | /robot1/odom                   | /robot1_tf/base_link     |
|Turtlebot 2| /robot2         | /robot2_tf      | /robot2/move_base_simple/goal  | /robot2_tf/base_link     |
|Turtlebot 3| /robot3         | /robot3_tf      | /robot3/amcl_pose              | /robot3_tf/base_link     |
|Turtlebot 4| /robot4         | /robot4_tf      | /robot4/move_base_simple/goal  | /robot4_tf/base_link     |

There are some frames and topics common for all robots such as **/map** frame and topics such as **/gazebo/<topic_name>**. These are common for all robots because they are robot independent.

Every Team can add this topic namespace and frame namespace to their code so that they publish to their respective robots.

The map_server is launched in **robots.launch**. The argument **map_file** points to the path to the map file. This can be changed to change the map file.

The initial positions of the robots are also specified in the **robots.launch**. This can be changed for each robot separately in the same file. Note that the changes must be made in arguments **init_pose** and **init_pose_x**, **init_pose_y**, **init_pose_a**.

The world and world position can be changed in **main.launch** lines 15 and 16, **spawn_world** node. The path to the world model and -x, -y parameters for the position.
