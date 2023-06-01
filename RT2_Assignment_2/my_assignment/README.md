Research Track II Second Assignment
=================================

Student: [Michele Moriconi](https://github.com/MickyMori) (S4861803), Professor: [Carmine Tommaso Recchiuto](https://github.com/CarmineD8)
------------------------------------------------------------------------------------------------------------------------------------------

This is the second assignment for the course Research Track 2 held at Genoa's University. The assignment required to create three nodes to make a robot move in the environment and to retrieve some data.

Installing and running
----------------------

The simulator requires a ROS installation, the ROS package [assignment_2_2022](https://github.com/CarmineD8/assignment_2_2022) and Jupyter Notebook.

To get the assignment_2_2022 package click on the link above or use the following command

```bash
$ git clone https://github.com/CarmineD8/assignment_2_2022
```

Before running the program make sure that the python files have the permission to be executed. To do so use the following commands inside the scrips folder:

```bash
$ chmod +x nodeB.py
```

```bash
$ chmod +x nodeC.py
```

To run the program use the command:

```bash
$ roslaunch my_assignment my_assignment.launch
```

Nodes
---------

### nodeA ###

The node A has the same functionalities it had in the orginal version but was made with Jupyter. It alse features some new functionalities as it displays the distance from the closest obstacle, it draws the trajectory of the robot and it shows in a graph the nuber of goals reached and cancelled.

### nodeB.py ###

The nodeB is a service node that keeps track of the number of goals reached and cancelled. This node subscribes to the topic "/reaching_goal/result" to get the data.

The service used by the node is GoalCounter.srv and it can be found inside the srv folder.

To visualize the data use the command:

```bash
$ rosservice call goalCounterService
```

### nodeC.py ###

The nodeC computes the distance of the robot from the goal and the speed of the robot. The node subscribe to the topic "/posVelData" to retrieve the position and velocity of the robot and after computing the distance and speed publishes them in the topic "/robotDistVel" using  the custom message DistAvgVel, that can be found in the msg folder. The node is set to publish the data once per second.

To visualize the data use the command:

```bash
$ rostopic echo /robotDistVel
```

Possible improvements
---------------------

In this section will be desceibed some possible future improvements of the code. 

When nodeC publishes the message while the goal has not been defined the distance increases a little over time, so I could add a treshold to avoid really small changes.

When the robots encounters a wall it turn in a fixed direction and not towards the shortest path. It could be implemented in the algorithm the code to make so that the robot can compute the best direction to turn.
 
