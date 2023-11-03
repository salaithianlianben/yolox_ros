# ROS2 + YOLOX + Python

In this project, I am going to use ROS2 foxy and the OS is ubunutu 20.04.
So you can read and follow each step on this doc https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html

### Setup
- Step 1 Create ROS workspace 
```bash
mkdir ros_ws
cd ros_ws
mkdir src
cd src
git clone https://github.com/salaithianlianben/yolox_ros.git
```

In the above installation requirements packages, there may be error on yolox. You can remove it. Run it again. 


- Step 2 Packages installation for the project
```bash
cd ros_ws/src/yolox_ros
python3 -m pip install -r requirements
cd yolox_ros
python3 setup.py develop
```

- Step 3 Launch the websocket server for intercommunication between two machines
```bash
cd ros_ws/src
git clone https://github.com/RobotWebTools/rosbridge_suite
cd ..

source /opt/ros/foxy/setup.bash

colcon build --symlink-install

source install/local_setup.bash
ros2 launch rosbridge_server rosbridge_websocket_launch.xml
```

There is error "Module Not found "bson"

```bash
python3 -m pip install pymongo tornado
```
Run it again 
```bash
ros2 launch rosbridge_server rosbridge_websocket_launch.xml
```

- Step 4 Open new terminal and Start webcame and scan the objects
```bash
cd ros_ws
source /opt/ros/foxy/setup.bash
colcon build --symlink-install

source ~/ros_ws/install/setup.bash
ros2 launch yolox_ros_py yolox_nano_torch_gpu_camera.launch.py
# ros2 launch yolox_ros_py yolox_nano_torch_gpu_camera.launch.py
```

