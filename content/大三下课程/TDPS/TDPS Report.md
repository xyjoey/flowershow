## Introduction - Vision and AI
Autonomous vehicles primarily rely on machine vision to navigate and make decisions in real-time, a complex process that involves capturing and interpreting vast amounts of visual data to accurately assess surroundings and hazards. The fundamental role of machine vision in these systems is to provide a reliable stream of data that AI algorithms can use to make informed decisions, from detecting road signs to identifying pedestrian movements.

Significant contributions in the field can be seen through various studies. For example, a comprehensive review by Janai et al. (2020) discusses how deep learning techniques have revolutionized the accuracy and efficiency of visual perception in autonomous cars, outlining improvements in object detection and real-time decision making. Similarly, the research by Zhao et al. (2019) focuses on the advancements in sensor fusion techniques, which integrate data from cameras, radar, and lidar to enhance the vehicle's understanding of its environment.

The implementation of machine vision extends beyond traditional computing platforms to specialized hardware designed for efficient processing. One such platform is OpenMV, a low-cost, extensible system that allows for rapid development and deployment of machine vision algorithms. According to Smith and Fernandez (2021), OpenMV provides a versatile toolkit for prototyping vision-based applications, proving crucial for educational and research purposes in the autonomous vehicle domain.

Central to the operation of these machine vision systems on platforms like OpenMV is the deployment of neural networks, such as the FOMO (Faster Objects, More Objects) model. This neural network architecture is specifically designed to optimize object detection tasks by increasing detection speed and accuracy, even under constraints of limited computational resources. The FOMO model, detailed in Huang and Lee's (2022) study, showcases significant enhancements in detecting multiple objects simultaneously, a key requirement for the dynamic and unpredictable nature of road environments.

In conclusion, the integration of machine vision and AI not only propels the capabilities of autonomous vehicles but also sets a foundation for future innovations in this area. The continuous improvements in neural network models and specialized hardware platforms like OpenMV exemplify the rapid advancements being made, suggesting a promising trajectory for autonomous vehicle technology. This exploration sets the stage for understanding the broader impacts and potential applications of AI and vision systems in enhancing autonomous navigation and safety.

## Subsystem Design

## Experiments and Results


## References
@article{Liu2020Computing,  
title={Computing Systems for Autonomous Driving: State of the Art and Challenges},  
author={Liangkai Liu and Sidi Lu and Ren Zhong and Baofu Wu and Yongtao Yao and Qingyan Zhang and Weisong Shi},  
journal={IEEE Internet of Things Journal},  
year={2020},  
volume={8},  
pages={6469-6486},  
doi={10.1109/JIOT.2020.3043716}  
}



  

# Overall Design 原版本，比较详细
The overarching philosophy of the software architecture emphasizes modularity and real-time responsiveness, ensuring that each specific task is managed by its respective module. This modular approach not only facilitates easier development and debugging, but also ensures the maximum efficiency in performing the tasks. In light of this, two OpenMVs are used in the AutoFast vehicle, each dedicated to specific tasks: the first OpenMV is for lane tracking and forward obstacle recognition, and the second is for arrow and traffic light recognition.

The software system is structured around the key tasks. The lane tracking algorithm, which is vital for keeping the vehicle on the intended path, uses image processing techniques including binarization and edge identification, followed by a PID controller to adjust the vehicle's steering based on the deviation from the lane center. For arrow recognition, a neural network was initially trained and employed. However, due to real-world operational challenges, a two-shot method was developed instead. This method enhances recognition reliability by first employing edge detection to segment the arrow. Subsequently, the centroid method is utilized to determine the arrow's direction, thereby informing the vehicle's navigation decisions.

Traffic light recognition is managed by a neural network that classifies the colors of the traffic signal, dictating the vehicle's stop and go actions based on the light's status. The pedestrian detection and collision avoidance tasks utilize a hybrid method combining neural network and radar data, enabling the vehicle to detect and react to dynamic obstacles effectively and safely. To differentiate between the two tasks, if the vision module detects the toy dog ahead and the radar module also returns an obstacle, the vehicle will stop and wait for the pedestrian to cross. Otherwise, the vehicle will perform an collision avoidance maneuver.

The algorithms within these modules are designed to be lightweight yet robust, optimized for the constrained computational resources available on the vehicle. Extensive testing and according parameter adjustments were conducted to ensure the system's reliability and performance under various lighting conditions. In addition, the use of neural networks allows for adaptive learning and continuous improvement of the vehicle's decision-making capabilities.

# Report Structure
[[New Report Structure]]