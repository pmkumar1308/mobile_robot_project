This repo contains coding done while following the tutorials offered on the Articulated Robotics youtube 
channel in the [Building a mobile robot playlist](https://www.youtube.com/playlist?list=PLunhqkrRNRhYAffV8JDiFOatQXuU-NnxT). Only the 
the simulation part of the tutorials is implemented.

The following concepts were learnt by following this tutorial:
1. Defining urdf files and compiling them through xacro
2. Running a mobile robot in a Gazebo simulation through a Gazebo differential drive plugin
3. Concepts of LiDARs and adding Gazebo ray_sensor plugins to simulate a LiDAR in the simulator

# Run the robot in Gazebo:

## Spawning the robot
### Method 1: to learn the workflow for spawning a robot in Gazebo

1. Start the `robot_state_publisher` through the `rsp.launch.py` file to publish the the robot description of the robot defined in the description folder
Make sure it is started with use_sim_time=True because the time from the Gazebo simulation has to be used by the nodes launched in the launch file. This flag will be `true` for all nodes when the robot is in a simulation environment.

```bash
ros2 launch mobile_robot_project rsp.launch.py use_sim_time:=true
```

2. Start `gazebo_ros`:
```bash
ros2 launch gazebo_ros gazebo.launch.py
```

3. Spawn the robot in Gazebo:
We use the spawn_entity script given by gazebo_ros package.
```bash 
ros2 run gazebo_ros spawn_entity -topic robot_description -entity <some-name-for-your-bot-or-entity>
```

### Method 2: through a launch file

A launch file `launch_sim.launch.py` contains all the above steps, to launch the simulation with a spawned robot in a pre-defined world(Here the `obstacles.world` file in the worlds folder)

```bash
ros2 launch mobile_robot_project launch_sim.launch.py world:=./src/mobile_robot_project/worlds/obstacles.world
```

## Moving the robot
The robot can be moved through the keyboard using the  `teleop_twist_keyboard` node in `teleop_twist_keyboard` package. It publishes the robot linear and angular velocities to the `/cmd_vel` topic

```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
