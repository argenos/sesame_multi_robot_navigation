# SESAME Multi Robot Simulation

## Installation

These instructions were adapted from the public [TIAGo Installation Tutorial](http://wiki.ros.org/Robots/TIAGo/Tutorials/Installation/InstallUbuntuAndROS) to include fixes to run a multi-robot simulation and install the ExSce Management tools.

Follow the necessary steps to [create a catkin workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace).

Use `rosinstall` to clone all the required ROS packages. If you haven't cloned this repo, first get the rosinstall file, for example:

```bash
cd ~/catkin_ws
wget https://raw.githubusercontent.com/hbrs-sesame/sesame_multi_robot_navigation/main/pal_sesame.rosinstall

```

Then run rosinstall:

```bash
rosinstall src pal_sesame.rosinstall
```

Install the dependencies for the cloned packages:

```bash
rosdep install -y --from-paths src --ignore-src --rosdistro noetic --skip-keys "urdf_test omni_drive_controller orocos_kdl pal_filters libgazebo9-dev pal_usb_utils speed_limit_node camera_calibration_files pal_moveit_plugins pal_startup_msgs pal_local_joint_control pal_pcl_points_throttle_and_filter current_limit_controller hokuyo_node dynamixel_cpp pal_moveit_capabilities pal_pcl dynamic_footprint gravity_compensation_controller pal-orbbec-openni2 pal_loc_measure pal_map_manager ydlidar_ros_driver"
```

Build your workspace:

```bash
catkin build
```

Source your catkin workspace:

```bash
source devel/setup.bash
```

Finally, to check that everything works as expected, try launching a scenario:

```bash
roslaunch exsce_ros scenario.launch scenario_id:=scenario_x
```
