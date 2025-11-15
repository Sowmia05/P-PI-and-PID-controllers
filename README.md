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
num=[1]
den=[1 10 20]
sys=tf(num,den)
subplot(2,2,1)
step(sys)
title('open loop system')


### With P-Controller
Kp=300;
c1=pid(Kp)
G1=feedback(c1*sys,1)
subplot(2,2,2)
step(G1)
title('P-CONTROLLER')

### With PI Controller
Kp=30;
Ki=70;
c2=pid(Kp,Ki)
G2=feedback(c2*sys,1)
subplot(2,2,3)
step(G2)
title('Pi-CONTROLLER')

### With PID Controller
Kp=350;
Ki=300;
Kd=50;
c3=pid(Kp,Ki,Kd)
G3=feedback(c3*sys,1)
subplot(2,2,4)
step(G3)
title('Pid-CONTROLLER')

## Output: 
### Without Controller (Open loop System)
<img width="884" height="426" alt="image" src="https://github.com/user-attachments/assets/f9f197f3-1b18-438a-85d5-661f434c5377" />


### With P-Controller
<img width="915" height="443" alt="image" src="https://github.com/user-attachments/assets/7d9b5471-78cd-494f-8e56-fa7912250b2c" />

### With PI Controller
<img width="835" height="433" alt="image" src="https://github.com/user-attachments/assets/d4944ea3-15d5-4dae-baf6-e0a7a7efccf5" />

### With PID Controller
<img width="815" height="420" alt="image" src="https://github.com/user-attachments/assets/93a79b8a-6dc0-49f7-8a7c-2b99603af0c2" />


## Result:
Thus the P, PI and PID controllers for the given system was analysed and the following conclusions were arrived using MATLAB. <br>
### With-out controller 
Delay time =   0.458
Rise time =0.999   
Peak time = 1.56          
Settling time = 1.96          
Steady State Error =0        
### With P Controller 
Delay time =0.0887         <br>
Rise time = 0.16           <br>
Peak time = 0.19      <br>
Settling time = 1.1          <br>
Steady State Error =0.1        <br>
### With PI Controller 
Delay time =0.303         <br>
Rise time = 0.649       <br>
Peak time = 0.82     <br>
Settling time = 1.87           <br>
Steady State Error = 0.87       <br>
### With PID Controller 
Delay time = 0.0243        <br>
Rise time =  0.0615     <br>
Peak time =  1.04   <br>
Settling time =0.0882          <br>
Steady State Error = 0.018       <br>




