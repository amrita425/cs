# MATLAB Control Systems Lab  
## Exercises 03 – 05

This repository contains **section-wise MATLAB programs** for Control Systems Laboratory experiments **3 to 5**, with only the **required formulas and executable code blocks**.

✔ MATLAB 2024 compatible  
✔ Exercise-wise and section-wise  
✔ Clean copy–paste code  
✔ Record + Viva oriented  

---

# EXERCISE 03  
## Time Domain Response of a First-Order System

### System Model
\[
G(s) = \frac{K}{Ts + 1}
\]

Pole:
\[
s = -\frac{1}{T}
\]

---

## 3.1 Basic Step Response
```matlab
clc; clear; close all;

K = 40;
T = 80;

n = K;
d = [T 1];

g = tf(n,d);
g

figure;
step(g);
grid on;
xlabel('Time (sec)');
ylabel('Amplitude');
title('Step Response of First-Order System');
```

---

## 3.2 Effect of Gain (K)
```matlab
clc; clear; close all;

T = 20;
K_values = [10 40 80];

figure; hold on;
for K = K_values
    g = tf(K,[T 1]);
    step(g);
end

grid on;
legend('Low Gain','Nominal Gain','High Gain');
xlabel('Time (sec)');
ylabel('Amplitude');
title('Effect of Gain on First-Order System');
```

## 3.3 Effect of Time Constant (T)
```matlab
clc; clear; close all;

K = 40;                     % Gain
T_values = [5 20 60];       % Low, Nominal, High time constants

figure; hold on;
for T = T_values
    g = tf(K,[T 1]);
    step(g);
end

grid on;
legend('Low T','Nominal T','High T');
xlabel('Time (sec)');
ylabel('Amplitude');
title('Effect of Time Constant on First-Order System');
```

## 3.4 Stability Analysis of First-Order System
```matlab
clc; clear;

% Define Gain and Time Constant
K = 40;
T = 20;

% Create Transfer Function
g = tf(K,[T 1]);

% Compute Poles
p = pole(g);
disp('Pole of the First-Order System:');
disp(p);
```

## 4.1 Nominal Second-Order System
```matlab
clc; clear; close all;

% Parameters
K = 40;        % System Gain
zeta = 0;      % Damping ratio
Wn = 40;       % Natural frequency (rad/s)

% Transfer Function
g = tf(K,[1 2*zeta*Wn Wn^2]);

% Step Response
step(g,10);
grid on;
xlabel('Time (sec)');
ylabel('Amplitude');
title('Nominal Second-Order System Step Response');
```

## 4.2 Effect of Damping Ratio (ζ)
```matlab
clc; clear; close all;

K = 40;             % System Gain
Wn = 40;            % Natural Frequency
zeta_values = [0 0.5 1 1.5];  % Damping Ratios: Undamped, Underdamped, Critically Damped, Overdamped

figure; hold on;
for zeta = zeta_values
    g = tf(K,[1 2*zeta*Wn Wn^2]);
    step(g,10);
end

grid on;
legend('Undamped (\zeta=0)','Underdamped (\zeta=0.5)','Critically Damped (\zeta=1)','Overdamped (\zeta=1.5)');
xlabel('Time (sec)');
ylabel('Amplitude');
title('Effect of Damping Ratio on Second-Order System');
```
## 4.3 Effect of Natural Frequency (ωₙ)
```matlab
clc; clear; close all;

K = 40;             % System gain
zeta = 0.5;         % Damping ratio
Wn_values = [10 40 80];  % Natural frequencies to compare

figure; hold on;
for Wn = Wn_values
    g = tf(K,[1 2*zeta*Wn Wn^2]);
    step(g,10);     % Simulate step response for 10 seconds
end

grid on;
legend('Low ω_n','Nominal ω_n','High ω_n');
xlabel('Time (sec)');
ylabel('Amplitude');
title('Effect of Natural Frequency on Second-Order System');
```


