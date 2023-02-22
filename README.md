# ESC Simulation
## An LTSpice simulation of an Electric Speed Controller.

This repository contains a simulation of a basic electronic speed controller
for a brushless DC motor. 

An ESC is a crucial component in devices such as drones or RC cars. It takes a DC voltage(11.1V in this project, imitating a 3-cell LiPo battery) and turns it into a 3-phase voltage using power FETs. 

I was inspired to make this circuit from this tutorial: https://howtomechatronics.com/how-it-works/how-brushless-motor-and-esc-work/.

So far, I have managed to create a functional 3-phase voltage generator using basic logic gates and a synchronous clock to trigger the 6 states needed for the driver. However, there are some factors that still need to be implemented:
- No back EMF detection: Back EMF is used in commercial ESCs to detect the motor's position. This is a very hard task to implement in LTSpice, as my motor model is just 3 coils winded up together.
- Inductive kickback reduction: A must before this circuit is implemented in real life. At this time, triggering the motors create very high impedance spikes of up to 30 Amperes, which is way too much.

Here are some pictures of this circuit:
- First, I generated a synchronous clock for the gate logic. This circuit needed only 6 states, so additional reset logic was added.
<img src="https://github.com/constlo/ESC/blob/master/6_state_clock.png"></img>

- Then I created the gate logic for the FETs.
<img src="https://github.com/constlo/ESC/blob/master/gate_logic.png"></img>

- The FET driver takes the input from the gate logic, and is multiplied by a separate PWM signal. Here, the duty cycle is 50%. However, I plan to use a microcontroller in the physical model to control the PWM.
<img src="https://github.com/constlo/ESC/blob/master/fet_drivers.png"></img>

- And Finally, the motor model, which is just a simple 6-coil setup used to imitate the real-life motor.
<img src="https://github.com/constlo/ESC/blob/master/motor_model.png"></img>

Here is the output of my ESC. As seen in the image, 3 different phases of PWM singal is created.

<img src="https://github.com/constlo/ESC/blob/master/motor_phases.png"></img>
