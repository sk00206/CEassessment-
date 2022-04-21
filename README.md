#  Autonomous Robot navigation
In this project we are aiming to simulate an atonomous robot that will navigate on it's own in a map filled with obstacles to reach a specific target without hitting or crossing any of the obstacles. It is a simple project that can be used as a start for your own design of future atonomous car. All required programs will be listed below.

# Required programs 
You need to download and install the following before working: 
- Robotics tool box
- Python
- Visual studio code 
We used them on ubuntu following these steps:
* Install [Virtualbox](https://www.virtualbox.org/) 
* Setting up the computer with [Ubuntu 18.04 LTS](https://old-releases.ubuntu.com/releases/18.04.5/) follow [this video](https://www.youtube.com/watch?v=x5MhydijWmc&t=1058sfor) more details 
* install [python](https://www.python.org/downloads/) choose any version we worked with 3.8
* install [Robotics toolbox](https://github.com/petercorke/robotics-toolbox-python/tree/71183f3221cf9ced69420f07ade06f4514c256ba)
* install [Visual studio code](https://code.visualstudio.com/)

# Code 
In this part we are focusing just on the code's functionality and breaking the code part by part for detailed explanation 
## functions used 
1. Input function `eval(input('enter text here))` to take input from user 
2. 
## code explanation part by part 
import these first to start programming   `from roboticstoolbox import Bicycle, RandomPath, VehicleIcon,RangeBearingSensor,LandmarkMap
from math import pi ,atan2
import matplotlib.pyplot as plt` 

`veh = Bicycle(
)` creates an object for your vehicle it takes information about the vehicle 
like we did here

`veh = Bicycle(
 animation = anim,
 control = RandomPath, 
 dim= 10 , 
 x0=( x,y ,0) ,
 )`  we set the map to be 10x10 and the initial position x0 to be x coordinate which is the user input and y which is the user input and we set the steer angle to be 0. this means that the x0 takes three parametrs (x coordinate,y coordinate,steerangle)
 
 Download a.png robot vector image from the internet and place it in the same working directory (folder) as your python programme for your robot icon.
 `anim = VehicleIcon('index.jpeg', scale = 1)`
 Creating an instance of VehicleIcon which you will put the information of the icon in. 
 We used a .jpeg but use a .png for better demonstration.
 
 `veh.init(plot=True)` is to be able to visualize your robot on the grid you created
 
 Creating a goal for the robot to go to 
 `goal=[x1,y1];
goal_marker_style = {
 'marker': 'D',
 'markersize': 3, 
 'color': 'b',
}` Since the goal coordinates will be user input we have set it to be x1 and y1 and in the start of the code we set x1 and y1 to equal a user input. the `goal_marker_style =` takes the style of the goal for example here it was set that the marker = Diamond and in coding it is D, and the marker size to be 3 and for it's color to be blue 

`plt.plot(goal[0], goal[1], **goal_marker_style)` plotting the goal 

To load the obstacles `map = LandmarkMap (n, 10)` where n is the number of obstacles and they are user input and in the start of the code we set n to equal a user input. And the 10 means in 10 unit grid.

`map.plot()` to plot the Land Marks.

To add the range bearing sensor which we will use to find out the distance between the robot and the obstacle and to stop if necessary.
`ensor=RangeBearingSensor(robot=veh, map= map ,animate=True)`

To printout the readings from the sensor. 
`print('Sensor readings: \n ' , sensor.h(veh.x))`

## flowchart 

# Discussing results 
## Screenshots 

# Areas for innovation 

