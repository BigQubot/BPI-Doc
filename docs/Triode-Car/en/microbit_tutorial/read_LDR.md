# Collect the signals

## Example Blocks

<div align=center>
<img src="../assets/Triode-car_read_LDR.png" width="600"/>
</div>

[Example project file on Github](https://github.com/Wind-stormger/Makecode/blob/master/microbit-Triode-car_read_LDR.hex)

> After the project file is downloaded locally, it can be imported into MakeCode for viewing and re-editing, or it can be burned directly to micro:bit via USB to run. 

## Design description 

1. The voltage analog values of the two sensors are sent to the computer through the USB serial port every 100ms. 
2. You can open the console in MakeCode to view the information received in real time. 

Refer to [](../hardware/analysis&calibrate.html).

The "Read (index) line tracking sensor" block in Triode-Car extensions can collect analog values from the photoresistors.

Micro: bit pins' voltage can be set from 0~3.3v, and has 1024(10bit) precision levels, therefore, the "read left/right line tracking sensor" block will input an analog value to adjust its voltage ranging from 0~1023.