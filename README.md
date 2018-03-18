# Where Am I?
Udacity Robond Localization project

## Project Overview
Welcome to the localization project! In this project, you will learn to utilize ROS packages to accurately localize a mobile robot inside a provided map in the Gazebo and RViz simulation environments.

Over the course of this lesson, you will learn about several aspects of robotics with a focus on ROS, including -

- Building a mobile robot for simulated tasks.

- Creating a ROS package that launches a custom robot model in a Gazebo world and utilizes packages like AMCL and the Navigation Stack.

- Exploring, adding, and tuning specific parameters corresponding to each package to achieve the best possible localization results.

Note: Similar to project 1, you are required to document the work along the way. Use the project rubric as reference when you work through the project!

## Gazebo: Hello, world!
In Term 1, you worked on several projects where most of the project structure was already implemented or provided to you. In this section, you will start from scratch and develop your own package in ROS throughout this project!

[image_1]: ./images/empty_gazebo_world.png
![alt text][image_1] 

## Robot Model: Basic Setup
As a roboticist or a robotics software engineer, building your own robots is a very valuable skill and offers a lot of experience in solving problems in the domain. Often, there are limitations around building your own robot for a specific task, especially related to available resources or costs. 

That's where simulation environments are quite beneficial. Not only do you have freedom over what kind of robot you can build, but you also get to experiment and test different scenarios with relative ease and at a faster pace. For example, you can have a simulated drone to take in camera data for obstacle avoidance in a simulated city, without worrying about it crashing into a building!

You previously learned about the Unified Robot Description Format (URDF) in Term-1. In this section, you will build a very basic mobile robot model by creating its own URDF file!

### Robot URDF
Let's first create a new folder in your package directory and an empty xacro file for the robot's URDF description.

### Launch Model

[image_2]: ./images/empty_gazebo_world.png
![alt text][image_2]

Create a new launch file that will help load the URDF file.

### Robot Actuation

[image_3]: ./images/empty_gazebo_world.png
![alt text][image_3]

Great work till now! You will next add wheels to your robot. For this robot, you will require only two wheels. Each wheel is represented as a link and is connected to the base link (the chassis) with a joint. 

### Robot Sensors

[image_4]: ./images/empty_gazebo_world.png
![alt text][image_4]

During both Term 1 and 2, you have come across and learned about different sensors that help provide robot feedback about its environment. For this robot, you will add two sensors - a camera and a laser rangefinder.

### Laser Rangefinder
Now, let's add the laser rangefinder. ROS offers support for a lot of different types of sensors. One of them, that you will be using for this robot and the project, is the Hokuyo rangefinder! 

### Gazebo Plugins
You have successfully added sensors to your robot, allowing it to visualize the world around it! But how exactly does the camera sensor takes those images during simulation? How exactly does your robot move in a simulated environment? 

The URDF in itself can't help with that. However, Gazebo allows us to create or use plugins that help utilize all available gazebo functionality in order to implement specific use-cases for specific models. 

## RViz
While Gazebo is a physics simulator, RViz can visualize any type of sensor data being published over a ROS topic like camera images, point clouds, Lidar data, etc. This data can be a live stream coming directly from the sensor or pre-recorded data stored as a bag file. RViz is your one-stop tool to visualize all the three core aspects of a robot: Perception, Decision Making, and Actuation.

In this section, you will integrate your model into RViz and visualize data from the camera and laser sensors!

## Adding a map

[image_0]: ./images/localization_map.png
![alt text][image_0] 

So far, you have created a robot model from scratch, added sensors to it to visualize its surroundings, and developed a package for this robot to launch it in a simulated environment. That's a great amount of work you have accomplished!

But, what surroundings is your robot currently sensing? And how would you go about localizing the robot if you don't know where you wish to localize it? 

In this section, you will launch your robot in a new environment using a map created by Clearpath Robotics.

## AMCL
You learned about Monte Carlo Localization (MCL) in great detail in a previous lesson. Adaptive Monte Carlo Localization (AMCL) dynamically adjusts the number of particles over a period of time, as the robot navigates around in a map. This adaptive process offers a significant computational advantage over MCL. 

The ROS amcl package implements this variant and you will integrate this package with your robot to localize it inside the provided map.

### Navigation Stack
You will be working with the move_base package using which you can define a goal position for your robot in the map, and the robot will navigate to that goal position.

