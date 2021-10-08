# ROS-Basics-Course
Notes:

Chapter-1:

Publisher: Publisher is a ROS program that Writes message into a Topic.

Topic: Topic is a Communication System Through which ROS communicates with the Robot.

Services: Services are another Complex Communication systems in ROS, it is used to provide a specific functionality to the robot, Services are structured in two parts on one side there is a service server providing the functionality for anyone to call it, on the other side there is a server client which is the one that calls the service functionality.  
  Note: 1) Service must be up and running before calling it.

Action: Just like Topics and Services, Actions are also used to provide a functionality to the Robot for anyone to call it, the main difference between a service and an action is that when a service is called robot has to wait until the service ends to perform another task but when an action is called the robot can can perform some other task simultaneously and an action also provides a feedback while action is being performed.
  Note: 1) Action server must be up and running before calling it.

Command to start Rviz: rosrun rviz rviz

                                                      **END OF CHAPTER - 1**

Chapter-2:

ROS Programs are executed using some special kind of files called the Launch Files.

Command to control the turtle_bot robot using keyboard in the course: roslaunch turtlebot_teleop keyboard_teleop.launch

Instructions to control the Robot:

Control Your Turtlebot!
---------------------------
Moving around:
   u    i    o
   j    k    l
   m    ,    .

q/z : increase/decrease max speeds by 10%
w/x : increase/decrease only linear speed by 10%
e/c : increase/decrease only angular speed by 10%
space key, k : force stop
anything else : stop smoothly

CTRL-C to quit

Note: roslaunch is a command used to launch a ROS program its structure is as follows:

roslaunch <package_name> <launch_file>

*Package: ROS uses packages to organize its programs, package is all the files a ROS program contains such as cpp files, python files, configuration files, compilation files, launch files and parameter files.

Following structure is followed by the packages:

launch folder: contains the launch files
src folder: cpp and python files
CMakeLists.txt: List of cmake rules for compilation
package.xml: Package information and dependencies

To go to any ROS Package we use the Command: roscd <package_name>  it will take us to the path where the package specified is located.

Note:
  1) Every ROS program that needs to executed is organized in a package.
  2) Every ROS program created has to be organized in a package, they are the main organization systems of ROS.

What's inside a launch file?

All launch files are contained inside the  <launch> tag where we specify the following parameters.
pkg = "package_name" - name of the package that contains the ROS program to executed.
type = "python_file_name.py" - Name of the program file that we want to execute.
name = "node_name" - name of the ROS node that will launch the python file.
output = "type_of_output" - Through which channel will the output of the python file will be printed.

catkin workspace: In order to create package we need to work in a very specific workspace called a catkin workspace denoted as catkin_ws. The personal ROS packages created by the user should reside in the catkin workspace in order for ROS to use them.

the catkin_ws folder has three folders build, devel and src, all the packages must reside in the src folder and everytime a package needs to be created the directory should be ~/catkin_ws/src.

Command to create a package:
catkin_create_pkg <package_name> <package_dependencies>

command to check the packages available: rospack list
command to find a package we need: rospack list| grep <package_name>

*NOTE**: If you create your Python file from the shell, it may happen that it's created without execution permissions. If this happens, ROS won't be able to find it. If this is your case, you can give execution permissions to the file by typing the next command: **chmod +x name_of_the_file.py**

We can force ROS to refresh the package list using rospack profile

When a python file is created from a web shell, it doesn't have executable permeissions so, its up to us to give the file an executable permission.

ROS nodes:
  ROS nodes are programs made in ROS, to see what are the nodes running use the command: rosnode list  

  To get information about the nodes use the command: rosnode info <node_name>

Compiling a ROS package: Inorder the packages to work they must be compiled there are 2 ways in which this can be done
1) catkin_make: This command will compile the whole src directory and it must be issued in the catkin_ws directory for it to work. After compiling it is important the source the workspace, this will make sure ROS will get the latest changes.

source devel/setup.bash

  Sometimes when its needed to compile only a specific package where the changes has been made we can use the following command:

  catkin_make --only pkg with dependencies <package_name>

2) Catkin build: This command to will compile the whole src directory and needs to be issued in the catkin_ws directory to work.

  if we try 2 use 2 methods at once it throws an error message for this to work we jst need to stick with a single process, if we want to use another method the compiled files should be removed.

  rm -rf build/ devel/
  catkin build

  and as always sourcing the workspace after compiling is the way to go!

Parameter Server:

Parameter server is a dictionary that ROS uses to store parameter values, these parameters can be used by nodes during the run time and are normally used for static data such as configuration parameters.

To get the list of the parameters we can use the Command: rosparam list

To get value of a particular parameter we can type: rosparam get <parameter_name>

To set the value of a parameter we can use the command: rosparam set <parameter_name> <value>

Roscore: In order for everything to work we need Roscore to be running, it is the main process that manages all of the ROS system, it has always be running in order to work with ROS, the command we can use to set roscore up is "roscore"


Environment Variables:

ROS uses a set of LINUX system Environment variables in order for it to work, we can see those variables using the commmand:

export | grep ROS

The most important variables are the ROS_MASTER_URI and the ROS_PACKAGE_PATH.

So, Basically ROS is a frame work that enables us to do all these processes, it provides us with a background to process these nodes and manage communications between them.

                                            **END OF CHAPTER - 2**
