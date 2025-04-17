# ROS2 입문 실습

## turtlesim install
```
sudo apt install ros-jazzy-turtlesim
```

## turtlesim Node 실행 결과

### ROS2 Node 정보 조회 예제 (`ros2 node info`)
```
ros2 node list
ros2 node info /turtlesim
```
![Turtlesim node 실행 예시](images/ros2_node_info.png)

### 1_Terminal
```
ros2 run turtlesim turtlesim_node
```

### 2_Terminal
```
ros2 node list
```
![Turtlesim node 실행 예시](images/run_turtle_and_node_list.png)

## Turtlesim Service 실행 결과

### ROS2 Service 정보 조회 예제 (`ros2 service info`)
```
ros2 service list
ros2 service type /turtle1/teleport_absolute
```
![Turtlesim node 실행 예시](images/ros2_service_info.png)

### ROS2 인터페이스 구조 확인 (`interface show`)
```
ros2 interface show turtlesim/srv/TeleportAbsolute
```
![Turtlesim service 실행 예시](images/ros2_service_interface.png)

### turtle2 생성: spawn 서비스 호출 예제 (`ros service spawn`)
```
ros2 service call /spawn turtlesim/srv/Spawn "{x: 1,y: 1,theta: 0, name: ''}"
```
![Turtlesim service 실행 예시](images/ros2_service_spawn.png)

### 1_Terminal
```
ros2 run turtlesim turtlesim_node
```
### 2_Terminal
```
ros2 service call /turtle1/teleport_absolute turtlesim/srv/TeleportAbsolute "{x: 2,y: 2,theta: 1.57}"
```
![Turtlesim service 실행 예시](images/ros2_service_call.png)

### ROS2 topic 및 interface 명령어 실습
```
ros2 topic list
ros2 topic type /turtle1/pose
ros2 topic list -t
ros2 topic info /turtle1/pose
ros2 topic list -v
ros2 interface show turtlesim/msg/Pose
```
![Turtlesim service 실행 예시](images/ros2_topic_debug.png)

### 토픽 메시지 실시간 출력 (`topic echo`)
```
ros2 topic echo /turtle1/pose
```
![Turtlesim service 실행 예시](images/ros2_topic_echo.png)

### ROS2 Twist 메시지 구조
```
ros2 interface show geometry_msgs/msg/Twist
```
![Turtlesim service 실행 예시](images/ros2_topic_twist.png)

#### Turtlesim 토픽 명령어 실행 결과
```
ros2 topic pub --once /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0,y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 0.0}}"
ros2 topic pub --once /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0,y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 1.8}}"
ros2 topic pub --rate 1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0,y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 1.8}}"
```
![Turtlesim service 실행 예시](videos/ros2_twist_publish_example.webm)

