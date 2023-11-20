# jackal
======

Common packages for Jackal, including messages and robot description. These are packages relevant
to all Jackal workspaces, whether simulation, desktop, or on the robot's own headless PC.

### Topic name 
- imu: /imu/data/*
- gps: /navsat/*
- pointcloud: /velodyne_points


## Environment

``` bash
sudo apt-get install ros-noetic-jackal-simulator ros-noetic-jackal-desktop

git clone https://github.com/DrawingProcess/jackal
```

## jackal Spawn
### jackal 2d lidar
``` bash
roslaunch jackal_gazebo jackal_world.launch config:=front_laser

roslaunch jackal_viz view_robot.launch

rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

### jackal 3d lidar
``` bash
roslaunch jackal_gazebo jackal_world.launch config:=3d_lidar

rosrun jackal_velodyne pcl_filter_node # topic /velodyne_points to /scan

roslaunch jackal_viz view_robot.launch

rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

## Navigation
### NAVIGATION WITHOUT A MAP
``` bash
# To launch the navigation demo, run:
roslaunch jackal_navigation odom_navigation_demo.launch

# To visualize with the suggested rviz configuration launch:
roslaunch jackal_viz view_robot.launch config:=navigation
```

### MAKING A MAP
```bash
# Jackal generates a map using gmapping. 
roslaunch jackal_navigation gmapping_demo.launch

# And on your workstation, launch rviz with the suggested configuration:
roslaunch jackal_viz view_robot.launch config:=gmapping

# When you’re satisfied, you can save the produced map using map_saver:
rosrun map_server map_saver -f mymap
```

### NAVIGATION WITH A MAP
```bash
# To start the AMCL demo:
roslaunch jackal_navigation amcl_demo.launch map_file:=/path/to/my/map.yaml

# To visualize with the suggested rviz configuration launch:
roslaunch jackal_viz view_robot.launch config:=localization
```