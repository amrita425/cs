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
