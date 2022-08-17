---
marp: true
theme: uncover
style: |
    :root {
    --color-background: #FFFFFF;
    --color-foreground: #8B2781;
    --color-highlight: #8B2781;
    --color-dimmed: #888888;
    }
    h1 {
      color: #51247A
    }
    h2 {
      color: #8B2781
    }
    h3 {
      color: #220033
    }
    section {
      font-size: 30px;
    }
paginate: true

---

# METR4202
## Robotics & Automation
### Week 4: Practical - Intro to RViz and TFs 

---

### Learning Outcomes 
- What is RViz?
- Writing a ROS Node in OOP paradigm 
- Writing Forward Kinematics in Python
- What are TFs in ROS?
---

### What is RViz (Robot Visualiser)?
- 3D Visualisation software tool for robots, sensors and algorithms
    - View robots written in URDF (Unified Robotics Description Format) 
    - Move robots wrriten in URDF
    - Loads of community made plugins for additional functionality 

---

### Let's Visualise a 2R robot
Create a `catkin_ws` in your home directory if not present

```SH
cd ~
mkdir -p catkin_ws/src
```
Install [practical 4](https://github.com/UQ-METR4202/practical_4.git) ROS package from github

```SH
cd ~/catkin_ws/src
git clone https://github.com/UQ-METR4202/practical_4.git
```

Building the package

```SH
cd ~/catkin_ws
catkin build
source ./devel/setup.bash
```
---

### Let's Visualise a 2R robot
Launch the `practical_4` package

```SH
roslaunch practical_4 display.launch
```

---

### What is the packages Node/Topic structure?

---

### What is the packages Node/Topic structure?
ROS has inbuilt visualiser for figuring this out

```SH
rosrun rqt_graph rqt_graph
```

---

### Let's write a ROS Node to intercept joint angles
Create python file in `/scripts` dir of `practical_4` package

```SH
cd ~/catkin_ws
mkdir -p ./src/practical_4/scripts/tf_demo.py
code .
```

---

### Let's Visualise the Node/Topic structure now
Use inbuilt ROS visualiser

*Terminal 1*
```SH
cd ~/catkin_ws
catkin build
source ./devel/setup.bash
roslaunch practical_4 display.launch
```

*Terminal 2*
```SH
noetic
cd ~/catkin_ws
source ./devel/setup.bash
rosrun practical_4 tf_demo.py
```

---

### Let's remap node and Visualise Node/Topic structure 
Reroute `/joint_states` topic to `/tf_demo_joint_states` in `display.launch`

---

### Let's write Forward Kinematics for Robot 
- Use Product of exponentials
- Use RViz/URDF to obtain link lengths
- Joint angles are about +ve y axis

---

### ROS already does the FK for us!
The power of `TF` in ROS

```SH
rosrun tf tf_echo /base_link /top_link
```

---

### Writing TF lookups in python   
Using `tf.TransformListener()`

---

## Next Week
- Continuation on TFs
- Continuation on ROS architecure and using OOP with ROS