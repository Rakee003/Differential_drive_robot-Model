# Differential_drive_robot-Model
Creating a Simple Two Wheeled Mobile Robot using the Primitive shapes in URDF .
![differentila_drive_robot_model](https://user-images.githubusercontent.com/58605350/126116971-699ff335-a09f-457b-bcd6-dd0d1e160d72.png)

## Packages

* differential_drive_robot_description
* differential_drive_robot_gazebo
* differential_drive_robot_control

## Dependencies
* geometry_msgs
* rospy
* std_msgs

## Package Explanation :
### differential_drive_robot_description:
This package contains the urdf description of the robot which is used to do all kinds of simulation works.
### differential_drive_robot_gazebo :
This package is used to deploy the robot model into the gazebo simulation world.
### differential_drive_robot_control:
As the name suggests this package is used to control the motion of the robot. Alternatively we can also use rqt robot steering for motion control.


## How to launch the robot ?
Create a workspace for example <b>catkin_ws</b> and paste all the three packages in the <b>src</b> folder
> Run the command in terminal
```sh
catkin_make
```

The Robot model is designed using various xacro files found at ~catkin_ws/src/differential_drive_robot_description/urdf :
* <b>differential_drive_robot.xacro </b>- Main Robot description
* <b>differentila_drive_robot.gazebo </b>- Gazebo description
* <b>xacro_variables.xacro </b>- xacro variables description
* <b>materials.xacro </b>- Colors description

### Visualization
To view the robot model in <b>rviz</b> :
> Run the command in terminal
```sh
roslaunch differential_drive_robot_description rviz_visualize.launch
```
![Screenshot from 2021-07-07 14-11-34](https://user-images.githubusercontent.com/58605350/126119354-755b2438-8b37-459c-806e-b0b34d359306.png)

To view the robot model also in gazebo atmosphere :
>Run the command in terminal
```sh
roslaunch differential_drive_robot_gazebo differential_drive_robot_rviz_gazebo.launch
```
![Screenshot from 2021-07-07 14-12-07](https://user-images.githubusercontent.com/58605350/126119404-d0f64eee-97ff-4068-9f2b-26d9d8f1eb4b.png)

### Control
Now into the control part. We can control the robot motion using two methods,
* rqt robot steering
* differential_drive_robot_control package

#### Robot steering :
> Run the command in terminal
```sh
rqt
```
![rqt_robotSteering](https://user-images.githubusercontent.com/58605350/126119940-78897718-5b08-49b2-abea-5604dbfb7460.png)

In rqt we can find the robot steering under Plugins
> Plugins-->Robot Tools-->Robot Steering

![Screenshot from 2021-07-07 13-51-40](https://user-images.githubusercontent.com/58605350/126119982-9bce0030-6d41-4565-8545-379bf4f26bdb.png)

The robot steering appears in which we are able to change the linear and angluar motion velocity i.e., we are actually changing <b>cmd_vel</b> parameter .

#### differential_drive_robot_control :
In this package the motion is controlled using the keyboard. The corresponding script which is used for this purpose can be found at 
> ~catkin_ws/src/differential_drive_robot_control/nodes/teleop.py

There is already a standard teleop node implementation available (for the turtlebot), we simply reused the node. Then a remapping is done from the turtlebot_teleop_keyboard/cmd_vel to /cmd_vel of our robot in the teleop.launch file.

## Launching 
Run the following commands in terminal :
* Start Rviz and Gazebo to visualize
```sh
roslaunch differential_drive_robot_gazebo differential_drive_robot_rviz_gazebo.launch
```

* Start the teleop:
```sh
roslaunch differential_drive_robot_control teleop.launch
```
![Screenshot from 2021-07-05 20-33-17](https://user-images.githubusercontent.com/58605350/126120229-4c33f291-4bf1-43d2-9624-8c0b74ca4057.png)


You can find the end result >>here<<.

































