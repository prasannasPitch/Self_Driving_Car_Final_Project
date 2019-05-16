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


#### tl_detector
This package contains the traffic light detection node: tl_detector.py. This node takes in data from the /image_color, /current_pose, and /base_waypoints topics and publishes the locations to stop for red traffic lights to the /traffic_waypoint topic.

The /current_pose topic provides the vehicle's current position, and /base_waypoints provides a complete list of waypoints the car will be following.

You will build both a traffic light detection node and a traffic light classification node. Traffic light detection should take place within tl_detector.py, whereas traffic light classification should take place within ../tl_detector/light_classification_model/tl_classfier.py.

![image](https://user-images.githubusercontent.com/37708330/57873819-7d16ce80-780f-11e9-81cb-936421bd18df.png)

#### waypoint_updater

This package contains the waypoint updater node: waypoint_updater.py. The purpose of this node is to update the target velocity property of each waypoint based on traffic light and obstacle detection data. This node will subscribe to the /base_waypoints, /current_pose, /obstacle_waypoint, and /traffic_waypoint topics, and publish a list of waypoints ahead of the car with target velocities to the /final_waypoints topic.

![image](https://user-images.githubusercontent.com/37708330/57873837-83a54600-780f-11e9-9b9c-7ef44e22a12c.png)

#### twist_controller

Carla is equipped with a drive-by-wire (dbw) system, meaning the throttle, brake, and steering have electronic control. This package contains the files that are responsible for control of the vehicle: the node dbw_node.py and the file twist_controller.py, along with a pid and lowpass filter that you can use in your implementation. The dbw_node subscribes to the /current_velocity topic along with the /twist_cmd topic to receive target linear and angular velocities. Additionally, this node will subscribe to /vehicle/dbw_enabled, which indicates if the car is under dbw or driver control. This node will publish throttle, brake, and steering commands to the /vehicle/throttle_cmd, /vehicle/brake_cmd, and /vehicle/steering_cmd topics.

![image](https://user-images.githubusercontent.com/37708330/57873846-8869fa00-780f-11e9-8a30-5d23d902b0b4.png)
