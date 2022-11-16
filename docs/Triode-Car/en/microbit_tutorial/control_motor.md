# Use buttons to control the motors

## Example Blocks 

<div align=center>
<img src="../assets/Triode-Car_motor_control_1.png" width="300"/>
</div>

[Example project file on Github](https://github.com/Wind-stormger/Makecode/blob/master/microbit-Triode-car_motor_control_1.hex)

> After the project file is downloaded locally, it can be imported into MakeCode for viewing and re-editing, or it can be burned directly to micro:bit via USB to run. 

## Design description 

1. Stop when starting or resetting. 
2. Press the button A and B  at the same time to go straight.
3. Press button A to turn right. 
4. Press the button B to turn left. 

In[Hardware analysis and calibration: Drive circuit](../hardware/analysis&calibrate.html#Drive-circuit),There is a switch in the drive circuit, which can switch the drive circuit from LM393 voltage comparator control to micro:bit control. The micro:bit control method of the drive circuit is the same as the LM393 voltage comparator, starting at low level and stopping at high level. 