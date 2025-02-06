# Exploration-PX4-Gazebo

Run [FUEL](https://github.com/HKUST-Aerial-Robotics/FUEL) and [FALCON](https://github.com/HKUST-Aerial-Robotics/FALCON) in Gazebo, PX4 SITL

## Build and Run

```
mkdir -p explore_ws/src
cd explore_ws/src
git clone git@github.com:ChanJoon/Exploration-PX4-Gazebo.git
cd ..
catkin_make
```

### FUEL
```
roslaunch fuel_exploration_manager rviz.launch
roslaunch fuel_exploration_manager exploration.launch
```

### FALCON
```
roslaunch falcon_exploration_manager rviz.launch
roslaunch falcon_exploration_manager exploration.launch
```