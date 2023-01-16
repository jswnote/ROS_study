ROS_10
======

# 4. 로봇의 구동
## TurtleBot 패키지 설치. 
### Noetic ver.


Install Dependent ROS Packages. 
```
sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
```

Install TurtleBot3 Packages.  
```
sudo apt install ros-noetic-dynamixel-sdk
sudo apt install ros-noetic-turtlebot3-msgs
sudo apt install ros-noetic-turtlebot3
```

TurtleBot model. 
```
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```

설정 적용. 
```
source ~/.bashrc
```

작업공간안에 TurtleBot 시뮬레이션을 위한 패키지를 설치. 
```
cd ~/my_ws/src
git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git
git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations
cd ../
catkin_make
```

시뮬레이션 환경 실행. 
```
source devel/setup.bash
roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```


