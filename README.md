# Where Am I?
Udacity Robond Localization project

## Project Overview
Welcome to the localization project! In this project, you will learn to utilize ROS packages to accurately localize a mobile robot inside a provided map in the Gazebo and RViz simulation environments.

Over the course of this lesson, you will learn about several aspects of robotics with a focus on ROS, including -

- Building a mobile robot for simulated tasks.

- Creating a ROS package that launches a custom robot model in a Gazebo world and utilizes packages like AMCL and the Navigation Stack.

- Exploring, adding, and tuning specific parameters corresponding to each package to achieve the best possible localization results.

Note: Similar to project 1, you are required to document the work along the way. Use the project rubric as reference when you work through the project!


## Steps to complete the project
1. Follow the steps outlined in this Project Lesson, to create your own ROS package, develop a mobile robot model for Gazebo, and integrate the AMCL and Navigation ROS packages for localizing the robot in the provided map.

2. Using the Parameter Tuning section as the basis, add and tune parameters for your ROS packages to improve your localization results in the map provided. Feel free to explore new parameters using the resources provided earlier in the same section. Please include the image of RViz with the robot at goal position and the PoseArray displayed. Each run may take a long time so don't forget to screenshot your robot at the goal position!

3. After achieving the desired results for the robot model introduced in the lesson, implement your own robot model with significant changes to the robot's base and possibly sensor locations.

4. Check your previous parameter settings with your new robot model, and improve upon your localization results as required for this new robot.

5. Document your work. You could use this Writeup Template. 

## Robot Model: Basic Setup
As a roboticist or a robotics software engineer, building your own robots is a very valuable skill and offers a lot of experience in solving problems in the domain. Often, there are limitations around building your own robot for a specific task, especially related to available resources or costs. 

That's where simulation environments are quite beneficial. Not only do you have freedom over what kind of robot you can build, but you also get to experiment and test different scenarios with relative ease and at a faster pace. For example, you can have a simulated drone to take in camera data for obstacle avoidance in a simulated city, without worrying about it crashing into a building!

You previously learned about the Unified Robot Description Format (URDF) in Term-1. In this section, you will build a very basic mobile robot model by creating its own URDF file!



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

