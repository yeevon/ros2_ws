# SETUP INSTRUCTIONS

**Note:** If your **workspace directory is not called ros2_ws**, then **replace ros2_ws** with **the name of your workspace directory** throughout these code segments and commands. 

**Note:** A file called **_waterworld.sdf_** is referenced throughout this document.  If the world that you are trying to open is not named **_waterworld.sdf_**, then replace **_waterworld.sdf_** with **the name of your world file** when entering these commands.

git clone https://github.com/AEmilioDiStefano/ros2_ws.git


## 1)  Create a GZ_SIM_SYSTEM_PLUGIN_PATH system variable

### This will enable the use of our physics plugins.

Open the .bashrc file again by typing the following into your terminal from your home directory:

```console
sudo gedit ~/.bashrc
```

Now paste the following at the end of the .bashrc file:
```console
export GZ_SIM_SYSTEM_PLUGIN_PATH="/opt/ros/jazzy/lib:${GZ_SIM_SYSTEM_PLUGIN_PATH}"
```

Save changes to the .bashrc file and close the editor.


## 2) Create a GZ_SIM_RESOURCE_PATH system variable

### This will allow you to reference models in your /models directory via a <uri></uri> in our SDF world files.  


Open your .bashrc file by typing the following into your terminal from your home directory:

```console
sudo gedit ~/.bashrc
```

Now paste the following at the end of the .bashrc file:
```console
export GZ_SIM_RESOURCE_PATH=$HOME/ros2_ws/src/my_robot_bringup/models:$GZ_SIM_RESOURCE_PATH
```

Save changes to the .bashrc file and close the editor.

Now the depicted below:

```console
<include>
  <name>water_tower</name>
  <uri>model://water_tower/model.sdf</uri>
  <pose>0 0 0 0 0 0</pose>
</include>
```

in your SDF world file will load the water_towel model from the /models directory into your world.

## 3) Make sure that the following lines are included in your .bashrc file:

```console
source /opt/ros/jazzy/setup.bash
```

```console
source ~/ros2_ws/install/setup.bash
```

```console
export GZ_SIM_SYSTEM_PLUGIN_PATH="/opt/ros/jazzy/lib:${GZ_SIM_SYSTEM_PLUGIN_PATH}"
```

```console
export GZ_SIM_RESOURCE_PATH=$HOME/ros2_ws/src/my_robot_bringup/models:$GZ_SIM_RESOURCE_PATH
```

# Important Commands

## Reload the Shell:

```console
source ~/.bashrc
```

## Build and Execute Your Environment:

**Build:**
```console
colcon build
```

**Execute:**
```console
source ~/ros2_ws/install/setup.bash
```

## Run a control node to control a robot:
```console
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
**Note:** In order to control the robot, **the terminal window running the teleop control node must be selected** rather than the Gazebo simulation window.


# Common Issues

## If Gazebo doesn't open when attempting to open a world from __my_robot_gazebo.launch.xml__:

Try opening your world from ROS2 in only Gazebo.

```console
gz sim "$(ros2 pkg prefix my_robot_bringup)/share/my_robot_bringup/worlds/waterworld.sdf" -v4
```

**If it doesn't open**, then build and source your environment again:

**Build:**
```console
colcon build
```

**Execute:**
```console
source ~/ros2_ws/install/setup.bash
```

**Now try launching again:**

```console
ros2 launch my_robot_bringup my_robot_gazebo.launch.xml
```


**Note:** A file called **_waterworld.sdf_** is referenced in the above commands.  If the world that you are trying to open is not named **_waterworld.sdf_**, then replace **_waterworld.sdf_** with **the name of youe world file** when entering these commands.

## If Gazebo opens but does not load your robot:

**Open** your **__my_robot_descrioption__* directory and **open** the document called **__CMakeLists.txt__**

**Make sure** that under the **__install (__** line of the **__CMakeLists.txt__** document, you see **the names of each directory** in the **__my_robot_descrioption__** directory.  If each directory name is not listed, **add it.** 


## Sources:

All downloaded objects were created by OpenRobotics and downloaded from <a href="https://app.gazebosim.org/OpenRobotics" target="_blank">https://app.gazebosim.org/OpenRobotics</a>
