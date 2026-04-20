# TurtleBot 2 ROS 2 Custom

This is a custom repository for the TurtleBot 2 (Kobuki) mobile base, migrated to ROS 2 Humble. 
It has been detached from the original Git history to allow for custom URDF modifications and other localized changes.

## Installation & Setup

### 1. Prerequisites
Ensure you have ROS 2 Humble installed on your Ubuntu 24.04 (or 22.04) system.

Install necessary system dependencies:
```bash
sudo apt-get update
sudo apt-get install -y     ros-humble-kobuki-velocity-smoother     ros-humble-sophus     ros-humble-teleop-twist-keyboard     ros-humble-joy-teleop     ros-humble-teleop-twist-joy
```

### 2. Build the Package
Navigate to your workspace root and build the packages:
```bash
cd ~/skuba_ws
# Install any missing dependencies via rosdep
rosdep install -i --from-path src --rosdistro humble -y

# Build the workspace
colcon build --symlink-install --executor sequential
```

### 3. Source the Workspace
After every build, source the setup file:
```bash
source ~/skuba_ws/install/setup.bash
```

## Usage

### Launching the Robot
To start the Kobuki node:
```bash
ros2 launch kobuki_node kobuki_node-launch.py
```

### Teleoperation (Keyboard)
In a new terminal (don’t forget to source), run:
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args --remap cmd_vel:=commands/velocity
```

### Customizing URDF
The URDF files can be found and modified within the `kobuki_description` or `turtlebot2_description` packages (depending on which package you are using for the model). Once changed, rebuild the workspace to apply changes.

---
*Derived from the original idorobotics/turtlebot2_ros2 project.*
