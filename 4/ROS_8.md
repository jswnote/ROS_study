ROS_8
=====
# 4. 로봇의 구동  
## ROS 메세지의 자료형. 

<p align="center"><img src = "./images/ros_msg.png" width = "800"  title = "ros_msg"></p>. 

signed : 정수형 변수 중 부호를 갖는 변수를 선언 (양수, 음수의 구분). 
unsigned : 음수를 사용하지 않는 변수. 
string : 문자열
time : 시작할 때부터 지금까지 흐른 시간을 표현.
duration : 두 time 자료형의 차이. 

ROS의 기본 자료형들은 std_msgs 패키지에 정의되어 있음. std_msgs에 포함되어 있는 자료형들을 확인하려면,
```
rosmsg package std_msgs
```
std_msgs 패키지에 포함된 자료형 표시. 


ROS에서는 기본 자료형 외에도 다양한 자료형들을 패키지로 제공하고 있음.
센서와 관련된 자료형들은 sensor_msgs 패키지에 포함.
```
rosmsg package sensor_msgs
```

<p align="center"><img src = "./images/sensor_msgs.png" width = "500"  title = "sensor_msgs"></p>.  

ROS에서 제공되는 자료형 외에 다른 자료형이 필요하면 사용자가 직접 자료형을 정의하여 사용 가능.  
기본 자료형이외의 다른 자료형들은 보통 기본 자료형 데이터를 묶어서 만들어짐. 
예를 들어, 로봇 동작에 관련된 자료형들이 주로 포함되어 있는 geometry_msgs(패키지)/Vector3.msg(자료형) 자료형의 경우 64비트 실수형 데이터 (x,y,z)가 묶어서 만들어져있음. c 언어 구조체와 비슷. 
이렇게 만들어진 자료형을 다시 여러개 사용해서 더 큰 단위의 자료형을 만들 수 있음. geometry_msgs의 Twist 자료형은 Vector3 자료형 두 개 (linear, angular)로 구성. 이렇게 다른 자료형 데이터를 묶어서 만들어진 자료형은 c 언어의 구조체처럼 사용. 
```
geometry_msgs::Twist  msgs;
msg.linear.x = 0.5;
msg.angular.z = 0.2;
```
