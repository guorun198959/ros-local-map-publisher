# ros-local-map-builder

## Overview
![](https://github.com/msc9533/ros-local-map-publisher/blob/master/doc/capture_rviz.png?raw=true)

[costmap_2d](http://wiki.ros.org/costmap_2d)와 비슷한 기능을 하는 패키지 입니다. ros tf tranform을 이용한 global map에서 base_link frame의 local map을 추출하는 기능을 제공합니다. 
하지만 `costmap_2d` 패키지와 달리 `odom`을 이용한 방식을 제공합니다. 이 방식은 `tf`와 달리 시간에 대한 제약을 받지 않습니다.  

## Installation

### Dependency Installation
```
sudo apt-get install ros-kinetic-map-server ros-kinetic-nav-msgs ros-kinetic-geometry-msgs
```

### Installation to your Workspace

```
cd {your work space}
git clone https://github.com/msc9533/ros-local-map-publisher.git
catkin_make
```

## Usage

```
roslaunch roslaunch local_map_builder test.launch
```

## Configuration

```
source_frame: "/map"
child_frame: "/base_link"
map_topic: "/map"
method: "odom" # tf or odom only
odom_topic: "/odom"
cost_map: true
pointcloud_topic: "/pcl"
global_map_static: true
map_size: [5.0, 5.0] #x,y (meter)
tolerance: 0.3 #tf 방식을 이용할때 설정하는 시간오차입니다.
```

### Configuration of `tf` Method

tf 방법을 사용할때는 다음과 같이 설정되어 있는것을 확인하여야 합니다.

