ROS_14
======

# 5. 2D 라이다
## 2D 라이다를 이용한 장애물 회피(2)


작업공간으로 이동한 후에 전에 만들었던 wanderbot 패키지로 이동하여 프로그램 컴파일.
```
cd ~/my_ws
cd src/wanderbot/src/
gedit go_scan.cpp
```

```
cd ../
gedit CMakeLists.txt

txt에서 추가.
add_executable(go_scan src/go_scan.cpp)
target_link_libraries(go_scan ${catkin_LIBRARIES})
```

다음으로 작업공간에서 catkin_make 실행 및 환경설정.
```
catkin_make
source devel/setup.bash
```

새로운 터미널 창. 작업공간 이동.
```
cd ~/my_ws
source devel/setup.bash
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

이전 터미널 창에서 노드를 실행.
```
rosrun wanderbot go_scan
```


<p align="left"><img src = "../images/turtlebot_error.png" width = "400"  title = "turtlebot_error"></p>
위와 같이 걸림 발생. 따라서 더 이상 진행 불가. 이러한 에러는 전방 0도만 확인하기 때문.

앞에 있는 장애물은 인지 가능하지만, 조금 옆에 있는 장애물은 인지 불가. 이러한 에러를 해결하려면 충돌 예상 범위 안의 모든 방향에 대해 확인해야함.
범위를 그럼 어떻게 잡아야할까?  
너무 작게 잡으면 위와 같은 에러가 발생하고, 너무 넓게 잡으면 더 진행할 수 있음에도 접근하지 않음. 따라서, 적절한 범위를 계산하여 잡는 것이 해결 방법.
계산식 생략. 여유있게 양쪽 15도 총 30도 여유있게 범위 측정. 물론 움직임이 있는 장애물이 사각지대로 들어올 수 있지만 여기서는 생략.


코드 수정.



