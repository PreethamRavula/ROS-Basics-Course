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
