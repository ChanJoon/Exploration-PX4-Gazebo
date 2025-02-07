# Exploration-PX4-Gazebo

Run [FUEL](https://github.com/HKUST-Aerial-Robotics/FUEL) and [FALCON](https://github.com/HKUST-Aerial-Robotics/FALCON) in Gazebo, PX4 SITL

## Build and Run

#### Install dependencies

Follow [FUEL](https://github.com/HKUST-Aerial-Robotics/FUEL) and [FALCON](https://github.com/HKUST-Aerial-Robotics/FALCON) README.md

#### Build

```bash
mkdir -p explore_ws/src
cd explore_ws/src
git clone git@github.com:ChanJoon/Exploration-PX4-Gazebo.git --recursive
cd ..
catkin_make
```

#### Run original examples

**FUEL**
```bash
roslaunch fuel_exploration_manager rviz.launch
roslaunch fuel_exploration_manager exploration.launch
```

**FALCON**
```bash
roslaunch falcon_exploration_manager rviz.launch
roslaunch falcon_exploration_manager exploration.launch
```

#### Run algorithms with PX4 SITL

1. Add Gazebo models
```bash
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:~/explore_ws/src/Exploration-PX4-Gazebo/FUEL/fuel_planner/exploration_manager/models
```
Also, you need to export models in your custom world file.

2. Run

**FUEL**

```bash
roslaunch fuel_exploration_manager px4_sitl_gazebo.launch
roslaunch fuel_exploration_manager rviz.launch
roslaunch fuel_exploration_manager exploration_px4.launch
roslaunch px4ctrl px4_ctrl.launch
```

**FALCON**

Before runnign FALCON, turn `auto_start` to `false` in `FALCON/falcon_planner/exploration_manager/config/exploration_manager.yaml`
```bash
roslaunch fuel_exploration_manager px4_sitl_gazebo.launch
roslaunch falcon_exploration_manager rviz.launch
roslaunch falcon_exploration_manager exploration_px4.launch
roslaunch px4ctrl px4_ctrl.launch
```