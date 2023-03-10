ROS_9
=====
# 4. 로봇의 구동  
## 로봇의 속도.    

선형 속도 - 직선 운동. 3차원의 (x,y,z) 방향의 속도를 각각 고려함. 
<p align="center"><img src = "../images/linear.png" width = "400"  title = "linear"></p>

오른손을 폈을 때, 엄지를 제외한 나머지 손가락들이 가르키는 방향이 x, 엄지가 가르키는 방향이 z, 손바닥에서 나오는 방향이 y.
드론이 아닌 일반 자동차를 생각하면 자동차는 오로지 x축 방향으로만 이동이 가능하기 때문에 x축 방향만 고려하면 됨(좌회전, 우회전은 회전이지 y축 방향이 아님). 

각속도 - 회전 운동.
  - Roll : x축을 중심으로 회전. 옆구르기. 
  - Pitch : y축을 중심으로 회전. 앞구르기. 
  - Yaw : z축을 중심으로 회전. 좌회전, 우회전ㅇ 여기에 포함. 
  - 일반 자동차는 Roll, Pitch 고려 안함. 비행체는 의미 있음. 


일반적인 자동차의 경우 앞바퀴의 방향에 의해 회전하게 됨. 평소에는 두 개의 앞바퀴가 기울어지면 회전하게 됨(Car-like steering, Ackermann steering). 실내 로봇으 경우 양쪽 바퀴의 속도를 제어하여 회전하게 함. 예를 들어, 직진할 경우에는 양쪽 바퀴의 속도를 같게하고, 왼쪽으로 회전하고 싶은 경우 오른쪽 바퀴의 속도를 빠르게 회전시키고 왼쪽 바퀴의 속도를 상대적으로 느리게 회전시켜 로봇의 방향을 왼쪽을 제어함(Differential drive, 차동 구동 방식). 양쪽 바퀴의 방향을 반대로 하면 제자리 회전도 가능함. 


로봇에서 속도를 지정하려면 6가지 속도(선형 3, 각 3)를 지정해야 하는데 이 때 ROS에서 Twist 자료형을 많이 이용. 
Twist 자료형은 크게 Vector3 자료형의 두 변수 linear, angular 안의 x,y,z 값을 지정.
```
geometry_msgs::Twist msg;
msg.linear.x = 0.5;
msg.angular.z = 0.2;
```
msg 변수 생성. ROS에서 기본적인 단위는 meter, second와 rad.
초당 0.5m 직진, 초당 0.2rad(16초당 반 바퀴) 회전. 
