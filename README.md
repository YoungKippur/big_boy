## big_boy
Ros2 Humble - RPLidar A1 - Raspberry Pi 4 - Old hoverboard
### Run simulation
```
ros2 launch big_boy launch_sim.launch.py world:=./src/big_boy/worlds/obstacles.world
``` 
```
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped
```
> **If you are not using ros2 control on the simulation, should run this instead** \
> ``` ros2 run teleop_twist_keyboard teleop_twist_keyboard```
## Packages
* [rplidar_ros](https://github.com/Slamtec/rplidar_ros/tree/dev-ros2)
* [hoverboard_driver](https://github.com/hoverboard-robotics/hoverboard-driver/tree/humble)