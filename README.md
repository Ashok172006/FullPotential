# FullPotential
## Drive Node for Autonomous Rover
This is a Python script that implements a drive node for an autonomous rover using ROS (Robot Operating System). The node receives joystick input, encoder data, and motion commands, and sends PWM (Pulse Width Modulation) signals to the rover's motors.
### Class Drive
The node is **subscribed** to 'joy' and 'encoder' topics. publishing to 'motor_rpm' topic.
#### Variable used:
 * modeupbtn and modednbtn are used to increment and decrement the pwm values respectively.
#### steer function() -> 
has 2 modes, mode = 0(for relative steer) and mode = 1(for absolute steer,doesnt depend upon initial angle value and steers to final angle value)
the **pwm** values for each of the 4 wheels is decided by the proportional factor in PID.
#### joycallback()->
 * modeupbtn and modednbtn are used as indices in d_arr, higher the index higher the pwm value.
 *  
#### steering()->
if both steering and full potential is locked (this aquires data from joycallback under this same condition) and
* if forward button is pressed then wheels steer to absolute 0 degree position, since mode==1.
* if parallel button is pressed then wheels are turned to a 90 degree absolute position as mode==1.
* if rotinplace button is pressed
*  
if steering is unlocked and fullpotential is locked
* 
