##Le package sma_join-train permet de simulter l'action d'un turtleBot3 qui en croisant le chemin d'un fil de robot, les rejoint dans le fil.
#Pour executer la simulation lancer les commandes suivantes:

cd catkin_ws/src
cd ..
catkin_make

roslaunch sma_join-train launch_gazebo.launch

rosrun map_server map_server ~/map.yaml

roslaunch sma_join_train turtle_multiple.launch multi_robot_name:=tb3_0 x_pos:=-2.0 y_pos:=1.0

roslaunch sma_join-train turtle_multiple.launch multi_robot_name:=tb3_1 x_pos:=-2.0 y_pos:=0.0

roslaunch sma_join-train turtle_multiple.launch multi_robot_name:=tb3_2 x_pos:=-2.0 y_pos:=-1.0

#lancer le leader follower

rosrun sma_join-train inter_leader_follower.py tb3_0 tb3_1

rosrun sma_join-train inter_leader_follower.py tb3_1 tb3_2


#lancer le teletop

ROS_NAMESPACE=tb3_0 rosrun turtlebot3_teleop turtlebot3_teleop_key

#lancer le join train

roslaunch sma_join-train launch_gazebo.launch

rosrun map_server map_server ~/map.yaml

roslaunch sma_join-train turtle_multiple.launch multi_robot_name:=tb3_0 x_pos:=0.0 y_pos:=2.0

roslaunch sma_join-train turtle_multiple.launch multi_robot_name:=tb3_1 x_pos:=-2.0 y_pos:=0.0

roslaunch sma_join-train turtle_multiple.launch multi_robot_name:=tb3_2 x_pos:=0.0 y_pos:=-2.0

rosrun sma_join-train inter_leader_follower.py tb3_0 tb3_1

rosrun sma_join-train inter_leader_follower.py tb3_1 tb3_2

ROS_NAMESPACE=tb3_0 rosrun turtlebot3_teleop turtlebot3_teleop_key


