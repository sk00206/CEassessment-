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
2. `abs()`	Returns the absolute value of a number
3. `eval()`	Evaluates and executes an expression

and many more to be explained below
## code explanation part by part 
import these first to start programming  

`from roboticstoolbox import Bicycle, RandomPath, VehicleIcon,RangeBearingSensor,LandmarkMap
from math import pi ,atan2
import matplotlib.pyplot as plt` 

Taking user input for initial position 

`x = eval(input("Enter the x coordinated of initial position : "))
y = eval(input("Enter the y coordinated of initial position : "))`


Taking user input for target

`x1 = eval(input("Enter the x coordinated of target position : "))
y1 = eval(input("Enter the y coordinated of target position : "))`


Taking user input for number of obstacles

`n = int(input("Enter the number of obstacles : "))`

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

`run = True
while(run):
    for i in sensor.h(veh.x):
        if i[0] < 3 :
            if abs(i[1]<pi):
                run = False`
This part of the code first sets that run = true then creates a while loop so while the robot is running for the readings coming out of the sensor if there is an obstacle that is within a tolerance of 3-units in range and 𝜋 in angles it stops. 

As for this part of the code it's responsible for moving the robot

       `else:
            run = True 
            while(run): 
                goal_heading = atan2(
                goal[1] - veh.x[1], 
                goal[0] - veh.x[0])
                steer = goal_heading - veh.x[2]
                veh.step(1,steer)
                if((abs(goal[0]-veh.x[0]) > 1) or (abs(goal[1]-veh.x[1]) > 1)):
                    run=True
                else:
                    run = False`
* The while loop is a continuous loop that only exits when the vehicle reaches the destination spot. 
* Throughout the travel of the vehicle, the goal heading variable calculates the angle of the target with respect to the vehicle. 
* As a result, the vehicle's required steering angle will alter. 
* All that remains is to ensure that the vehicle stops when it reaches the target point by keeping the linear velocity constant and computing the steer angle as described previously.
* The run flag is set to True, and the programme continues to execute, if the absolute difference between the vehicle's x-y coordinates and the target location does not exceed a preset tolerance, in this case 0.05. 
* Otherwise, the loop exists and the run flag is set to False.
* The run flag is set to True, and the programme continues to execute, if the absolute difference between the vehicle's x-y coordinates and the target location does     not exceed a preset tolerance, in this case 0.05. 
* Otherwise, the loop exists and the run flag is set to False.



## flowchart 

# Discussing results 
## Screenshots 
This is an image of the map created with the robot only 

![image](https://user-images.githubusercontent.com/99183661/164906705-58a043c8-10b7-44fa-9d89-043a547bff70.png)

This is an image of the map created with robot on its way to the target(the blue diamond) and surrounded by obstacles

![image](https://user-images.githubusercontent.com/99723032/164911294-e30e43e4-c213-434d-a4f7-5ecefae019c4.png)

This is an image of the robot when it reached its target

![image](https://user-images.githubusercontent.com/99723032/164911521-493b426b-6657-4a44-82bd-375f8feb5821.png)

This is an image of the expected output when the user runs the code 

![image](https://user-images.githubusercontent.com/99723032/164911700-84a0cb55-50b4-4bad-8a85-2a630d8be0bc.png)


# Areas for innovation 

1. Strengthen the part of the code that is responsible for avoiding the obstacles 
2. Try to do the same task in a shorter code 
3. Using functions then recalling them
4. Using a code to make the obstacles and the target move so that the robot can detect their movement and move accordingly
5. analyzing which route has the least obstacles and use it

