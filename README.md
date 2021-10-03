
cd catkin_ws/src

git clone https://github.com/Goohuram/sma_multiturtle.git

cd ..

catkin_make

roslaunch sma_multiturtle launch_gazebo.launch

rosrun map_server map_server ~/map.yaml

roslaunch sma_multiturtle turtle_multiple.launch multi_robot_name:=tb3_0 x_pos:=-2.0 y_pos:=1.0

roslaunch sma_multiturtle turtle_multiple.launch multi_robot_name:=tb3_1 x_pos:=-2.0 y_pos:=0.0

roslaunch sma_multiturtle turtle_multiple.launch multi_robot_name:=tb3_2 x_pos:=-2.0 y_pos:=-1.0



Follower

rosrun sma_multiturtle inter_leader_follower.py tb3_0 tb3_1

rosrun sma_multiturtle inter_leader_follower.py tb3_1 tb3_2


teletop

ROS_NAMESPACE=tb3_0 rosrun turtlebot3_teleop turtlebot3_teleop_key

join

roslaunch sma_multiturtle launch_gazebo.launch

rosrun map_server map_server ~/map.yaml

roslaunch sma_multiturtle turtle_multiple.launch multi_robot_name:=tb3_0 x_pos:=0.0 y_pos:=2.0

roslaunch sma_multiturtle turtle_multiple.launch multi_robot_name:=tb3_1 x_pos:=-2.0 y_pos:=0.0

roslaunch sma_multiturtle turtle_multiple.launch multi_robot_name:=tb3_2 x_pos:=0.0 y_pos:=-2.0

rosrun sma_multiturtle inter_leader_follower.py tb3_0 tb3_1

rosrun sma_multiturtle inter_leader_follower.py tb3_1 tb3_2

ROS_NAMESPACE=tb3_0 rosrun turtlebot3_teleop turtlebot3_teleop_key


