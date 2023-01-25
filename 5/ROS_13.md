ROS_13
======

# 5. 2D 라이다
## 2D 라이다를 이용한 장애물 회피

LaserScan: ROS에서 2D 라이다의 측정 결과를 발행하는 토픽 자료형. LaserScan 자료형은 여러 개의 데이터로 구성되어 있음.    
float32[] ranges 배열 데이터를 이용. 각 각도에 대해 장애물까지의 거리가 저장되어있음.   
터틀봇의 라이다는 정면 0도를 기준으로 360도 전방위에 대해 1도 간격으로 거리를 측정. 그러므로 터틀봇이 발행하는 메세지의 ranges 배열은     
ranges[0] = 0도에서 측정한 거리. ranges[1] = 1도에서 측정한 거리. ranges[2] = 2도에서 측정한 거리. ranges[3] = 3도에서 측정한 거리.... 
원하는 각도에 있는 장애물까지의 거리를 알 수 있음.

터틀봇의 라이다에서 발행한 토픽. 터틀봇의 라이다에서는 LaserScan 메세지 자료형의 토픽을 Scan이라는 이름으로 발행. 그러므로 토픽을 구독하기 위해서는 다음과 같이 선언.

```
#include "ros/ros.h"
#include "geometry_msgs/Twist.h"
#include "sensor_msgs/LaserScan.h"

Float range_ahead;
#main에서 이용하기 위해 외부 변수로 선언.
#이렇게 하면 Scan 토픽이 수신될 때마다 정면 0도 방향의 거리가 range_ahead에 저장. 그 값이 출력.

void scan_cb(const sensor_msgs::LaserScan::ConstPtr& msg) {
  range_ahead = msg->ranges[0];
  #정면 0도 각도 방향의 장애물까지의 거리를 range_ahead에 저장 변수에 저장.  
  printf("range ahead: %f\n", range_ahead);
}

int main(int argc, char**argv) {
  ros::init(argc, argv, "go_scan");
  ros::NodeHandle n;
  ros::Publisher  cmd_pub = n.advertise<geometry_msgs::Twist>("cmd_vel",1);
  ros::Subscriber scan_pub = n.subscribe<sensor_msgs::LaserScan>("scan", 1, scan_cb);
  #토픽 구독. 자료형은 LaserScan, 토픽 이름 scan, 콜백함수 scan_cb.  
  ros::Rate loop_rate(10);
  geometry_msgs::Twist cmd;
}
```

main 함수에서는 이렇게 측정한 거리에 따라 적절히 터틀봇을 조종할 수 있음.

```
ros::Rate loop_rate(10);
  geometry_msgs::Twist  cmd;

  while(ros::ok()) {
    if(range_ahead < 0.8) {
    cmd.linear.x = 0;
    cmd.angular.z = 0.2;
    } else {
        cmd.linear.x = 0.2;
        cmd.angular.z = 0;
    }
    cmd_pub.publish(cmd);
    ros::spinOnce();
    loop_rate.sleep();
  }
  
  return 0;
}
```
    
  
