# Multi-Robot Factory Automation System

[![Project Demo](https://github.com/Mark-Moawad/Hello-Real-World-with-ROS/blob/master/preview.png)](https://drive.google.com/file/d/1CaGhjmFSNeky4_XKoFSbqpe0pyfgFG6T/view?usp=sharing "Factory Automation Demo")

A comprehensive ROS-based robotic automation system designed for multi-robot factory environments. This project implements a complete software stack for coordinating mobile robots and manipulators in a simulated industrial setting.

## Overview

This system provides an integrated solution for warehouse and factory automation, featuring autonomous navigation, manipulation control, and behavior-based coordination. The implementation leverages modern ROS tools and frameworks to deliver a scalable, modular architecture suitable for real-world industrial applications.

## Key Features

- **Multi-Robot Coordination**: Seamless integration of mobile robots and industrial manipulators
- **Autonomous Navigation**: SLAM-based mapping and path planning for mobile platforms
- **Advanced Manipulation**: Motion planning and control using MoveIt! framework
- **Computer Vision Integration**: Perception capabilities for object detection and tracking
- **Behavior Management**: FlexBE-based state machine implementation for complex task orchestration
- **Gazebo Simulation**: High-fidelity physics simulation for testing and validation

## System Architecture

### Core Components

- **Navigation Stack**: Implements gmapping for SLAM and move_base for autonomous navigation
- **Manipulation System**: MoveIt!-based motion planning for robotic arms
- **Factory States**: Custom state implementations for factory-specific operations
- **Vision Processing**: TF-based coordinate transformations and sensor fusion
- **Behavior Orchestration**: FlexBE framework for hierarchical task planning

### Robot Models

The system includes complete URDF models with:
- Mobile robot platforms with differential drive kinematics (TurtleBot3)
- Multi-DOF manipulator arms with gripper end-effectors (UR5 and UR10 robotic arms)
- Sensor suites including cameras, LiDARs, and depth sensors

## Technical Stack

- **ROS Version**: ROS Noetic (compatible with ROS Melodic)
- **Simulation**: Gazebo 11
- **Motion Planning**: MoveIt! 1.0
- **Behavior Trees**: FlexBE 2.0
- **Languages**: Python, C++, XML (URDF/SDF)

## Installation

### Prerequisites

```bash
# ROS Noetic on Ubuntu 20.04
sudo apt-get update
sudo apt-get install ros-noetic-desktop-full
sudo apt-get install ros-noetic-moveit ros-noetic-navigation
sudo apt-get install ros-noetic-flexbe-behavior-engine
```

### Building the Workspace

```bash
# Clone the repository
git clone https://github.com/Mark-Moawad/Multi-Robot-Factory-with-ROS.git
cd Multi-Robot-Factory-with-ROS

# Build with catkin
catkin_make

# Source the workspace
source devel/setup.bash
```

## Usage

### Launch Factory Simulation

```bash
# Start the complete factory environment
roslaunch hrwros_gazebo hrwros_environment.launch

# Launch navigation stack
roslaunch hrwros_week3 turtlebot_navigation.launch

# Start manipulation system
roslaunch hrwros_moveit_config moveit_planning_execution.launch
```

### Running Behavior Trees

```bash
# Launch FlexBE for behavior management
roslaunch flexbe_behaviors factory_automation_behavior.launch
```

## Project Structure

```
src/
├── hrwros/                      # Core factory simulation packages
├── hrwros_factory_states/       # Custom state implementations
├── hrwros_factory_behaviors/    # FlexBE behavior definitions
├── hrwros_gazebo/               # Simulation environments and models
├── hrwros_moveit_config/        # Motion planning configuration
├── hrwros_support/              # URDF models and meshes
└── hrwros_week*/                # Modular feature packages
```

## Features Breakdown

### Autonomous Navigation
- Real-time SLAM with occupancy grid mapping
- Dynamic obstacle avoidance
- Multi-waypoint path planning
- Adaptive localization

### Robotic Manipulation
- Inverse kinematics solving
- Collision-aware planning
- Trajectory optimization
- Gripper control for pick-and-place operations

### Vision System
- Coordinate frame management with TF
- Sensor data fusion
- Object pose estimation
- Camera-based localization

### Behavior Control
- Hierarchical state machines
- Event-driven task execution
- Error recovery mechanisms
- Real-time monitoring and control

## Development

### Adding New States

Custom states can be added to `hrwros_factory_states/src/` following the FlexBE state API.

### Modifying Robot Models

URDF definitions are located in `hrwros_support/urdf/` and can be extended with additional sensors or actuators.

### Customizing Behaviors

Behavior trees are defined in `hrwros_factory_behaviors/` and can be edited using the FlexBE App.

## Contributing

Contributions are welcome! Please follow standard ROS package conventions and include appropriate documentation.

## License

This project is licensed under the MIT License.

## Contact

For questions or collaboration opportunities, please open an issue on GitHub.

## Acknowledgments

Built with ROS (Robot Operating System) and leveraging the open-source robotics community's excellent tools and frameworks.
