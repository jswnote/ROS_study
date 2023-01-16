ROS_11
======

# 4. 로봇의 구동. 
## 로봇의 구동. 

turtlebot을 움직이려면 어떻게 움직일지에 대한 정보를 토픽으로 발행해야함.
```
#include "ros/ros.h"
#include "geometry_msgs/Twist.h"

int main(int argc, char **argv) {
	ros::init(argc, argv, "go_rot");
	ros::NodeHandle n;
	ros::Publisher	pub = n.advertise<geometry_msgs::Twist>("cmd_vel", 1);
	
	ros::Rate	loop_rate(10);
	geometry_msgs::Twist	cmd;
	cmd.linear.x = 0.5;
	
	while(ros::ok()) {
		pub.publish(cmd);
		ros::spinOnce();
		loop_rate.sleep();
	}
	
	return 0;
```
cmd_vel : 토픽의 이름.
geometry_msgs : Twist 자료형. 
