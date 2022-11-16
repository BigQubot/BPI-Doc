# Installing

This article will guide you through installing Arduino support for the Leaf-S3.

## Install support using Arduino IDE

![](../assets/images/logo_arduino.png)

Here's how to install the Arduino-ESP32 directly from the Arduino IDE.

> Note: For an overview of SoC support, see the table in [Supported Soc](https://docs.espressif.com/projects/arduino-esp32/en/latest/getting_started.html#supported-soc-s), your There you can find out whether a particular chip is in a stable or development release.

- Link to stable version: https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

- Development version link: https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_dev_index.json

> As of Arduino IDE version 1.6.4, Arduino allows the installation of third-party platform packages using the Boards Manager. We have packages for Windows, macOS and Linux.

To start the installation process with Boards Managaer, follow these steps:

- Install current upstream Arduino IDE version 1.8 or higher. The current version is at the arduino.cc website.

- Start Arduino and open the File>Preferences window and click on the location shown.

![](../assets/images/install_guide_preferences.png)

- Enter one of the above publish links after Additional Board Manager URLs. You can add multiple URLs, one per line.

![](../assets/images/install_guide_boards_manager_url.png)

Open the Board Manager from the Tools > Boards menu and install the esp32 platform.

![](../assets/images/install_guide_boards_manager_esp32.png)

After restarting the arduino IDE, you can see more ESP32 options, and you can configure it as shown in the figure.

![](../assets/images/Board_chose.jpg)