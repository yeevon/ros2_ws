# URDF-Demo
Demo of URDF, Gazebo, RVIZ and Keyboard Teleop Application


-- ~/.bashrc file requirements to source

source /opt/ros/jazzy/setup.bash


source ~/ros2_ws/install/setup.bash


export GZ_SIM_SYSTEM_PLUGIN_PATH="/opt/ros/jazzy/lib:${GZ_SIM_SYSTEM_PLUGIN_PATH}"


export GZ_SIM_RESOURCE_PATH=$HOME/ros2_ws/src/my_robot_bringup/models:$GZ_SIM_RESOURCE_PATH




-- Launch Gazebo and URDF

ros2 launch my_robot_bringup my_robot_gazebo.launch.xml 


-- Launch Keyboard Teleoperation Package

ros2 run teleop_twist_keyboard teleop_twist_keyboard
