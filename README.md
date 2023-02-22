# ESC Simulation
## An LTSpice of an Electric Speed Controller.

This repository contains a simulation of a basic electronic speed controller
for a brushless DC motor. 

An ESC is a crucial component in devices such as drones or RC cars. It takes a DC voltage(11.1V in this project, imitating a 3-cell LiPo battery) and turns it into a 3-phase voltage using power FETs. 

I was inspired to make this circuit from this tutorial: https://howtomechatronics.com/how-it-works/how-brushless-motor-and-esc-work/.

So far, I have managed to create a functional 3-phase voltage generator using basic logic gates and a synchronous clock to trigger the 6 states needed for the driver. However, there are some factors that still need to be implemented:
- No back EMF detection: Back EMF is used in commercial ESCs to detect the motor's position. This is a very hard task to implement in LTSpice, as my motor model is just 3 coils winded up together.
- Inductive kickback reduction: A must before this circuit is implemented in real life. At this time, triggering the motors create very high impedance spikes of up to 30 Amperes, which is way too much.

Here is my motor model, using 100uH coils.
<img src="https://github.com/constlo/ESC/blob/master/motor_model.png"></img>
