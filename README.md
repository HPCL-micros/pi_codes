### 为了正确配置ROS的分布式环境，并使用ros remote launch，需要以下配置：
(以uav0为例进行说明，uav0 IP 地址为192.168.21.100)

#### 在.bashrc文件中添加如下内容：
```
export ROS_MASTER_URI=http://192.168.21.200:11311
export ROS_HOSTNAME=192.168.21.100
export ROSLAUNCH_SSH_UNKNOWN=1
```

#### 在/home/pi/catkin_ws/目录下新建env.sh脚本文件，并添加如下内容:
```
# !/bin/bash
. /home/pi/catkin_ws/devel/setup.sh
source /opt/ros/kinetic/setup.bash
source ~/catkin_ws/devel/setup.bash
export ROS_HOSTNAME="192.168.21.100"
exec "$@"
```
#### 使用chmod为env.sh添加执行权限
```
chmod +x /home/pi/catkin_ws/env.sh
```
