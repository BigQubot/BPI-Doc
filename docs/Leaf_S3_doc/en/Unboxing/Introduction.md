# 【Introduction to development board】

The BPI-Leaf-S3 has an onboard ESP32-S3 chip that supports 2.4 GHz Wi-Fi and Bluetooth® LE dual-mode wireless communication. The board supports two power supply modes: USB and external 3.7V lithium battery, which can realize automatic power switching function under dual power supply, and support USB charging mode. Small size, convenient interface, easy to use, and can be directly applied to low-power IoT projects.

The BPI-Leaf-S3 development board supports ESP-IDF, Arduino, MicroPython and other methods for programming and development in terms of software.

All IO pins corresponding to the chip are marked on the BPI-Leaf-S3 development board, and the order of the IO pins is consistent with the Espressif ESP32-S3-DevKitC-1 development board. Developers can support DevKitC-1 according to actual needs. The peripherals are added to the BPI-Leaf-S3, and the development board can also be plugged into the breadboard.

## key features

- ESP32-S3, Xtensa® 32 bit LX7
- On-Chip Peripherals PSRAM, FLASH
- Ultra-low power 10uA
- 2.4G WIFI, Bluetooth 5, Bluetooth mesh
- GPIO , ADC , TOUCH , PWM , I2C , SPI , RMT , I2S , UART , LCD, CAMERA , USB , JTAG
- 1*4pin I2C connector
- 1*USB Type-C
- 1 * 2pin battery connector, support charging
- 1 * Full Color LED

## hardware

### Interface diagram

![](../assets/images/Leaf-S3_board.png)

### Hardware Specifications

