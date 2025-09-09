# 4-DOF Robotic Manipulator – Kinematics, Dynamics & Control  

This repository contains the design, modeling, kinematics, dynamics, and control simulation of a **4-DOF robotic manipulator (PRRR configuration)**. The project was developed as part of the **ELE00150M Robot Kinematics and Dynamics** module at the University of York.  

<p align="center">
  <img width="418" height="367" alt="image" src="https://github.com/user-attachments/assets/4550677d-8e0f-454c-9b28-6fed4907d636" />
</p>



---

## 📌 Project Objective  
The primary objective of this project was to:  
- **Design** a robotic manipulator with 4 joints (1 prismatic + 3 revolute).  
- **Model** its kinematics and dynamics mathematically.  
- **Implement** control strategies using **PD (Proportional-Derivative) controllers**.  
- **Simulate** the manipulator in MATLAB/Simulink using a CAD-imported model.  

---

## ⚙️ Design Overview  

- **Manipulator Type:** PRRR (Prismatic + Revolute × 3).  
- **Applications:** Educational, prototyping, light industrial tasks.  
- **Key Features:**  
  1. **Stable Base** – foundational support.  
  2. **Prismatic Joint (vertical)** – provides linear sliding motion.  
  3. **Two Revolute Arm Segments** – extend/retract motion for reach.  
  4. **Offset End Effector (L-shaped)** – suitable for grippers or sensors (e.g., for obstacle avoidance).  

---

## 📏 Dimensions  

| Link | Joint Type | Length (mm) | Width/Offset (mm) | Other Dimensions |
|------|------------|-------------|-------------------|------------------|
| 1    | Prismatic  | 1000        | 0                 | Ø = 200 |
| 2    | Prismatic  | 1000        | 0                 | Ø = 200 (inner), Ø = 250 (outer) |
| 3    | Revolute   | 500         | 0                 | Width = 100, Joint Ø = 80 |
| 4    | Revolute   | 500         | 0                 | Width = 100, Joint Ø = 80 |
| 5    | Revolute   | 500         | 300 offset        | Width = 100, Joint Ø = 80 |

---

## 🧮 Kinematics  

- **Forward Kinematics:**  
  - Modeled using **DH parameters**.  
  - Transformation matrices derived: T01, T12, T23, T34, T04, T0P.  

- **Inverse Kinematics:**  
  - Solves for joint variables (θ₂, θ₃, θ₄, d₁) given an end-effector pose.  
  - Validity check ensures workspace constraints are respected.  

- **Jacobian:**  
  - Derived symbolically for mapping joint velocities to end-effector velocities.  
  - Includes intermediate Jacobians for **center of mass tracking** (2D case).  

---

## ⚡ Dynamics  

- **Mass Matrix (M):** Computed symbolically using Jacobians, inertia tensors, and link masses.  
- **Centrifugal & Coriolis Effects:** Derived from partial derivatives of the mass matrix.  
- **Potential Energy & Gravity Vector:** Calculated from centers of mass under gravity (-9.81 m/s² along X-axis).  

---

## 🎮 Control  

- **Controller Type:** Proportional-Derivative (PD) joint-space controller.  
- **Implementation:** MATLAB Simulink model with imported CAD assembly.  
- **Control Law:**  

  <img width="565" height="116" alt="image" src="https://github.com/user-attachments/assets/fac97df4-64d9-4b83-88ac-28c3724a3761" />


- **Tuned Gains:**  
  - Joint 1 (Prismatic): Kp = 300000, Kd = 2000  
  - Joint 2 (Revolute): Kp = 500, Kd = 20  
  - Joint 3 (Revolute): Kp = 2000, Kd = 1700  
  - Joint 4 (Revolute): Kp = 1500, Kd = 50  

---

## 📊 Simulation & Results  

- **Setup:** Step commands applied to all joints.  
- **Observation:**  
  - Desired positions tracked with **minimal overshoot**.  
  - **Settling times** within acceptable range.  
  - **Accurate regulation** of prismatic and revolute joints.  
- **Conclusion:** The PD controller is effective, providing a foundation for hardware implementation.  

---

## 🚀 Applications & Use Cases  

This manipulator can be applied in:  
- **Pick-and-Place Operations** – transferring small objects.  
- **Assembly Tasks** – positioning and holding components.  
- **Material Handling** – light-duty transport.  
- **Education & Research** – robotics kinematics/dynamics study, teaching tool.  
- **Prototyping** – testing ideas for more complex robotic systems.  
- **Obstacle Avoidance (with sensors)** – using offset end effector as sensor mount.  


---

## ✅ Conclusion  

This project successfully integrates **mechanical design, symbolic modeling, and control simulation** of a robotic manipulator. It demonstrates a **complete workflow** from kinematic/dynamic analysis to control validation in simulation, offering a foundation for:  
- **Advanced control strategies** (e.g., adaptive or nonlinear control).  
- **Hardware implementation** in real robotic systems.  

---


