# **Adaptive Traffic Singal Control System**
The project aims to reduce congestion in saturated road networks. A traditional rule-based traffic signal control system is transformed into an adaptive system using deep reinforcement learning to reduce congestion in saturated road networks.

---


## **Data**
Real data is collected from 12 intersections in Chifeng, China are used in this project. 4.84 million raw records are given, from which 1.94 million valid records are selected after data cleaning. 


Road data contains datetime, road lane, traffic flow, vehicle type, and vehicle speed etc.


Traffic singal includes different phases scheduled with duration.


Map data are created by me using SUMO (Simulation of Urban MObility). Special lanes, car flows and traffic lights are created in netedit.
<p float="left">
  <img src=./img/road_map.png  width="300" height="180"/>
  <img src=./img/sumo_full_map.png width="300" height="180" />
</p>

<p float="left">
  <img src=./img/sumo_road_lane.png  width="300" height="180"/>
  <img src=./img/sumo_intersection.png  width="300" height="180"/>
</p>

- The top left image is captured from Gaode Map with 12 intersections.  <br/>
- The top right image is the converted road map that will be used in SUMO. <br/>
- The bottom left image shows a specific intersection in SUMO with different vehicle lanes.  <br/>
- The bottom right image shows connections for a junction describing how incoming and outgoing edges of junctions are connected.


Below is an example of executing the traffic simulation with Sumo-gui.
<img src=./img/roadnet_testing.gif  width="300" height=""/>

---

## **Model**
The original source code is derived from the paper: "Multi-Agent Deep Reinforcement Learning for Large-Scale Traffic Signal Control" ([early access version](https://ieeexplore.ieee.org/document/8667868), [preprint version](https://arxiv.org/pdf/1903.04527.pdf), [source code](https://github.com/cts198859/deeprl_signal_control)).

The model is tailored  according to the specific situation. Please refer to the backbone of the original paper:<br/>
<img src=./img/original_backbone.png>


---
## **Performance**
According to the original traditional traffic signal control system, the process is redesigned according to the following rule:
-	The duration of each traffic signal is set to 15 seconds, while the maximum duration of the red light is 120 seconds, and the green light is 50 seconds.
-	The junction information (e.g., total queue length) is collected and fed into the decision model, producing a strategy for each signal in every intersection. 
---

<p float="left">
<img src=./img/before.png  width="300" height="180"/>
<img src=./img/after.png width="300" height="180" />
</p> 

The above images show the result of traffic simulation using SUMO at 8:04 AM. The left image is the simulation before optimization, while the right image is the traffic condition after optimization.

Overall, the model works well and the queue length at each intersection reduces by an average of 31.7%, especially for the east-west traffic flow. 

More information should be collected to use the model in the real world (more precise road map, traffic flow information, vehicle speed). The pedestrian signal should also be taken into consideration. The model should be tested at different time periods of the day.

---


# Citation
```
@article{chu2019multi,
  title={Multi-Agent Deep Reinforcement Learning for Large-Scale Traffic Signal Control},
  author={Chu, Tianshu and Wang, Jie and Codec{\`a}, Lara and Li, Zhaojian},
  journal={IEEE Transactions on Intelligent Transportation Systems},
  year={2019},
  publisher={IEEE}
}

