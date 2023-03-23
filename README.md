<div id="top"></div>
<!--
README to be edited according to the need.
-->

# Autonomous Referee System Project - MSD2022

## Table of Content
1. [About The Project](#about-the-project)
2. [Feasibility Studies](#feasibility-studies)
3. [System Architecture](#system-architecture)
4. [Scope of the project](#scope-of-the-project)
5. [Method and Procedure](#method-and-procedure)
6. [Implementation and Validation for corner kick procedures](#implementation-and-validation-for-corner-kick-procedures)
7. [How to get smooth start](#how-to-get-smooth-start)
8. [Suggestion for improvement](#suggestion-for-improvement)
9. [Team](#team)

<!-- ABOUT THE PROJECT -->
## About The Project
The Autonomous Referee project, has been started in 2015 with the aim of assisting human referee, to be more reliable and accountable in decision making process in soccer robot game. This project has been developed by Eindhoven University of Technology for the RoboCup Middle Size League(MSL) and leverages cutting-edge technologies including computer vision, Machine Learning, and robotics to enable autonomous monitoring and management of soccer games. By integrating these technologies, the system can perform a wide range of functions such as tracking the ball position, detecting fouls, and signaling when the ball crosses the goal line. Such capabilities are expected to significantly reduce the chances of human error and ensure a more accurate and consistent refereeing judgment.
<!-- Feasibility Analysis -->
## Feasibility Studies
In order to develop the autonomous referee different technologies have been taken into consideration to create the Data to be implemented in the decision algorithm as follow:
- Using Tech United Data 
- Sensors Mounted on top of each robot
- Using Data Fusion for data collection
- Fixed Independent Sensors Mounted on the Stadiums

A complete report regarding the feasibility analysis of all these methods is provided and can be found in "Feasibility Check" folder.
According to our scope of the project, using stadium camera is the best option to choose from according to several factors including:
- Reliability
- Accessibility
- Easy to record and reuse


<!-- System Architecture -->
## System Architecture

The **Architecture Description** document can be found in the "System Architecture" folder. The purpose of this document is to provide a comprehensive overview of the system's design, so that stakeholders can understand how the system works, how it can be maintained and improved. All the procedures starting from stakeholder's need until the solution design is described in details in this document.

![System Architecture](https://user-images.githubusercontent.com/120414397/227020183-aba1bf27-cf96-4e15-9812-ae452a9f37d4.PNG)

<!-- Scope of the project -->
## Scope of the project 

Data acquisition strategy is selected as using multiple cameras around the stadium. For the starting point to set an integration delivery, a corner kick game start procedure will be used for validation of the algorithm but it can be used for other starting procedures such as goal kick or free kick. The reason for choosing this rule for validation of our algorithm can be summarized as follows: 

- The procedure is simple 
- Similar with other game starting procedures. 
- Camera technology is less complex, and hardware is reachable. 
- Implementation has a direct effect on the game, since the human referee does not measure distances during a real match. 
- The procedure is not directly related to any rule violations that makes it easy to integrate with future/past implementations. 

<!-- Method and procedure -->
## Method and procedure

By using one of the security cameras, the corner kick procedure will be used for validating the developed algorithm. In detail, an object detection algorithm will be run in a proper video recording to detect the ball and players from different teams. Then a bird’s eye transformation will be applied to calculate distances between them. By using the distances, the corner kick procedure will be checked and a signal depending on the players positions will be sent to the referee. A dataset containing robot images from different teams and ball images with and without a player around it should be collected in the first place. It has been decided to use YOLO to detect objeects. YOLO is well known deep learning architecture. It is not only easy to find several resources to implement but also to train. 

The explanation of the deep learning models for object detection is out of scope of this report. However, this can be addressed shortly. YOLO models are trained by different datasets for years and more accurate versions are developed. By using predefined software templates and also pretrained models, a high accuracy model can be achieved. The libraries are also optimized to automate using best parameters and strategies, they are fool-proof. The dataset is also expected to be small, compared to a standart dataset that needs to be used in a computer vision model. Therefore using an already implemented YOLO model would be beneficial for performance. 
In the following video the model can successfully detect ball and both teams robots:

![ezgif com-optimize (1)](https://user-images.githubusercontent.com/120414397/227038630-5f09d067-59e2-4e3e-8ea9-17e036398eee.gif)

The bird's eye vision transform is another to calculate distances between objects. A simple Euclidian distance calculation can be used, however a proper coordinate axis should be set before starting calculations. The simplest approach would be to get a top view of the image and a proper scaling should be done. By that way, one can convert pixel distances in to real-world measurements. In order to transform the auxiliary view in to top view, a linear transformation have to be done. This transformation matrix can be calculated by matching different points taken from image in terms of pixels and real-world measurements. Luckily, the field lines are perpendicular to each other, and they can be used to calculate transformation matrix.

![image](https://user-images.githubusercontent.com/120414397/227039753-4d70c67d-09ae-4569-9b98-30c239d85abb.png)


<!-- Implementation and Validation for corner kick procedures -->
## Implementation and Validation for corner kick procedures
The developed python code  can be found in the folder named "Developed Software".

According to corner kick procedure:

- The robot of the attacking team that is taking the kick is positioned at the ball. 
- All other players of the corner kick awarded team can stay anywhere on the field except in a circle with a radius of 2m around the ball until the ball is in play.
- All players of the opponent team can stay anywhere on the field except in a circle with a radius of 3m around the ball until the ball is in play. One robot may stay anywhere inside the penalty area (except goal area) of its own team, even if the distance to the ball is shorter than 3m. 

As a result any violation according to this procedures should be logged by autonmous referee


 



- <!-- How to get smooth start -->
## How to get smooth start

- It is recommended to not start from the scratch.
- Study the documents regarding the previous groups.
- It is highly recommended to get in touch with the Tech United team and use the Tech United repository in case of using TURTLEs. <br />
  Some of the people that you can get in touch with:<br />
  Tech United Website: https://www.techunited.nl/en/<br />
  Tech United (Techunited@tue.nl)<br />
  René van de Molengraft - Project Sponsor and Technical Consultant (M.J.G.v.d.Molengraft@tue.nl)<br />
  Ruben Beumer (r.m.beumer@tue.nl) <br />


- Ask for permission for using the surveillance cameras at the Robotics Lab.
  You may contact Ömür Arslan (o.arslan@tue.nl) to ask for the permission.
- Get in touch with MSD2022.
- Get in touch with Matthias Briegel<br />
  Matthias is the person who has previously worked on developing AutoRef system and he may share some interesting ideas for the development of the AutoRef system. (matthias_briegel@hotmail.com)
  
  <!-- Suggestion for improvement-->
## Suggestion for improvement
- Apply the algorithm for other rule's procedures such as free kick and goal kick
- Train the model to work with different types of robots and balls
- Try to combine different cameras for better view of the field

<!-- Team -->
## Team

This project has been carried out by the Mechatronic Systems Design (MSD) 2022 at Eindhoven University of Technology (TU/e) for the 1st in-house project in Block II of the program. The team members are as follow:

Elham Honarvar - Design Engineer and Project manager (e.honarvar@tue.nl)<br />
Farah Fadel - Design Engineer and Team Leader (f.fadel@tue.nl)<br />
Ahmet Demirel - Design Engineer and System Architect (a.demirel@tue.nl)<br />
Atefeh Dehghannayyeri - Design Engineer and Test Engineer (a.dehghannayeri@tue.nl)<br />



<p align="right">(<a href="#top">back to top</a>)</p>


