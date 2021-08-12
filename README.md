## Arbotix Drivers

This repository contains the Arbotix ROS drivers, catkinized, and ready for ROS Noetic.


# how to run this stuff

- install the arbotix firmware on the arbotix-m controller
  [see](https://github.com/ZiyunClaudeWang/Arduino_setup)

- make sure to switch the power supply plug to external power for the
  servos

- set up udev rules [copied from here](https://github.com/RobotnikAutomation/widowx_arm)
   - copy the udev rules under ``config/58-widowx.rules`` to ``/etc/udev/rules.d/``
   - adjust the SERIAL field in the rules to match your usb-to-serial device:
```
udevadm info -a -n /dev/ttyUSB0| grep serial 
```
 
- catkin build this workspace
- adjust the yaml configuration file in
  ``arbotix_python/launch/turret.yaml``
- run the server:
```
roslaunch arbotix_python turret.launch
```
- set the speed of the servo:
```
rosservice call /head_pan_joint/set_speed "speed: 0.1"
```
- switch it on or off:
```
rostopic pub /head_pan_joint/spin std_msgs/Bool "data: true"
```
  
