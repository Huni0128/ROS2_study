# ROS2 입문 실습

## turtlesim install
```
sudo apt install ros-jazzy-turtlesim
```

## turtlesim Node 실행 결과

### ROS 2 Node 정보 조회 예제 (`ros2 node info`)
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

### ROS 2 Service 정보 조회 예제 (`ros2 service info`)
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



