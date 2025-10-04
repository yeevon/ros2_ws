# SETUP INSTRUCTIONS

## 1)  Create a GZ_SIM_SYSTEM_PLUGIN_PATH system variable

### This will enable the use of our physics plugins.

Open the .bashrc file again by typing the following into your terminal from your home directory:

```console
sudo gedit .bashrc
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
sudo gedit .bashrc
```

Now paste the following at the end of the .bashrc file:
```console
export GZ_SIM_RESOURCE_PATH=$GZ_SIM_RESOURCE_PATH:~/ros2_ws/src/my_gz_worlds/worlds:~/ros2_ws/src/my_gz_worlds/models
```

Save changes to the .bashrc file and close the editor.

Now the following code:

```console
<include>
  <name>water_tower</name>
  <uri>model://water_tower/model.sdf</uri>
  <pose>0 0 0 0 0 0</pose>
</include>
```

in your SDF world file will load the water_towel model from the /models directory into your world.

## 3) Make sure that the following line is included in your .bashrc file:

```console
source /opt/ros/jazzy/setup.bash
```


# Important Commands

### Reload the Shell:

```console
source ~/.bashrc
```

### Source your environment:

```console
source /opt/ros/jazzy/setup.bash
```


## Sources:

All downloaded objects were created by OpenRobotics and downloaded from <a href="https://app.gazebosim.org/OpenRobotics" target="_blank">https://app.gazebosim.org/OpenRobotics</a>
