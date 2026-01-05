# MATLAB Control Systems Lab  
## Exercises 03 – 05

This README documents the **aim, apparatus, procedure, inference, and result** for Control Systems Laboratory experiments **03 to 05**, written in a clear and humanised manner suitable for **lab records, viva, and GitHub documentation**.

---

## Experiment 01 – Implementation of Block Diagram in Simulink Environment

---

## Aim
To implement and simulate the given mathematical expressions and transfer function–based block diagrams using the Simulink environment and to verify the correctness of the obtained outputs.

---

## Apparatus Required
- MATLAB 2024 with Simulink Package  
- Computer system  

---

## Procedure
1. MATLAB was opened and the Simulink Library Browser was accessed.  
2. A new Simulink model was created.  
3. The given mathematical expressions were implemented using basic Simulink blocks such as Constant, Gain, Add, and Product blocks.  
4. The input values were assigned as specified and the simulation was run to obtain the output.  
5. Transfer Function blocks were then used to implement the given transfer function–based block diagram.  
6. The blocks were interconnected according to the given diagram and required gains were applied.  
7. The simulation was executed and the final output was observed and verified.

---

## Inference
The simulation demonstrates that mathematical expressions and transfer function relationships can be accurately represented using Simulink block diagrams. Correct selection of blocks and proper interconnection are essential to obtain the desired output. The visual block-based approach of Simulink makes system modelling intuitive and easy to analyse.

---

## Result
The given mathematical expressions and transfer function–based block diagrams were successfully implemented in the Simulink environment. The output obtained from the simulation closely matched the expected theoretical results, confirming the correctness of the model and implementation.

---

## Experiment 02 – Mechanical Translational System

## IMPLEMENTATION OF MECHANICAL TRANSLATIONAL SYSTEM IN SIMULINK ENVIRONMENT

---

### Aim
To model, implement, and simulate a mechanical translational system using differential equations in the Simulink environment and to study the effect of mass, damping, and spring elements on system behaviour.

---

### Apparatus Required
- MATLAB 2024 with Simulink Package  
- Computer system  

---

### Procedure
1. The mechanical translational system was analysed and the governing differential equations were derived using Newton’s laws of motion.  
2. The equations were rearranged into implementation form by keeping the highest-order derivative on the left-hand side.  
3. MATLAB was opened and the Simulink library browser was launched.  
4. A new Simulink model was created and integrator blocks were used to implement the derived equations.  
5. Appropriate system parameters such as mass, damping coefficient, and spring constant were assigned.  
6. A discrete impulse force was applied as input.  
7. The simulation was executed and the displacement versus time response was observed for each system configuration.

### Inference
The simulation results clearly show the influence of individual mechanical elements on system behaviour. A mass-only system continues to move indefinitely due to the absence of resistance. Introducing a damper causes the motion to decay over time. When both spring and damper are present, the system oscillates initially and gradually settles, demonstrating damped oscillatory behaviour. This confirms the combined effects of inertia, damping, and stiffness on mechanical systems.

---

### Result
The mechanical translational systems were successfully modelled and simulated in the Simulink environment using differential equations. The observed responses for mass, mass–damper, and mass–spring–damper systems closely matched theoretical expectations, validating the correctness of modelling and simulation.

---

## EXERCISE 03  
## Time Domain Response of a First-Order System

### Aim
To analyse the step response of a first-order system using MATLAB and to study the effect of gain and time constant on the system response and stability.

---

### Apparatus Required
- MATLAB 2024 with Control System Toolbox  
- Computer system  

---

### Procedure
1. MATLAB was opened and a new script file was created.  
2. The transfer function of a first-order system was defined using suitable values of gain and time constant.  
3. The step response of the system was generated using the `step()` command.  
4. The gain was varied while keeping the time constant constant and the change in output was observed.  
5. The time constant was varied while keeping the gain constant and the response speed was analysed.  
6. Poles of the system were checked to verify stability.

---

### Inference
The step response shows that a first-order system reaches steady state smoothly without oscillations. Changing the gain affects only the final output value, whereas changing the time constant affects how fast the system responds. For positive values of the time constant, the system pole lies in the left half plane, ensuring stable behaviour.

---

### Result
The step responses of a first-order system were successfully generated using MATLAB. The effects of gain and time constant on system behaviour were observed, and the system was found to be stable for all positive values of the time constant.

---

## EXERCISE 04  
## Time Domain Response of Second-Order Systems

### Aim
To study the time-domain response of second-order systems and analyse the effect of damping ratio and natural frequency on system performance and stability.

---

### Apparatus Required
- MATLAB 2024 with Control System Toolbox  
- Computer system  

---

### Procedure
1. MATLAB was opened and the standard second-order transfer function was defined.  
2. The step response of the nominal system was plotted.  
3. The damping ratio was varied to observe undamped, underdamped, critically damped, and overdamped responses.  
4. The natural frequency was varied while keeping the damping ratio constant to study its effect on response speed.  
5. Pole locations were analysed to determine the stability of the system.

---

### Inference
The response of a second-order system depends mainly on the damping ratio and natural frequency. Undamped systems show continuous oscillations, underdamped systems oscillate with decreasing amplitude, critically damped systems reach steady state quickly without oscillations, and overdamped systems respond slowly. Systems with positive damping ratio have poles in the left half plane and are stable.

---

### Result
The step responses of various second-order systems were successfully simulated using MATLAB. The influence of damping ratio and natural frequency on oscillations, overshoot, and response speed was clearly observed, and the stability conditions of second-order systems were verified.

---

## EXERCISE 05  
## Stability Analysis Using Pole–Zero Plot

### Aim
To analyse the stability of linear time-invariant systems using pole–zero plots and to validate the stability behaviour through step response analysis.

---

### Apparatus Required
- MATLAB 2024 with Control System Toolbox  
- Computer system  

---

### Procedure
1. MATLAB was opened and transfer functions representing stable, unstable, and marginally stable systems were defined.  
2. Poles and zeros of each system were obtained using MATLAB functions.  
3. Pole–zero plots were generated to identify the location of poles in the s-plane.  
4. Step responses were plotted to verify the stability characteristics of each system.  
5. The relationship between pole location and system stability was analysed.

---

### Inference
Systems with all poles in the left half plane are stable and settle to a finite steady-state value. Systems with poles in the right half plane are unstable and their outputs grow without bound. Marginally stable systems have poles on the imaginary axis and exhibit sustained oscillations. Pole–zero plots provide a clear and direct method for predicting system stability.

---

### Result
The stability of different systems was successfully analysed using pole–zero plots and step response analysis. Stable, unstable, and marginally stable behaviours were clearly identified, confirming that system stability depends entirely on the location of poles in the s-plane.

