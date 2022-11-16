# Control the motors by Bluetooth

## Introduce 

The bluetooth feature can be enabled through MakeCode extensions, we can control the micro: bit with our smartphones through certain applications.

* iOS users:[Micro:bit App on App Store](https://apps.apple.com/cn/app/micro-bit/id1092687276)

* Android users:[Microbit-blue GitHub link](https://github.com/microbit-foundation/microbit-blue/raw/master/releases/ble_demo_v1_5_4.apk)&[Kitronik Move on Google Play Store](https://play.google.com/store/apps/details?id=com.kitronik.blemove) 

> There is an official release of the Micro: bit App on both the iOS App Store and Android's Google Play Store, however, the iOS version has support for bluetooth connection, whereas the Google Play store's does not. This is why we require third party apps on Android devices that supports bluetooth connection.

## Bluetooth pairing process and notes:

* In the MakeCode editor, open the extensions on the bottom of advanced tab, click on the bluetooth extension icon to apply.Bluetooth and Radio extensions cannot coexist, choosing bluetooth will automatically remove radio extension.

<div align=center>
<img src="../assets/Makecode_bluetooth_extension.jpg" width="200"/>
</div>

* When pairing the micro: bit with android third-party app, one could turn on "Passkey pairing: Paring requires 6 digit key to pair." option in Project settings.
* To enter pairing mode, connect micro: bit to power, press reset button once while holding A+B button.
Do NOT let go of A+B buttons while the progress bar is running, it would interrupt the pairing process and one would need to start over.
* Android devices need to turn on GPS and bluetooth to have a stable connection.
* On Android devices, navigate to bluetooth settings, find and pair with the micro: bit. Once the pairing process starts, micro: bit will hint to press button A once, then it would scroll a 6 digit pairing code. Enter the code on the Andriod device to complete the pairing process.
* Press the reset button on the Micro: bit after pairing to restart.
* iOS devices does not require to enter bluetooth settings. To pair with the micro: bit, please follow the pairing instructions in the official micro: bit app.

## Example Blocks
<div align=center>
<img src="../assets/TriodeCar_bluetooth_control_1.png" width="500"/>
</div>

[Example project file on Github](https://github.com/Wind-stormger/Makecode/blob/master/microbit-Triode-car_bluetooth_control_1.hex)

> After the project file is downloaded locally, it can be imported into MakeCode for viewing and re-editing, or it can be burned directly to micro:bit via USB to run. 

## Design description 

When paired successfully with bluetooth, display a red heart, whereas a disconnection would display an "X" symbol. Press the buttons inside the app to control the Triode-Car wirelessly. Press button A to go forward, C to turn left, and D to turn right, release the buttons to stop.

The "on event from()with value()" block can be found in the Control tab in Makecode.