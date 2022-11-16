# 安裝

這篇文章將會指引您安裝Leaf-S3的Arduino支持。

## 使用Arduino IDE安裝支持

![](../assets/images/logo_arduino.png)

這是直接從 Arduino IDE 安裝 Arduino-ESP32 的方法。

> 注意：有關 SoC 支持的概述，請查看[Supported Soc](https://docs.espressif.com/projects/arduino-esp32/en/latest/getting_started.html#supported-soc-s) 的表格，您可以在其中找到特定芯片是否處於穩定或開發版本。

- 穩定版鏈接：https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

- 開發版鏈接：https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_dev_index.json

> 從 Arduino IDE 版本 1.6.4 開始，Arduino 允許使用 Boards Manager 安裝第三方平台包。我們有適用於 Windows、macOS 和 Linux 的軟件包。

要使用 Boards Managaer 開始安裝過程，請執行以下步驟：

- 安裝 1.8 或更高版本的當前上游 Arduino IDE。當前版本位於arduino.cc網站。

- 啟動 Arduino 並打開 文件>首選項 窗口，並點擊圖示中的位置。

![](../assets/images/install_guide_preferences.png)

- 在Additional Board Manager URLs後面輸入上述發布鏈接之一。您可以添加多個 URL，一行一個。

![](../assets/images/install_guide_boards_manager_url.png)

從 工具 > 開發板 菜單打開 開發板管理器 並安裝esp32平台。

![](../assets/images/install_guide_boards_manager_esp32.png)

重啟arduino IDE之後可以看到多了ESP32選項，按照圖示配置即可

![](../assets/images/Board_chose.jpg)