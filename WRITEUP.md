# Writeup: Building a Controller #

![img.png](img/controller_design.png)

## Implemented Controller


### Implemented body rate control  

I completed the `QuadControl::BodyRateControl` method 
to implement this functionality.
Also, I configured a value for the angle rate gain parameter (`kpPQR`)
in the `QuadControlParams.txt` file.

This P-controller produces desired moments for the
roll, pitch, and yaw axes.
My implementation is based on the following expression:

![img.png](img/body_rate_controller.png)

Here, u<sub>p</sub>, u<sub>q</sub>, and u<sub>r</sub> are 
rotational accelerations along each axis.

### Implement roll pitch control 

I completed the `QuadControl::RollPitchControl` method
to implement this functionality.
Also, I configured a value for the roll/pitch gain parameter (`kpBank`)
in the `QuadControlParams.txt` file.

This P-controller produces pitch rate (q<sub>c</sub>) and roll rate (p<sub>c</sub>) .
My implementation is based on the following expression:

![img.png](img/roll_pitch_control.png)

The variable `desiredRollRate` inside the method stores
the calculated value of p<sub>c</sub>, and the `desiredPitchRate`
stores the value of q<sub>c</sub>.

### Implement altitude controller 

I completed the `QuadControl::AltitudeControl` method
to implement this functionality.
Also, I configured values for gain parameter (`kpPosZ`, `KiPosZ`, and `kpVelZ`)
in the `QuadControlParams.txt` file.

This PID-controller produces  a collective thrust command.
My implementation is based on the following expression:

![img.png](img/altitude_controller.png)

Here, u<sub>l</sub> controls vertical acceleration.
The variable `desiredAcceleration` inside the method stores
the calculated value of first u<sub>l</sub> and later
of c.

### Implement lateral position control 

I completed the `QuadControl::LateralPositionControl` method
to implement this functionality.
Also, I configured values for gain parameter (`kpPosXY` and `kpVelXY`)
in the `QuadControlParams.txt` file.

This PD-controller produces the desired horizontal
accelerations.
For the x direction, my implementation is based on the 
following expression:

![img.png](img/lateral_position_controller.png)

We use an analogous expression for the y direction.


### Implement yaw control 
I completed the `QuadControl::YawControl` method
to implement this functionality.
Also, I configured a value for the yaw control gain parameter (`kpYaw`)
in the `QuadControlParams.txt` file.

This P-controller produces the desired yaw rate (r<sub>c</sub>).
My implementation is based on the following expression:

![img.png](img/yaw_controller.png)

The variable `desiredYawRate` inside the method stores
the calculated value of r<sub>c</sub>.

### Calculating the motor commands

I completed the `QuadControl::GenerateMotorCommands` method
to implement this functionality.

This function produces a motor command for each motor.
My implementation is based on the following expressions:

![img.png](img/motor_commands_1.png)

And

![img.png](img/motor_commands_2.png)


## Flight Evaluation


### Scenario 1: Introduction  

![img.png](img/scenario_1.png)

### Scenario 2: Body rate and roll/pitch control  

![img.png](img/scenario_2.png)

### Scenario 3: Position/velocity and yaw angle control

![img.png](img/scenario_3.png)

### Scenario 4: Non-idealities and robustness   

![img_1.png](img/scenario_4.png)
