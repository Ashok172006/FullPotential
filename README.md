# FullPotential
## Drive Node for Autonomous Rover
This is a Python script that implements a drive node for an autonomous rover using ROS (Robot Operating System). The node receives joystick input, encoder data, and motion commands, and sends PWM (Pulse Width Modulation) signals to the rover's motors.
### Class Drive
The node is **subscribed** to 'joy' and 'encoder' topics. publishing to 'motor_rpm' topic.


