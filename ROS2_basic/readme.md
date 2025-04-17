# ROS2 입문 실습

## Turtlesim install
```
sudo apt install ros-jazzy-turtlesim
```

## Turtlesim Node 실행 결과

### Node info 조회 예제
```
ros2 node list
ros2 node info /turtlesim
```
![Turtlesim Node 정보 조회 결과](images/ros2_node_info.png)

### 1_Terminal
```
ros2 run turtlesim turtlesim_node
```

### 2_Terminal
```
ros2 node list
```
![Turtlesim 실행 및 노드 리스트 확인](images/run_turtle_and_node_list.png)

## Turtlesim Service 실행 결과

### Service info 조회 예제
```
ros2 service list
ros2 service type /turtle1/teleport_absolute
```
![Turtlesim 서비스 리스트 및 타입 확인](images/ros2_service_info.png)

### Interface 구조 확인
```
ros2 interface show turtlesim/srv/TeleportAbsolute
```
![TeleportAbsolute 서비스 인터페이스 구조](images/ros2_service_interface.png)

### Turtle2 생성: spawn service 호출 예제
```
ros2 service call /spawn turtlesim/srv/Spawn "{x: 1,y: 1,theta: 0, name: ''}"
```
![Turtle2 생성 서비스 호출 예시](images/ros2_service_spawn.png)

### 1_Terminal
```
ros2 run turtlesim turtlesim_node
```
### 2_Terminal
```
ros2 service call /turtle1/teleport_absolute turtlesim/srv/TeleportAbsolute "{x: 2,y: 2,theta: 1.57}"
```
![Turtle1 위치 이동 서비스 호출 결과](images/ros2_service_call.png)

### Topic 및 interface 명령어 실습
```
ros2 topic list
ros2 topic type /turtle1/pose
ros2 topic list -t
ros2 topic info /turtle1/pose
ros2 topic list -v
ros2 interface show turtlesim/msg/Pose
```
![Turtlesim 토픽 리스트 및 인터페이스 확인](images/ros2_topic_debug.png)

### Topic message 실시간 출력
```
ros2 topic echo /turtle1/pose
```
![Turtlesim pose 토픽 실시간 출력](images/ros2_topic_echo.png)

### Twist message 구조
```
ros2 interface show geometry_msgs/msg/Twist
```
![Twist 메시지 구조 확인](images/ros2_topic_twist.png)

### Turtlesim topic 명령어 실행 결과
```
ros2 topic pub --once /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0,y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 0.0}}"
ros2 topic pub --once /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0,y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 1.8}}"
ros2 topic pub --rate 1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0,y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 1.8}}"
```
![Twist 퍼블리시를 통한 Turtlesim 동작 (GIF)](videos/ros2_twist_publish_example.gif)

### Turtlesim keyboard 제어 결과
```
ros2 run turtlesim turtle_teleop_key
```
![Turtlesim 키보드 제어 실행 영상 (GIF)](videos/ros2_action_key.gif) 
![RQT 그래프 상의 토픽 흐름 확인](images/ros2_action_key_result_rqt.png)

### Turtlesim 액션 명령어 실습
```
ros2 action list
ros2 action list -t
ros2 interface show turtlesim/action/RotateAbsolute
```
![RotateAbsolute 액션 구조 확인](images/ros2_action_interface.png)
