# FullPotential
## Drive Node for Autonomous Rover
This is a Python script that implements a drive node for an autonomous rover using ROS (Robot Operating System). The node receives joystick input, encoder data, and motion commands, and sends PWM (Pulse Width Modulation) signals to the rover's motors.
## Initialization
### Class Drive
* Initializes the ROS node drive_arc.
* The node is **subscribed** to 'joy' and 'encoder' topics. publishing to 'motor_rpm' topic.
#### Variable used:
 * __self.modeupbtn__ and __self.modednbtn__ : They are used to increment and decrement the pwm values respectively.
 * __self.rotinplace_btn__ : This is a variable(button) responsible for rotating the rover in one place.I have mentioned in breif about this below in the function it is used.
 * __self.steer_unlock_axis__ : This variable is used to unlock the steering control. When the joystick axis with index 4 is manipulated, it toggles the lock state of the steering. This means that the user can enable or disable manual control of the steering.
 * 

#### enc_Callback function() ->
 * The enc_callback function in the code is responsible for processing encoder data received from the rover's wheels.
 * It receives Encoder Data and updates the current encoder readings (enc_data) with the new data.

#### joycallback()->
 * The modeupbtn and modednbtn variables serve as indices in the d_arr array. As the index increases, the corresponding PWM (Pulse Width Modulation) value also increases. Essentially, the code adjusts the self.mode 
  variable based on user interactions, incrementing or decrementing it to change the rover's speed.
 * It is responsible for handling incoming messages on a specific topic. When a message is received, the callback function processes it, updates internal state and variables There are actually two modes to run a rover. One is Steering and other is Full Potential Depending the incoming message. 
#### steer function() -> 
has 2 modes, mode = 0(for relative steer) and mode = 1(for absolute steer,doesnt depend upon initial angle value and steers to final angle value)
the **pwm** values for each of the 4 wheels is decided by the proportional factor in PID.
 
#### steering()->
 > for all these corresponding conditions, data from joycallback is used.
#### if both steering and full potential is locked (this aquires data from joycallback under this same condition) and
* if forward button is pressed then wheels steer to absolute 0 degree position, since mode==1.
* if parallel button is pressed then wheels are turned to a 90 degree absolute position as mode==1.
* if rotinplace button is pressed then 
*  
#### if steering is unlocked and fullpotential is locked
* and forward button is pressed then we get the current wheel angle from encode callback and use it as initial angle and then turn it 45 degrees relatively clockwise w.r.t to initial angle since mode==0.
* if parallel button is pressed same happens except in anticlockwise.
* if samedir axis value isnt 0 and oppdir value is less than threshold then all wheels rotate with same direction and speed.
* if oppdir value isnt 0 and samedir < threshold then fron wheels and back wheels rotate in opposite direction.
if steering is locked and full potential unlocked u can control each wheel individually with different speeds based on the value of each wheel axes.


