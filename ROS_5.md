
ROS_5
=====

이번에는 이전 챕터에서 노드에서 발행하고 있는 토픽을 수신한 다음 출력하는 노드를 만들어보자.

```
#include "ros/ros.h"
#include "std_msgs/Int32.h"

# 콜백 함수(토픽을 받았을 때 실행되는 함수) 이름 cb. 토픽 메시지 자료형(std_msgs), 포인터(ConstPtr&), 토픽으로 수신하는 메시지 msg
void cd(const std_msgs::Int32::ConstPtr& msg) {
              printf("%d\n", msg->data);
}

int main(int argc, char **argv) {
              ros::init(argc, argv, "topic_sub");
              # 노드 선언 및 노드 이름.
              ros::NodeHandle n;
              # 노드 핸들러 선언.
              ros::Subscriber sub = n.subscribe("counter ", 1000, cb);
              # 토픽을 구독하는 변수로 정의. (advertise 대신 subscribe를 이용해서 토픽을 구독함을 주변에 알림. counter : 토픽의 이름. cb : 콜백함수.)
              # 콜백 함수 : 토픽을 받았을 때 받은 데이터로 여러가지 작업을 실시해야함 그 작업의 내용을 기술해 놓은 것이 콜백 함수.
              ros::spin();
              # 무한 반복하다 토픽을 받으면 콜백 함수 실행.
}
              
              
              
