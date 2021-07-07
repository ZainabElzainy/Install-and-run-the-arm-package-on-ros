# Install-and-run-the-arm-package-on-ros
 ### To install Install  arm package on ROS melodic
 1. download VirtualBox 
https://www.virtualbox.org/wiki/Downloads 

1. download ubuntu-18.04.5-desktop-amd64.iso.torrent  https://releases.ubuntu.com/18.04/
1. create the virtual machine
1. Install ROS melodic following step http://wiki.ros.org/melodic/Installation/Ubuntu
1. open the terminal 
1. Create a workspace by using catkin_make as **workspace1png.png and workspace2.png files** or follow the step **here** http://wiki.ros.org/catkin/Tutorials/create_a_workspace
 **do not forget**configure catkin_make with Python 3  By writing this command $ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
1. enter $ echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
1. enter $ source ~/.bashrc
1. - Add the “arduino_robot_arm” package to “src” folder
	$ cd ~/catkin_ws/src
	$ sudo apt install git
	$ git clone https://github.com/smart-methods/arduino_robot_arm 

1. install all the dependencies 
	$ cd ~/catkin_ws
	$ rosdep install --from-paths src --ignore-src -r -y
	$ sudo apt-get install ros-melodic-moveit
	$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
	$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
	$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
1. Compile the package
     $ catkin_make
1. Run the arm pakage in RViz by  this command :
$ roslaunch robot_arm_pkg check_motors.launch
1. open in gazebo 
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
1. control both of them together
$ rosrun robot_arm_pkg joint_states_to_gazebo.py

**in RViZ**
 control on arm by joint_state_publisher box
change the the base_joint ,shoulder ,elbow and wrist  as **RVIZ1.MP4 file**
**then ctrl+s (save changes)**

1. **then** to see final the changes in GAZEBO and RViz 
$ roslaunch moveit_pkg demo_gazebo.launch
 
**in RViz** you can do changes to  see changes in the arm before and after throgh the start box and goal box as **RViz_befor_after.jpg file** 
then enter Plan to see before Execute or Enter Plan and Execute
 
**finally**, you can see the changes in GAZEBO and RViz as **RVIZ2.MP4  and  GAZEBO+RViz.MP4 files**
