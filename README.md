# gazebo_sensor_ros2
Sensor simulation using Gazebo of ROS2

## Environment
- Ubuntu 22.04 (on WSL2)
- ROS Humble

## RealSense
Below page is also the article about this RealSense on Gazebo in Japanese.
https://qiita.com/koichi_baseball/items/212768586c6b5f20e078

### Demo

https://user-images.githubusercontent.com/46204057/219066966-ca2c2bda-f469-4ff6-b8bf-15b7ec0a832f.mp4

### Dependicies
 - librealsense
 - [realsense-ros](https://github.com/IntelRealSense/realsense-ros.git)
 - [realsense_gazebo_plugin](https://github.com/pal-robotics/realsense_gazebo_plugin.git)

#### librealsense
```
sudo apt-get install ros-$ROS_DISTRO-realsense2-camera
```

#### realsense-ros and realsense_gazebo_plugin
```
cd ~/ros2_ws/src
git clone https://github.com/IntelRealSense/realsense-ros.git -b ros2-development
git clone https://github.com/pal-robotics/realsense_gazebo_plugin.git -b foxy-devel
cd ~/ros2_ws
colcon build --symlink-install
source install/setup.bash
```

### Usage
#### git clone and colcon build
```
cd ~/ros2_ws/src
git clone https://github.com/koichirokato/gazebo_sensor_ros2
cd ~/ros2_ws
colcon build --symlink-install
source install/setup.bash
```

#### Set Environment value
Run the following command to load the RealSense model file.
(It will work without running it, but the model will not appear on Gazebo.)

```
export GAZEBO_MODEL_PATH=~/ros2_ws/install/realsense2_description/share/realsense2_description/meshes/:$GAZEBO_MODEL_PATH
```

#### Launch ROS node
##### Gazebo

```
ros2 launch gazebo_sensor_ros2 realsense_gazebo.launch.py
```

##### Rviz
```
rviz2 -d ~/ros2_ws/src/gazebo_sensor_ros2/rviz/config.rviz
```

