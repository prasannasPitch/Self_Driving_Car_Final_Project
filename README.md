# Udacity Self-Driving Car Engineer Nanodegree

## Capstone Project - System Integration

This project is the final project of  Udacity Self-Driving Car Engineer Nanodegree. Utilizing ROS nodes to implement waypoint tracking, control and classification of traffic lights, the final code will be implemented on a real-life autonomous vehichle, named Carla. The vehicle will be driven around a test track with the team's code.

### System Architecture
The following system architecture diagram shows the ROS nodes and topics used in the project.

![image](https://user-images.githubusercontent.com/37708330/57636758-1775d880-75aa-11e9-88ce-f16026764a9f.png)

### Project Structure

The project is divided into three modules : 1. Perception 2. Planning 3. Control. As the name suggests, the perception module is responsible for the
perception based data processing. By using the perception data, traffic lights and obstacles are detected. In this project, the camera is the only perception
sensor used to accomplish the goal. 


#### tl_detector.py
This package contains the traffic light detection node: tl_detector.py. This node takes in data from the /image_color, /current_pose, and /base_waypoints topics and publishes the locations to stop for red traffic lights to the /traffic_waypoint topic.

The /current_pose topic provides the vehicle's current position, and /base_waypoints provides a complete list of waypoints the car will be following.

You will build both a traffic light detection node and a traffic light classification node. Traffic light detection should take place within tl_detector.py, whereas traffic light classification should take place within ../tl_detector/light_classification_model/tl_classfier.py.
