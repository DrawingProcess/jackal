jackal
======

Common packages for Jackal, including messages and robot description. These are packages relevant
to all Jackal workspaces, whether simulation, desktop, or on the robot's own headless PC.

### Topic name 
- imu: /imu/data/*
- gps: /navsat/*
- pointcloud: /velodyne_points

### Execution

``` bash
sudo apt-get install ros-noetic-jackal-simulator ros-noetic-jackal-desktop

git clone https://github.com/DrawingProcess/jackal

roslaunch jackal_gazebo jackal_world.launch config:=3d_lidar
roslaunch jackal_viz view_robot.launch

rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```