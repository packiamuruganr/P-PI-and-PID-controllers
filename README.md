# Analysis of P, PI and PID Controllers using MATLAB
## Aim:
To analyse the effect of P, PI and PID controllers for the system having open loop transfer function, G(S)=1/(S^2+10S+20) using MATLAB. 
## Apparatus Required:
Computer with MATLAB software

## Theory:
	A controller is a device introduced in the system to modify the error signal and to produce a control signal. 
	The way the controller produces the control signal is called the control action.

Consider the following unity feedback system,
 <img width="823" height="281" alt="image" src="https://github.com/user-attachments/assets/36e49512-cf47-4fec-b00c-f79dc0af1c5f" />

### Proportional (P) Controller:
The proportional controller produces an output, which is proportional to error signal.<br>
u(t)∝e(t) <br>
⇒u(t)=Kpe(t) <br>
Apply Laplace transform on both the sides - <br>
U(s)=KpE(s) <br>
U(s)/E(s)=Kp <br>
Therefore, the transfer function of the proportional controller is Kp.

### Proportional Integral (PI) Controller:
The proportional integral controller produces an output, which is the combination of outputs of the proportional and integral controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s)E(s) <br>
U(s)/E(s)=Kp+Ki/s <br>
Therefore, the transfer function of proportional integral controller is Kp+Kis. <br>

### Proportional Integral Derivative (PID) Controller:
The proportional integral derivative controller produces an output, which is the combination of the outputs of proportional, integral and derivative controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt+ Kd (de(t)/dt) <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s+Kds)E(s) <br>
U(s)/E(s)=Kp+Ki/s+Kd s <br>
Therefore, the transfer function of the proportional integral derivative controller is Kp+Ki/s+Kd s

### Characteristics of Kp, Ki and Kd terms:

Increasing the proportional gain ( ) has the effect of proportionally increasing the control signal for the same level of error. The fact that the controller will "push" harder for a given level of error tends to cause the closed-loop system to react more quickly, but also to overshoot more. Another effect of increasing   is that it tends to reduce, but not eliminate, the steady-state error.
The addition of a derivative term to the controller ( ) adds the ability of the controller to "anticipate" error. With derivative control, the control signal can become large if the error begins sloping upward, even while the magnitude of the error is still relatively small. This anticipation tends to add damping to the system, thereby decreasing overshoot. The addition of a derivative term, however, has no effect on the steady-state error.
The addition of an integral term to the controller ( ) tends to help reduce steady-state error. If there is a persistent, steady error, the integrator builds and builds, thereby increasing the control signal and driving the error down. 
 


## Procedure:
	Open MATLAB software
	Open a new script file.
	Type the program.
	Save and Execute the program.
	Determine the steady state error and analyse the controllers.
## Program: 
### Without Controller (Open loop System)
```
num=[1];
den=[1 10 20];
sys=tf(num,den);
subplot(2,2,1)
step(sys)
title('open loop system')
```



### With P-Controller
```
kp=300;
c1=pid(kp)
g1=feedback(c1*sys,1)
subplot(2,2,2)
step(g1)
title('p-controller')
```



### With PI Controller
```
kp=30;
ki=70;
c2=pid(kp,ki)
g2=feedback(c2*sys,1)
subplot(2,2,3)
step(g2)
title('pi-controller')
```

### With PID Controller
```
kp=350;
ki=300;
kd=50;
c3=pid(kp,ki,kd)
g3=feedback(c3*sys,1)
subplot(2,2,4)
step(g3)
title('pid controller')
```

## Output: 
### Without Controller (Open loop System)

<img width="852" height="428" alt="Screenshot 2025-11-01 135941" src="https://github.com/user-attachments/assets/f6d30325-fef3-42ae-8f7a-2b08ae2e310d" />

### With P-Controller

<img width="846" height="457" alt="Screenshot 2025-11-01 140001" src="https://github.com/user-attachments/assets/c34c76b9-be01-4fd9-865f-592bfc2e91d6" />




### With PI Controller

<img width="759" height="434" alt="Screenshot 2025-11-01 140007" src="https://github.com/user-attachments/assets/b462b9a6-90ba-4e81-ae1c-5b0b99d31102" />


### With PID Controller

<img width="842" height="414" alt="Screenshot 2025-11-01 140015" src="https://github.com/user-attachments/assets/e1cb9f16-e2c4-4529-b8a9-54d64d165638" />



## Result:
Thus the P, PI and PID controllers for the given system was analysed and the following conclusions were arrived using MATLAB. <br>
### With-out controller 
Delay time = 0.95       <br>
Rise time = -         <br>
Peak time = -        <br>
Settling time = 2.52           <br>
Steady State Error = 1.99       <br>
### With P Controller 
Delay time = 0.0684        <br>
Rise time = 0.109          <br>
Peak time = 0.18          <br>
Settling time = 1.19          <br>
Steady State Error = 0.4      <br>
### With PI Controller 
Delay time = 0.263       <br>
Rise time = 0.67             <br>
Peak time = 0.819       <br>
Settling time = 2.74           <br>
Steady State Error = 2.5    <br>
### With PID Controller 
Delay time = 0.0142     <br>
Rise time = 1.97          <br>
Peak time = 2         <br>
Settling time = -          <br>
Steady State Error = 1      <br>




