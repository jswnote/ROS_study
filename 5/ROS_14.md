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


