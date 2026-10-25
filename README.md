# AI-Vision Based Guided Pick and Place Dual Arm Manipulator

Mini project repository for the course **MCT300 / MEC300 Mini Project** (B.Tech. Mechanical Engineering - Digital Manufacturing) at **SASTRA Deemed to be University**.

* **Author:** Perugu Venkata Aditya (Reg. No: 127161035)
* **Guide:** Dr. Badri Narayanan R, Sr. Asst. Professor, School of Mechanical Engineering
* **Academic Year:** 2025–26 (Even Semester)

---

##  Project Overview
This project presents an autonomous, simulation-verified **vision-guided dual-arm robotic manipulator** designed to bridge perception, spatial reasoning, and motion control. Operating within an industrial simulation workflow, the system uses artificial intelligence to perceive dynamic environments, compute 3D spatial positioning, map coordinate reference frames, and execute synchronized pick-and-place operations.

### Key Features
* **Visual Perception:** YOLOv8 and YOLOv8n models trained to detect and classify 8 object classes (cubes and cylinders in red, green, white, and black) with high accuracy ($\text{mAP@0.5} \approx 0.99$).
* **Depth Fusion:** Combines 2D bounding boxes with simulated RGB-D camera data to extract true 3D spatial coordinates $(X, Y, Z)$.
* **Coordinate Transformation:** Uses the **ROS 2 TF** framework to map coordinates seamlessly from the camera frame to the robot base frame.
* **Motion Planning & Control:** Utilizes the **MATLAB Robotics Toolbox** for inverse kinematics to convert task-space target positions into precise joint-space angles.
* **Simulation Environment:** Fully implemented and validated inside **NVIDIA Isaac Sim** utilizing ROS 2 Action Graphs.

---

## 🛠️ Tech Stack & Tools
* **Simulation Platform:** NVIDIA Isaac Sim
* **Object Detection:** YOLOv8 / YOLOv8n (Ultralytics)
* **Middleware & Architecture:** ROS 2 Humble (Action Graph, TF)
* **Kinematics & Solver:** MATLAB Robotics Toolbox
* **Programming Languages:** Python, MATLAB

---

## 📂 Repository Contents & Links
* `Mini_Project_Presentation_Perugu_Venkata_Aditya_v2.pptx`: Comprehensive review presentation detailing the 8-step methodology, system architecture, results, and evaluation curves.
  * [View Presentation v2 Link](https://docs.google.com/presentation/d/1JboutIsVRSBazAftS-U3cfYh8CynYIXy/edit?usp=drive_link&ouid=110186731700141658012&rtpof=true&sd=true)
* `Mini_Project_Presentation_Perugu_Venkata_Aditya.pptx`: Core slide deck highlighting the structural overview and visual progression.
  * [View Core Presentation Link](https://docs.google.com/presentation/d/1DpI9osB0PRHa81bTwyb4ByhCCpzJuGMF/edit?usp=drive_link&ouid=110186731700141658012&rtpof=true&sd=true)
* `Mini_Project_Report_Perugu_Venkata_Aditya.docx`: Complete project report containing bonafide certificates, literature surveys, mathematical derivations, implementation details, and model performance evaluation graphs.
  * [View Project Report Document Link](https://docs.google.com/document/d/1LotfhD96-8xPyOB0W55eUKArGWZfWVrq/edit?usp=drive_link&ouid=110186731700141658012&rtpof=true&sd=true)

---

##  Methodology (8-Step Pipeline)
1. **Synthetic Data Generation:** Automated creation of varied virtual scenes, lighting, and camera viewpoints in NVIDIA Isaac Sim.
2. **Dataset Preparation:** Exporting annotations in YOLO format with normalized bounding box coordinates.
3. **Model Training:** Training YOLOv8 on the synthetic dataset and saving optimal weights (`best.pt`).
4. **Validation:** Evaluating detector performance using precision, recall, and F1-confidence curves.
5. **Depth Fusion:** Mapping box center pixels with depth values via pinhole camera equations.
6. **Frame Transformation:** Translating and rotating camera-frame coordinates to the robot base frame via ROS 2 TF.
7. **Grasp Planning & IK:** Computing joint configurations using MATLAB inverse kinematics.
8. **Execution:** Dual-arm execution involving picking, holding, transporting, and accurately placing objects.

---

##  Limitations & Future Scope
* **Current Status:** Tested exclusively in a controlled simulation environment (NVIDIA Isaac Sim).
* **Challenges Faced:** Action Graph path adjustments and frame alignment calibration were necessary to resolve initial coordinate discrepancies.
* **Future Work:** Deployment onto physical hardware with a real RGB-D camera, integration of collision-aware planning, closed-loop ROS 2 IK execution, and 6D pose estimation for dense clutter.
