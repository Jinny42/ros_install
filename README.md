### ROS Kinetic 간단 설치

- OS Version : Ubuntu 16.04 (LTS, Xenial Xerus) [download](http://releases.ubuntu.com/16.04/)


1. 아래 명령어를 입력해서 스크립트 파일을 다운로드 받는다.

```
wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh
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


---

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

---

**여기서부터는 위에 설치한 내용에 대한 설명이다.**

### 적용된 ROS 환경설정

`/.bashrc` 맨 아래에 아래와 같은 내용을 추가했다.

```
# Set ROS Melodic
source /opt/ros/melodic/setup.bash
source ~/catkin_ws/devel/setup.bash

# Set ROS Network
export ROS_MASTER_URI=http://localhost:11311
export ROS_HOSTNAME=localhost

# Set ROS alias command
alias cw='cd ~/catkin_ws'
alias cs='cd ~/catkin_ws/src'
alias cm='cd ~/catkin_ws && catkin_make'
```

**설명**

```
# Set ROS Melodic
source /opt/ros/melodic/setup.bash
source ~/catkin_ws/devel/setup.bash
```

위에 코드는 ROS 환경설정 불러오기를 의미한다.
'#'은 주석문의 시작을 알리는 문법이고 그 뒤의 내용이 주석문이다.
그리고 2번째 줄과 3번째 줄은 반드시 설정해야할 ROS 환경설정이다.

---

```
# Set ROS Network
export ROS_MASTER_URI=http://localhost:11311
export ROS_HOSTNAME=localhost
```

위에 코드는 ROS 네트워크 설정을 의미한다.
ROS_MASTER_URI와 ROS_HOSTNAME의 설정이다.
ROS는 네트워크를 이용해 노드 간에 메시지 통신을 하기 때문에 이 설정은 매우 중요하다.
우선은 둘 다 자신의 네트워크 IP를 입력해주면 된다.
차후에 마스터 PC가 따로 있고, 로봇은 호스트 PC를 사용하는 경우, 이를 구분하여 입력하면 서로 다른 컴퓨터 간의 통신이 가능하게 된다.
지금은 둘 다 자신의 네트워크 IP를 입력한다.
추가적으로 자신의 IP 정보는 터미널 창에서 ifconfig 명령어로 확인할 수 있다.
(ifconfig는 리눅스에서 자신의 Ip를 확인하기 위해 사용한다. 유선일 때 enp3s0, 무선일 때 wlp2s0의 inet addr에 자신의 ip가 표시된다.)

---

```
# Set ROS alias command
alias cw='cd ~/catkin_ws'
alias cs='cd ~/catkin_ws/src'
alias cm='cd ~/catkin_ws && catkin_make'
```

위 코드는 단축 명령어를 설정을 의미한다.
리눅스에서 단축 명령어는 `alias`를 이용해서 만든다.
`cw`는 미리 설정해 둔 catkin 작업 폴더인 `~/catkin_ws`로 이동
`cs`는 catkin 작업 폴더 중 소스 파일이 있는 `~/catkin_ws/src`로 이동
`cm`은 catkin 작업 폴더인 `~/catkin_ws`로 이동한 후,`catkin_make` 명령어로 ROS 패키지를 빌드

** ROS 환경설정 확인 방법**
`export|grep ROS` 명령어를 이용해 아래처럼 자신의 ROS 환경설정을 확인할 수 있다.

```
declare -x ROSLISP_PACKAGE_DIRECTORIES="/home/ubuntu/catkin_ws/devel/share/common-lisp"
declare -x ROS_DISTRO="melodic"
declare -x ROS_ETC_DIR="/opt/ros/melodic/etc/ros"
declare -x ROS_HOSTNAME="localhost"
declare -x ROS_MASTER_URI="http://localhost:11311"
declare -x ROS_PACKAGE_PATH="/home/ubuntu/catkin_ws/src:/opt/ros/melodic/share"
declare -x ROS_PYTHON_VERSION="2"
declare -x ROS_ROOT="/opt/ros/melodic/share/ros"
declare -x ROS_VERSION="1"
```

---

### 통합 개발환경(IDE)

업데이트 중...