The move_base package is a very powerful tool. It utilizes a costmap - where each part of the map is divided into which area is occupied, like walls or obstacles, and which area is unoccupied. As the robot moves around, a local costmap, in relation to the global costmap, keeps getting updated allowing the package to define a continuous path for the robot to move along. 

What makes this package more remarkable is that it has some built-in corrective behaviors or maneuvers. Based on specific conditions, like detecting a particular obstacle or if the robot is stuck, it will navigate the robot around the obstacle or rotate the robot till it finds a clear path ahead. 

## Parameter Tuning
Exploring, adding, and tuning parameters for the amcl and move_base packages are some of the main goals of this project. In this section, we will cover some parameters that will help you get started, but you will get a chance to experiment with the rest and observe what effect they bring about. 

## Testing
Going through different parameters, understanding their implications, and testing it all out in RViz will be a challenging task. That’s why we recommend you test your implementation on a shorter path rather than the entire map. 

The pose your robot starts with places it somewhere in the middle of a corridor. It is recommended that you carry out some initial tests across the length of that corridor before the robot takes a turn. This will help you figure out several aspects to improve your implementation. You can figure out if the robot gets stuck or not initially based on where it thinks are the walls with respect to its position, how quickly the robot moves and how quickly it sticks to the trajectory, and more importantly how good the PoseArray looks as the robot moves forward. Does it shrink or get worse? 

You can easily carry out these tests using the 2D Nav Goal button in RViz’ toolbar, as we covered in another section.

## Launching
The above method is great for testing, but for your project submission your robot needs to navigate to a specific goal position while localizing itself along the way. In the project repo we have provided you with a C++ node that will navigate the robot to the goal position for you. You will need to create a new folder for that.


## Recap
You have done a great job so far with this project and hopefully learned a lot to be able to create your own projects for other robotics tasks! Let’s quickly recap what you covered in this project lesson -

- You learned to build your own simulated mobile robot, added sensors to it, and integrated it with Gazebo and RViz by developing a ROS package for that robot.

- Next, you integrated ROS packages like the Adaptive Monte Carlo Localization (AMCL) package and the Navigation Stack, that would allow your robot to navigate and localize itself in a particular environment or map.

- You then learned about different parameters corresponding to these packages that could help you improve your results.

## Project Instructions
You have made significant headway with your project already. There are a few more steps that you have to work on for your submission -

- You need to explore and add more parameters to improve upon your localization results. Include a screenshot of the supplied robot at the goal position.

- Once you achieve good results on the mobile robot we covered in the classroom, you will create your own mobile robot with significant changes to the model, and aim to achieve similar results for that robot! There's a lot you can experiment with here - you could try different wheels or a different laser sensor, or different drive controllers etc.

You can find more details regarding your submission in the next section. Good luck!

## Project Submission
### Steps to complete the project
1. Follow the steps outlined in this Project Lesson, to create your own ROS package, develop a mobile robot model for Gazebo, and integrate the AMCL and Navigation ROS packages for localizing the robot in the provided map.

2. Using the Parameter Tuning section as the basis, add and tune parameters for your ROS packages to improve your localization results in the map provided. Feel free to explore new parameters using the resources provided earlier in the same section. Please include the image of RViz with the robot at goal position and the PoseArray displayed. Each run may take a long time so don't forget to screenshot your robot at the goal position!

3. After achieving the desired results for the robot model introduced in the lesson, implement your own robot model with significant changes to the robot's base and possibly sensor locations.

4. Check your previous parameter settings with your new robot model, and improve upon your localization results as required for this new robot.

5. Document your work. You could use this Writeup Template. 

### Evaluation
Once you have completed your project, use the Project Rubric to review the project. If you have covered all of the points in the rubric, then you are ready to submit! If you see room for improvement in any category in which you do not meet specifications, keep working and engage in discussions with your fellow students and your mentor!

Your project will be evaluated by a Udacity reviewer according to the same Project Rubric. Your project must "meet specifications" in each category in order for your submission to pass.

### Submission
### What to include in your submission
You may submit your project as a zip file or with a link to a GitHub repo. The submission must include these items:

1. Your entire ROS package that you developed based on this Project's lesson. Your project reviewer should be able to take the ROS package as is and run it on their system.

2. The Project write-up in the PDF format that addresses all the rubric points and is based on the template linked above.

3. Images of your results for both the robot models, the one provided in the Classroom and the one you created. Each image should consist of the robot at the goal position and with the PoseArray being displayed in RViz. Both images should have your full name watermarked on them. You can include these images as part of your write-up, but for clarity purposes, it is recommended that you include them separately as well.


