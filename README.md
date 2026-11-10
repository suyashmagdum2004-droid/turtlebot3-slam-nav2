# TurtleBot3 SLAM and Autonomous Navigation using ROS 2

## Project Overview

This project demonstrates Simultaneous Localization and Mapping (SLAM) and autonomous navigation using a TurtleBot3 Burger robot in a Gazebo simulation environment.

The robot uses LiDAR sensor data to map its surroundings, localizes itself within the generated map, and navigates autonomously to user-defined goal positions using the ROS 2 Navigation Stack (Nav2).


## Technologies Used

- ROS 2 Humble
- Ubuntu 22.04
- Gazebo 11
- TurtleBot3 Burger
- Cartographer SLAM
- Nav2 Navigation Stack
- RViz2
- LiDAR Sensor

## Project Features

- TurtleBot3 simulation in Gazebo.
- Environment mapping using LiDAR and Cartographer.
- 2D occupancy grid map generation and saving.
- Robot localization using the generated map.
- Autonomous goal navigation using Nav2.
- Visualization of the robot, map and navigation goals in RViz2.

## Project Structure

```text
turtlebot3-slam-nav2/
├── maps/
│   ├── turtlebot3_map.pgm
│   └── turtlebot3_map.yaml
├── screenshots/
├── launch/
├── config/
├── worlds/
├── README.md
└── .gitignore
```

## Setup Requirements

- Ubuntu 22.04
- ROS 2 Humble
- Gazebo 11
- TurtleBot3 ROS 2 packages
- Navigation2
- Cartographer

## Running the Project

### 1. Source ROS 2 and TurtleBot3 workspace

```bash
source /opt/ros/humble/setup.bash
source ~/turtlebot3_ws/install/setup.bash
export TURTLEBOT3_MODEL=burger
```

### 2. Launch Gazebo simulation

```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

### 3. Start SLAM mapping

```bash
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
```

Use keyboard teleoperation to move the robot and explore the environment while Cartographer builds the map.

### 4. Save the map

```bash
ros2 run nav2_map_server map_saver_cli -f ~/turtlebot3-slam-nav2/maps/turtlebot3_map
```

### 5. Launch autonomous navigation

```bash
ros2 launch turtlebot3_navigation2 navigation2.launch.py \
use_sim_time:=True \
map:=$HOME/turtlebot3-slam-nav2/maps/turtlebot3_map.yaml
```

Use RViz2 to initialize the robot's position with **2D Pose Estimate** and send navigation goals using **Nav2 Goal**.

## Project Results

- Generated a 2D occupancy grid map of the simulated environment.
- Demonstrated LiDAR-based environment mapping.
- Configured autonomous navigation using Nav2.
- Tested goal-based navigation in a Gazebo simulation environment.

## Future Improvements

- Develop custom Gazebo environments.
- Tune Nav2 planner and controller parameters.
- Improve navigation performance and obstacle avoidance.
- Extend the project to a physical TurtleBot3 robot.

## Vedios
Mapping:- https://1drv.ms/v/c/b88c68f3f37e1421/IQCL9rSbEME7S4EPCo2jI3ISAQ-okMNs36N-33AucpkE0Tc?e=CXvyBr

Result:- https://1drv.ms/v/c/b88c68f3f37e1421/IQADtGNOYmwAT6HBjACb0ZcRATTeUT_9BX7gaGk-ano-D4E?e=QNhnd6

## Author

**Suyash Magdum**

Robotics and Automation Engineering Student
