# IMR_Gazebo Package
## Dependencies


## Running Launch Files
Rviz Single Arm:
```
	roslaunch imr_arm_gazebo imr_arm_gazebo.launch
```
Rviz Double Arm with IMR Tabletop and Tray:
```
	roslaunch imr_arm_gazebo imr_arm_gazebo2.launch
```
## Controlling the Arms
- In order to the position controllers for the arms, the following rostopics can be used:
Arm 1:
/imr_arm1/joint1_position_controller/command
/imr_arm1/joint2_position_controller/command
/imr_arm1/joint3_position_controller/command
/imr_arm1/joint4_position_controller/command

/imr_arm2/joint1_position_controller/command
/imr_arm2/joint2_position_controller/command
/imr_arm2/joint3_position_controller/command
/imr_arm2/joint4_position_controller/command
- These position control messages work for both launch files described above
- Each topic type is a std_msgs/Float64 message and the zero configuration is with the arm pointing straight up.
- A good way to test this is to open rqt and use the Message Publisher plugin to pass these messages to the arm and see how it reacts.

## Troubleshooting
- Gazebo generally takes a while to shutdown, and crashing it with ctrl-c or ctrl-z can cause it to have trouble booting up the next time. I have found that ctrl-c generally expedites the closing process but does not cause a full crash
- If you get red text (errors) or sometimes even yellow (warnings) in the startup sequency of Gazebo, something has gone wrong so let it fully load and then close it out and fully unload before trying it again. Generally, cycling it in this way causes it to reset itself
- When there is another Gazebo instance still running on the system, but you cannot close it. Run the following
```
	killall -9 gazebo & killall -9 gzserver  & killall -9 gzclient
```
- This will kill all of the instances of Gazebo
