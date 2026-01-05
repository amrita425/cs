# MATLAB Control Systems Lab  
## Exercises 03 – 05


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

K = 28;  
T = 28*2; 
n=K;
d = [T 1]; 
g = tf(n,d); 
disp('The Transfer Function G(s) is:'); 

g
figure; 
step(g); 
title(['Step Response for K = ', num2str(K), ' and T = ', num2str(T)]);

grid on; 
ylabel('Amplitude'); 
xlabel('Time (sec)');
```

---

## 3.2 Effect of Gain (K)
```matlab
clc; clear; close all;

T = 20;
K_values = [10 28 80];    % do each value or all-in-one go

figure; hold on;
for K = K_values
    g = tf(K,[T 1]);
    step(g);
end

grid on;
legend('Low Gain','Nominal Gain','High Gain');    % remove this if you are doing one-by-one
xlabel('Time (sec)');
ylabel('Amplitude');
title('Effect of Gain on First-Order System');
```

## 3.3 Effect of Time Constant (T)
```matlab
clc; clear; close all;

K = 28;                     % Gain
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

## 3.4 Stability Analysis of First-Order System (stable)
```matlab
clc; clear; close all; 

K = 20;  
T = 20*2; 
n=K;
d = [T 1]; 
g = tf(n,d); 
disp('The Transfer Function G(s) is:'); 

g
figure; 
step(g); 
title(['Step Response for K = ', num2str(K), ' and T = ', num2str(T)]); 
grid on; 
ylabel('Amplitude'); 
xlabel('Time (sec)');
```

## 3.4 Stability Analysis of First-Order System (unstable)
```matlab
clc; clear; close all; 

K = 20;  
T = 20*2; 
n=K;
d = [-T 1]; 
g = tf(n,d); 
disp('The Transfer Function G(s) is:'); 

g
figure; 
step(g); 
title(['Step Response for K = ', num2str(K), ' and T = ', num2str(T)]); 
grid on; 
ylabel('Amplitude'); 
xlabel('Time (sec)');
```



## 4.0 Basic code
```matlab
clc, clear, close all;

k = 28;
z = 0;
Wn = 28;

n = k;
d = [1 2*z*Wn Wn^2];

g = tf(n, d);
step(g, 10)
```

## 4.1 Nominal Second-Order System
```matlab
clc; clear; close all;

K = 28;        % System Gain
zeta = 0;      % Damping ratio
Wn = 28;       % Natural frequency (rad/s)

g = tf(K,[1 2*zeta*Wn Wn^2]);

step(g,10);
grid on;
xlabel('Time (sec)');
ylabel('Amplitude');
title('Nominal Second-Order System Step Response');
```

## 4.2 Effect of Damping Ratio (ζ)
```matlab
clc; clear; close all;

K = 28;             % System Gain
Wn = 28;            % Natural Frequency
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

K = 28;             % System gain
zeta = 0.5;         % Damping ratio
Wn_values = [10 28 80];  % Natural frequencies to compare

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

## 4.4 (a) Stable System
```matlab
clc, clear, close all;

k = 28;
z = 0;
Wn = 28;

n = k;
d=[1 2*z*wn wn^2];

g = tf(n, d);
step(g, 10)
```

## 4.4 (b) Unstable System
```matlab
clc, clear, close all;

k = 28;
z = 0;
Wn = 28;

n = k;
d =[1 -2*z*wn wn^2];;

g = tf(n, d);
step(g, 10)
```


## 5.1 Stable System
```matlab
clear; clc; close all;

k = 28;
n1 = [k 5];
n2 = [2];
n12 = conv(n1, n2);

d1 = [1 2];
d2 = [1 15];
d12 = conv(d1, d2);

g = tf(n12, d12);

figure(1);
step(g);
xlabel('Time (sec)');
ylabel('Amplitude');
title('Step Response – Stable System');

figure(2);
pzplot(g);
title('Pole-Zero Plot – Stable System');
```

## 5.2 Unstable System
```matlab
clear; clc; close all;

k = 28;
n1 = [k 5];
n2 = [2];
n12 = conv(n1, n2);

d1 = [1 2];
d2 = [1 -15];
d12 = conv(d1, d2);

g = tf(n12, d12);

figure(1);
step(g);
xlabel('Time (sec)');
ylabel('Amplitude');
title('Step Response – Unstable System');

figure(2);
pzplot(g);
title('Pole-Zero Plot – Unstable System');
```

## 5.3 Marginally Stable System
```matlab
clear; clc; close all;

k = 28;
n1 = [k 5];
n2 = [2];
n12 = conv(n1, n2);

d12 = [1 0 k];
g = tf(n12, d12);

figure(1);
step(g);
xlabel('Time (sec)');
ylabel('Amplitude');
title('Step Response – Marginally Stable System');

figure(2);
pzplot(g);
title('Pole-Zero Plot – Marginally Stable System');

```
