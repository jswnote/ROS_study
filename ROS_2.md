ROS setup
=========

1. Parallels 설치
2. Parallels 설치 후 linux ubuntu 설치 이미지 파일 다운로드
  - 여기서 parallels에서는 ARM 파일을 받아야 가능.(AMD는 설치 안됨)
  - ubuntu 20.04.5 LTS 다운함. 
  - ARM 설치 link <https://cdimage.ubuntu.com/focal/daily-live/current/>.  
  
  parallels ubuntu 20.04.5 LTS 설치
  <p align="left"><img src = "../images/2022-12-30-ROS_2/parallels_setup.png" width = "400"  title = "parallels_setup"></p>
  ubuntu 설치 확인
  <p align="left"><img src = "../images/2022-12-30-ROS_2/linux_version.png" width = "400"  title = "linux_version"></p>
  
3. ROS 설치
  - ROS noetic 버전 설치
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update 
#여기까지가 설치를 준비하는 과정

sudo apt install ros-noetic-desktop-full
#ros 설치 부분, full = 전체 설치

echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
#환경설정 ubuntu에서 ros의 명령어가 실행이 원할하게 해주는 부분

sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
#ros와 파이썬이 연동되도록 하는 부분.

sudo rosdep init
rosdep update
```
  - ROS noetic link <http://wiki.ros.org/noetic/Installation/Ubuntu>
  
  ROS noetic 버전 확인
  <p align="left"><img src = "../images/2022-12-30-ROS_2/ros_version.png" width = "400"  title = "ros_version"></p>
  
