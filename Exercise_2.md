# Mechanical Translational System – MATLAB & Simulink (Programmatic Implementation)

---

## Question Statement

Implement and simulate the following **mechanical translational systems** using **MATLAB code** such that the **Simulink block diagram is generated automatically**.  
All system parameters must be defined in MATLAB, and the Simulink model should update automatically when parameter values are changed.

Systems to be implemented:
1. Mass only system  
2. Mass + Damper system  
3. Mass + Damper + Spring system

Impulse force is to be applied as the input, and displacement is to be observed as the output.

---

## 1. Mass Only System

### MATLAB Code
```matlab
clc; clear; close all;

m = 4;              % Mass (kg)
Tstop = '10';

model = 'Mass_System';
new_system(model); open_system(model);

add_block('simulink/Sources/Impulse',[model '/Force'],...
    'Position',[30 80 60 110]);

add_block('simulink/Math Operations/Gain',[model '/1_over_m'],...
    'Gain','1/m','Position',[110 80 160 110]);

add_block('simulink/Continuous/Integrator',[model '/Integrator1'],...
    'Position',[210 80 240 110]);

add_block('simulink/Continuous/Integrator',[model '/Integrator2'],...
    'Position',[290 80 320 110]);

add_block('simulink/Sinks/Scope',[model '/Scope'],...
    'Position',[360 80 390 110]);

add_line(model,'Force/1','1_over_m/1');
add_line(model,'1_over_m/1','Integrator1/1');
add_line(model,'Integrator1/1','Integrator2/1');
add_line(model,'Integrator2/1','Scope/1');

set_param(model,'StopTime',Tstop);
```

---

## 2. Mass + Damper System

### MATLAB Code
```matlab
clc; clear; close all;

m = 4;              % Mass (kg)
b = 6;              % Damping coefficient (Ns/m)
Tstop = '10';

model = 'Mass_Damper_System';
new_system(model); open_system(model);

add_block('simulink/Sources/Impulse',[model '/Force'],...
    'Position',[30 80 60 110]);

add_block('simulink/Math Operations/Sum',[model '/Sum'],...
    'Inputs','+-','Position',[100 80 120 110]);

add_block('simulink/Math Operations/Gain',[model '/1_over_m'],...
    'Gain','1/m','Position',[150 80 200 110]);

add_block('simulink/Continuous/Integrator',[model '/Integrator_v'],...
    'Position',[240 80 270 110]);

add_block('simulink/Continuous/Integrator',[model '/Integrator_x'],...
    'Position',[310 80 340 110]);

add_block('simulink/Math Operations/Gain',[model '/Damper'],...
    'Gain','b','Position',[240 140 270 170]);

add_block('simulink/Sinks/Scope',[model '/Scope'],...
    'Position',[380 80 410 110]);

add_line(model,'Force/1','Sum/1');
add_line(model,'Integrator_v/1','Damper/1');
add_line(model,'Damper/1','Sum/2');
add_line(model,'Sum/1','1_over_m/1');
add_line(model,'1_over_m/1','Integrator_v/1');
add_line(model,'Integrator_v/1','Integrator_x/1');
add_line(model,'Integrator_x/1','Scope/1');

set_param(model,'StopTime',Tstop);
```

---

## 3. Mass + Damper + Spring System

### MATLAB Code
```matlab
clc; clear; close all;

m = 4;              % Mass (kg)
b = 6;              % Damping coefficient (Ns/m)
k = 0.3;            % Spring constant (N/m)
Tstop = '10';

model = 'Mass_Damper_Spring_System';
new_system(model); open_system(model);

add_block('simulink/Sources/Impulse',[model '/Force'],...
    'Position',[30 80 60 110]);

add_block('simulink/Math Operations/Sum',[model '/Sum'],...
    'Inputs','+--','Position',[100 80 130 120]);

add_block('simulink/Math Operations/Gain',[model '/1_over_m'],...
    'Gain','1/m','Position',[160 90 210 120]);

add_block('simulink/Continuous/Integrator',[model '/Integrator_v'],...
    'Position',[250 90 280 120]);

add_block('simulink/Continuous/Integrator',[model '/Integrator_x'],...
    'Position',[320 90 350 120]);

add_block('simulink/Math Operations/Gain',[model '/Damper'],...
    'Gain','b','Position',[250 150 280 180]);

add_block('simulink/Math Operations/Gain',[model '/Spring'],...
    'Gain','k','Position',[320 150 350 180]);

add_block('simulink/Sinks/Scope',[model '/Scope'],...
    'Position',[400 90 430 120]);

add_line(model,'Force/1','Sum/1');
add_line(model,'Integrator_v/1','Damper/1');
add_line(model,'Damper/1','Sum/2');
add_line(model,'Integrator_x/1','Spring/1');
add_line(model,'Spring/1','Sum/3');
add_line(model,'Sum/1','1_over_m/1');
add_line(model,'1_over_m/1','Integrator_v/1');
add_line(model,'Integrator_v/1','Integrator_x/1');
add_line(model,'Integrator_x/1','Scope/1');

set_param(model,'StopTime',Tstop);
```

---

**Author:** Sabari Poornesh S

