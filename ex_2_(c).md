# Two-Mass Spring–Damper System (MATLAB → Simulink)

---

## Question Statement

Build the Simulink block diagram of a **two-mass spring–damper mechanical system** using **MATLAB code**, such that:

- The entire Simulink model is generated programmatically
- All parameters are defined and controlled from MATLAB
- No manual Simulink drawing is used
- Impulse force is applied as input
- Displacements of both masses are observed as outputs

---

## MATLAB Code

```matlab
clc; clear; close all;

%% Parameters
B  = -0.3;     % Damper coefficient
k1 = 0.5;      % Spring constant
k12 = 0.5;     % Coupling spring
B2 = 0.1;      % Coupling damper
M1 = 1;        % Mass 1
M2 = 3;        % Mass 2

Tstop = '10';

model = 'Two_Mass_Spring_Damper';
new_system(model);
open_system(model);

%% ---------- MASS 1 ----------

add_block('simulink/Math Operations/Gain',[model '/B'],...
    'Gain','B','Position',[40 40 80 70]);

add_block('simulink/Math Operations/Gain',[model '/k1'],...
    'Gain','k1','Position',[40 90 80 120]);

add_block('simulink/Math Operations/Gain',[model '/k12_1'],...
    'Gain','k12','Position',[40 160 80 190]);

add_block('simulink/Math Operations/Sum',[model '/Sum1'],...
    'Inputs','+-','Position',[120 80 150 120]);

add_block('simulink/Math Operations/Sum',[model '/Sum2'],...
    'Inputs','++','Position',[190 90 220 120]);

add_block('simulink/Math Operations/Gain',[model '/1_M1'],...
    'Gain','1/M1','Position',[250 90 300 120]);

add_block('simulink/Continuous/Integrator',[model '/v1'],...
    'Position',[330 90 360 120]);

add_block('simulink/Continuous/Integrator',[model '/x1'],...
    'Position',[390 90 420 120]);

add_block('simulink/Sinks/Scope',[model '/Scope1'],...
    'Position',[460 90 490 120]);

%% ---------- MASS 2 ----------

add_block('simulink/Sources/Discrete Impulse',[model '/Impulse'],...
    'Position',[40 280 80 310]);

add_block('simulink/Math Operations/Gain',[model '/k12_2'],...
    'Gain','k12','Position',[40 340 80 370]);

add_block('simulink/Math Operations/Gain',[model '/B2'],...
    'Gain','B2','Position',[40 390 80 420]);

add_block('simulink/Math Operations/Sum',[model '/Sum3'],...
    'Inputs','+-','Position',[120 310 150 350]);

add_block('simulink/Math Operations/Gain',[model '/1_M2'],...
    'Gain','1/M2','Position',[190 320 240 350]);

add_block('simulink/Continuous/Integrator',[model '/v2'],...
    'Position',[270 320 300 350]);

add_block('simulink/Continuous/Integrator',[model '/x2'],...
    'Position',[330 320 360 350]);

add_block('simulink/Sinks/Scope',[model '/Scope2'],...
    'Position',[400 320 430 350]);

%% ---------- Difference (x2 - x1) ----------

add_block('simulink/Math Operations/Sum',[model '/x2_minus_x1'],...
    'Inputs','+-','Position',[250 210 280 240]);

%% ---------- Connections (Mass 1) ----------

add_line(model,'x1/1','B/1');
add_line(model,'x1/1','k1/1');
add_line(model,'B/1','Sum1/1');
add_line(model,'k1/1','Sum1/2');
add_line(model,'Sum1/1','Sum2/1');
add_line(model,'k12_1/1','Sum2/2');
add_line(model,'Sum2/1','1_M1/1');
add_line(model,'1_M1/1','v1/1');
add_line(model,'v1/1','x1/1');
add_line(model,'x1/1','Scope1/1');

%% ---------- Connections (Coupling) ----------

add_line(model,'x2/1','x2_minus_x1/1');
add_line(model,'x1/1','x2_minus_x1/2');
add_line(model,'x2_minus_x1/1','k12_1/1');
add_line(model,'x2_minus_x1/1','k12_2/1');

%% ---------- Connections (Mass 2) ----------

add_line(model,'Impulse/1','Sum3/1');
add_line(model,'k12_2/1','Sum3/2');
add_line(model,'Sum3/1','1_M2/1');
add_line(model,'1_M2/1','v2/1');
add_line(model,'v2/1','x2/1');
add_line(model,'x2/1','Scope2/1');

%% ---------- Simulation ----------
set_param(model,'StopTime',Tstop);
```

---

## How to Run

1. Open MATLAB
2. Copy the code into a `.m` file
3. Run the script
4. Simulink model opens automatically
5. Click **Run** to simulate

---

## Author

**Sabari Poornesh S**  
B.Tech – Automation & Robotics Engineering  
Amrita Vishwa Vidyapeetham, Coimbatore

