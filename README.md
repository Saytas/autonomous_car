# Install

$ sudo apt-get install libi2c-dev

# Clone the repository

$ git clone https://gitlab.com/bradanlane/ros-i2cpwmboard.git

$ source devel/setup.bash

$ catkin_make

$ source devel/setup.bash

$ cd /src/ros-i2cpwmboard/launch

$ sudo nano i2cpwm_node.launch


### Replace this
<launch>
  <node pkg="i2cpwm_board" name="i2cpwm_board_node" type="i2cpwm_board" output="screen" launch-prefix="sudo -E ">
  </node>
</launch>


### With this
<launch>
  <node pkg="i2cpwm_board" name="i2cpwm_board_node" type="i2cpwm_board" output="screen">
  </node>
</launch>


### throttle="1" values= starts from 348
### Steering="2" values= 265,269,270 - 365
### throttle:
### 	linear.x
### steering
### 	angular.z

$ catkin_create_pkg auto_control rospy

$ rosrun i2cpwm_board i2cpwm_board # On Pi (Master)

$ rosrun auto_control auto_control.py # On Pi (Master)

$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py 	# On host machine

### Instead of above

$ roslaunch auto_control auto_control.launch

$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py 
