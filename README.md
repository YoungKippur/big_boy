## big_boy
Ros2 Humble - Ubuntu 22.04 (Jammy) - RPLidar A1 - Raspberry Pi 4 - Old hoverboard

### Run lidar
```bash
sudo chmod 777 /dev/serial/by-id/usb-Silicon_Labs_CP2102_USB_to_UART_Bridge_Controller_0001-if00-port0
``` 
```bash
ros2 launch big_boy rplidar.launch.py
```
### Run robot
```bash
sudo chmod 777 /dev/serial/by-id/usb-1a86_USB_Serial-if00-port0
``` 
```bash
ros2 launch big_boy launch_robot.launch.py
```
If you wanna drive it, use:
```bash 
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped
```
### Run simulation
```bash
ros2 launch big_boy launch_sim.launch.py world:=./src/big_boy/worlds/obstacles.world
```
```bash 
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped
```
> **Warning** \
> If you are not using ros2 control on the simulation, should run this instead \
> ```ros2 run teleop_twist_keyboard teleop_twist_keyboard```
### Slam Toolbox
## Run mapping or localization
```bash 
ros2 launch big_boy  online_async_launch.py use_sim_time:=true
```
## Run navigation
```bash 
ros2 launch big_boy navigation_launch.py use_sim_time:=true
```
### AMCL
## Run localization (Hard)
```bash 
ros2 run nav2_map_server map_server --ros-args -p yaml_filename:=my_map_save.yaml -p use_sim_time:=true
```
```bash 
ros2 run nav2_util lifecycle_bringup map_server
```
```bash 
ros2 run nav2_amcl amcl --ros-args -p use_sim_time:=true
```
## Run localization (Easy)
```bash 
ros2 launch big_boy localization_launch.py map:=./my_map_save.yaml use_sim_time:=true
```
## Run navigation
```bash 
ros2 launch big_boy navigation_launch.py use_sim_time:=true map_subscribe_transient_local:=true
```
### Packages
* [rplidar_ros](https://github.com/Slamtec/rplidar_ros/tree/dev-ros2)
* [hoverboard_driver](https://github.com/hoverboard-robotics/hoverboard-driver/tree/humble)