<table>
   <tr>
      <td>BPI-Leaf-S3 Spec Sheet</td>
   </tr>
   <tr>
      <td>SoC main control chip</td>
      <td>ESP32-S3, Xtensa® 32-bit LX7 Dual-Core Processor</td>
   </tr>
   <tr>
      <td>Frequency</td>
      <td>240MHz MAX</td>
   </tr>
   <tr>
      <td>Operating Temperature</td>
      <td>-40℃~+85℃</td>
   </tr>
   <tr>
      <td>On-Chip ROM</td>
      <td>384KB</td>
   </tr>
   <tr>
      <td>On-chip SRAM</td>
      <td>320KB</td>
   </tr>
   <tr>
      <td>Off-chip FLASH ROM</td>
      <td>8MB</td>
   </tr>
   <tr>
      <td>On-Chip Peripherals PSRAM</td>
      <td>2MB</td>
   </tr>
   <tr>
      <td>WIFI</td>
      <td>IEEE 802.11 b/g/n, 2.4Ghz band, 150Mbps</td>
   </tr>
   <tr>
      <td>Bluetooth</td>
      <td>Bluetooth 5, Bluetooth mesh</td>
   </tr>
   <tr>
      <td>GPIO</td>
      <td>BPI-Leaf-S3 has brought out 36 available GPIOs</td>
   </tr>
   <tr>
      <td>ADC</td>
      <td>2 × 12-bit SAR ADC supporting 20 analog channel inputs</td>
   </tr>
   <tr>
      <td>TOUCH Capacitive Touch Sensor</td>
      <td>14</td>
   </tr>
   <tr>
      <td>SPI</td>
      <td>4</td>
   </tr>
   <tr>
      <td>I2C</td>
      <td>2, supports master or slave mode</td>
   </tr>
   <tr>
      <td>I2S</td>
      <td>2, serial stereo data input and output</td>
   </tr>
   <tr>
      <td>LCD</td>
      <td>1, supports 8-bit ~16-bit parallel RGB, I8080, MOTO6800 interface</td>
   </tr>
   <tr>
      <td>CAMERA</td>
      <td>1, supports 8-bit ~16-bit DVP image sensor interface</td>
   </tr>
   <tr>
      <td>UART</td>
      <td>3, supports asynchronous communication (RS232 and RS485) and IrDA</td>
   </tr>
   <tr>
      <td>PWM</td>
      <td>8 independent channels, 14-bit precision</td>
   </tr>
   <tr>
      <td>MCPWM</td>
      <td>2</td>
   </tr>
   <tr>
      <td>USB</td>
      <td>1 × Full Speed ​​USB 2.0 OTG, Type-C Female</td>
   </tr>
   <tr>
      <td>USB Serial/JTAG Controller</td>
      <td>1, USB Full Speed ​​Standard, CDC-ACM, JTAG</td>
   </tr>
   <tr>
      <td>Temperature Sensor</td>
      <td>1, measuring from –20 °C to 110 °C, for monitoring chip internal temperature</td>
   </tr>
   <tr>
      <td>SD/MMC</td>
      <td>1 × SDIO host interface with 2 card slots, supports SD card 3.0 and 3.01, SDIO 3.0, CE-ATA 1.1, MMC 4.41, eMMC 4.5 and 4.51</td>
   </tr>
   <tr>
      <td>TWAI® Controller</td>
      <td>1, compatible with ISO11898-1 (CAN Specification 2.0)</td>
   </tr>
   <tr>
      <td>Generic DMA Controller</td>
      <td>5 receive channels and 5 transmit channels</td>
   </tr>
   <tr>
      <td>RMT</td>
      <td>4 channels transmit, 4 channels receive, shared 384 x 32-bit RAM</td>
   </tr>
   <tr>
      <td>Pulse Counter</td>
      <td>4 pulse count controllers (units), each with 2 independent channels</td>
   </tr>
   <tr>
      <td>Timer</td>
      <td>4 × 54-bit general-purpose timers, 16-bit clock prescaler, 1 × 52-bit system timer, 3 × watchdog timers</td>
   </tr>
   <tr>
      <td>External Crystal</td>
      <td>40Mhz</td>
   </tr>
   <tr>
      <td>RTC and Low Power Management</td>
      <td>Power Management Unit (PMU) + Ultra Low Power Coprocessor (ULP)</td>
   </tr>
   <tr>
      <td>Low Power Current</td>
      <td>10uA</td>
   </tr>
   <tr>
      <td>Operating Voltage</td>
      <td>3.3V</td>
   </tr>
   <tr>
      <td>Input Voltage</td>
      <td>3.3V~5.5V</td>
   </tr>
   <tr>
      <td>Maximum Discharge Current</td>
      <td>2A@3.3V DC/DC</td>
   </tr>
   <tr>
      <td>USB charging</td>
      <td>Support</td>
   </tr>
   <tr>
      <td>Maximum Charge Current</td>
      <td>500mA</td>
   </tr>
   <tr>
      <td>Controllable full color LED</td>
      <td>1</td>
   </tr>
</table>


### Hardware Dimensions


![](../assets/images/Leaf-S3_board_dimension.png)

<table>
   <tr>
      <td>BPI-Leaf-S3 Size Chart</td>
   </tr>
   <tr>
      <td>Pin spacing</td>
      <td>2.54mm</td>
   </tr>
   <tr>
      <td>Mounting Hole Spacing</td>
      <td>23mm/ 62.25mm</td>
   </tr>
   <tr>
      <td>Mounting Hole Dimensions</td>
      <td>Inner Diameter 2mm/Outer Diameter 3mm</td>
   </tr>
   <tr>
      <td>Motherboard Dimensions</td>
      <td>26 × 65.25(mm)/1.02 x 2.57(inches)</td>
   </tr>
   <tr>
      <td>plate thickness</td>
      <td>1.2mm</td>
   </tr>
   <tr>
      <td></td>
   </tr>
</table>

The pin spacing is compatible with universal boards (hole boards, dot matrix boards) and breadboards, which is convenient for debugging applications.

## Information and resources

- [GitHub: BPI-Leaf-S3 Development Board Schematic PDF](https://github.com/BPI-STEAM/BPI-Leaf-S3-Doc/blob/main/sch/BPI-Leaf-S3-Chip- V0.1A.pdf)

- [ESP32-S3 Specifications](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_cn.pdf)

- [ESP32-S3 Technical Reference Manual](https://www.espressif.com/sites/default/files/documentation/esp32-s3_technical_reference_manual_cn.pdf)