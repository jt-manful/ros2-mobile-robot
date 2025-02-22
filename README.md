# ROS2 Mobile Robot with Arm

This project involves building a mobile robot with a simple two-axis robotic arm using ROS2. The robot consists of a mobile base with wheels and a robotic arm mounted on top. The project uses URDF/Xacro for robot description and Gazebo for simulation.

## Project Structure

```
my_robot_ws/
├── src/
│   ├── my_robot_description/
│   │   ├── urdf/
│   │   │   ├── base.xacro
│   │   │   ├── arm.xacro
│   │   │   ├── my_robot.urdf.xacro
│   │   ├── launch/
│   │   │   ├── display.launch.py
│   │   │   ├── gazebo.launch.py
│   ├── my_robot_bringup/
│   │   ├── launch/
│   │   │   ├── bringup.launch.py
```

## Features

- Mobile base with wheels
- Simple two-joint robotic arm
- Simulated in Gazebo
- Uses ROS2 for robot control

## Installation and Setup

### 1. Install ROS2 and Dependencies

Follow the ROS2 installation guide for your OS:\
[ROS2 Installation](https://docs.ros.org/en/ros2_documentation/index.html)

### 2. Clone the Repository

```sh
git clone https://github.com/yourusername/my_robot_ws.git
cd my_robot_ws
```

### 3. Build the Workspace

```sh
colcon build --symlink-install
source install/setup.bash
```

### 4. Launch the Robot in RViz

```sh
ros2 launch my_robot_description display.launch.py
```

### 5. Launch the Robot in Gazebo

```sh
ros2 launch my_robot_description gazebo.launch.py
```

### 6. Control the Arm

Send a command to move the arm:

```sh
ros2 topic pub -1 /set_joint_trajectory trajectory_msgs/msg/JointTrajectory '{header: {frame_id: arm_base_link}, joint_names: ["arm_base_forearm_joint", "forearm_hand_joint"], points: [ {positions: {0.0, 0.0}} ]}'
```

