## Robot Package Template

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

A launch file `launch_sim.launch.py` contains all the above steps, to launch it:

```bash
ros2 launch mobile_robot_project launch_sim.launch.py
```
