ROS_7 - 토픽 구독 노드 실행
=======================
roscore 실행.  
```
roscore
```

작업공간 이동.  
```
cd ~/my_ws
```

환경설정(setup.bash).  
```
source devel/setup.bash
```

토픽 발행 노드 실행(rosrun) - 패키지 이름(topic_ex) - 실행파일 이름(topic_publisher).  
```
rosrun topic_ex topic_publisher
```

새로운 터미널에서 작업공간 src 디렉토리 아래의 패키지 디렉토링 아래의 src 디렉토리로 이동. 
```
cd ~/my_ws/src/topic_ex/src/
```

gedit를 이용하여 topic_subscriber.cpp라는 소스코드를 작성. 
```
gedit topic_subscriber.cpp
```

하나 위 디렉토리로 이동한 후 CMakeLists.txt 수정. 
```
cd ../
gedit CMakeLists.txt
```

소스파일, 실행파일 기술, 링크 라이브러리 기술. 
```
add_executable(topic_subscriber src/topic_subscriber.cpp)
target_link_libraries(topic_subscriber ${catkin_LIBRARIES})
```

작업공간 디렉토리로 이동, catkin_make 실행 후 컴파일 진행.  
```
cd ~/my_ws
catkin_make
```

환경 설정 후 토픽 구독 노드 실행. 
```
source devel/setup.bash
rosrun topic_ex topic_subscriber
```

토픽 발행 노드 0.5초당 1씩 증가. 
다른 터미널에서 토픽 구독 정보 확인. 
```
rosnode list
```

노드의 정보 확인. 
```
rosnode info [노드 이름]
```

현재 counter라는 토픽이 구독, 발행 확인.  최근 발행된 5개의 값을 확인 가능. 
```
rostopic echo counter -n 5
```
