### ROS Melodic 간단 설치

- OS Version : Ubuntu 18.04 (LTS)


1. 아래 명령어를 입력해서 스크립트 파일을 다운로드 받는다.

```
wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh
```

2. 아래 명령어를 입력해서 실행권한을 설정한다.

```
chmod 755 ./install_ros_melodic.sh
```

3. 아래 명령어를 입력해서 스크립트 파일을 실행한다.

```
bash ./install_ros_melodic.sh
```

4. 설치가 완료되면, ROS 환경설정까지 자동으로 끝난 상태이다. 터미널을 종료한다.

5. 새로운 터미널에서 아래 명령어를 입력해서 ROS가 제대로 설치되었는지 테스트한다.

```
roscore
```

```
... logging to /home/ubuntu/.ros/log/447217be-44d0-11e9-bda2-f82819ab5faf/roslaunch-ubuntu-15ZD970-18155.log
Checking log directory for disk usage. This may take awhile.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.

started roslaunch server http://localhost:37081/
ros_comm version 1.14.3


SUMMARY
========

PARAMETERS
 * /rosdistro: melodic
 * /rosversion: 1.14.3

NODES

auto-starting new master
process[master]: started with pid [18165]
ROS_MASTER_URI=http://localhost:11311/

setting /run_id to 447217be-44d0-11e9-bda2-f82819ab5faf
process[rosout-1]: started with pid [18176]
started core service [/rosout]

```

6. 위에 처럼 출력되면 설치가 완료된 것이다. 종료는 `Ctrl+C`이다.
