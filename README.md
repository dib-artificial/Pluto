# Pluto — A Natural Language Model Designed Toward General Intelligence TinyML

[![Pluto Demo](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEguk_Aeu9srpZDPxlZ4LRiPXA921hZlweoRngAm91TtbJyR1iGf3llINPmlIvAuvuhxjTUpeVC0GCqSfM7Td-_BYBvLAbP_1ShysDFi-39ClHsxATPuRqJLte3ZLjOMQvIeRT2V-JDT_j34XmV2ton-xjn0xfJnryMsP2uoKHaBVz3qWemFdJQvTFlq-1o/s1600/pluto_image_video.jpg)](https://www.youtube.com/watch?v=QuJR2e3oPL4)

> [!WARNING]
> **Bluetooth Configuration and Flash Memory Optimization**
>
> The ESP32 has built-in Bluetooth functionality. However, enabling the internal Bluetooth stack can significantly increase firmware memory usage.
>
> In this project, the reported flash usage is approximately **80% when using the ESP32's built-in Bluetooth**. To reduce firmware memory usage, an external **HC-06 Bluetooth module** is used instead, bringing the reported flash usage down to approximately **22%**.
>
> These figures represent the project's observed results and may vary depending on the ESP32 configuration, firmware, libraries, and build environment.
>
> The HC-06 communicates with the ESP32 through UART2 using the following configuration:
>
> ```cpp
> #define RX2_PIN 16
> #define TX2_PIN 17
>
> Serial.begin(115200);
> Serial2.begin(9600, SERIAL_8N1, RX2_PIN, TX2_PIN);
> ```
>
> **Code explanation:**
>
> - `RX2_PIN 16`: ESP32 GPIO 16 receives serial data.
> - `TX2_PIN 17`: ESP32 GPIO 17 transmits serial data.
> - `Serial.begin(115200)`: Initializes the USB serial interface for debugging.
> - `Serial2.begin(9600, SERIAL_8N1, RX2_PIN, TX2_PIN)`: Initializes UART2 at 9600 baud with 8 data bits, no parity, and 1 stop bit.
>
> **Note:** These are UART pin definitions and serial initialization settings, not timer configurations.

<p align="center">
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgpBaPAcNWBw98ty-ua-o98rnI4ygQO4VTUhtxYhyphenhyphenpWOr6HZ9nJq_YsTCskVdoGCChHc8veA8b545yigHI9Gm9dTlPC-qkSQtX62v-hdJniJ1gt2uRKxokV9Ec1hId_zm3K11NGbScyTkQ4QN6anyGyZM4Vox7uFIgp-fvx5yOr_e7FTID22miURhM9QgU/s1600/apps_ss.jpg">
</p>

## Flutter Bluetooth Application

A lightweight Flutter application UI is used to communicate with Pluto running on the ESP32 through the external HC-06 Bluetooth module.

The application performs three primary functions:

1. **Bengali-to-English Translation:** The application translates Bengali input into English using an internet-based translation service.
2. **Instruction Transmission:** The translated English text is sent to the HC-06 module over Bluetooth and forwarded to the ESP32 for Pluto to process.
3. **Text Reception:** The application receives text responses from the HC-06 module and handles them in the UI.

The Bluetooth connection between the phone and the ESP32 does not itself require an internet connection. However, the translation feature requires internet access.

### Flutter Application Source Code

The Flutter application source code is available in this repository for inspection. Developers can review the UI, translation workflow, Bluetooth communication, and instruction transmission/reception logic.


## Hardware Specifications (the module we used)

TinyML engine (Pluto) runs on an ESP32 development board featuring a CH340 USB-to-UART interface and USB Type-C connector.

| Specification | Details |
|---|---|
| Development Board | ESP32 Dev Board |
| USB Interface | USB Type-C |
| USB-to-UART Bridge | CH340 |
| Microcontroller Family | Espressif ESP32 |
| CPU Architecture | Xtensa LX6 |
| CPU Cores | Dual-core (2 cores) |
| Maximum CPU Frequency | Up to 240 MHz |
| Internal SRAM | 520 KB (chip-level specification) |
| ROM | 448 KB (chip-level specification) |
| Flash Storage | 4 MByte (32Mbit) |
| Wi-Fi | 2.4 GHz, IEEE 802.11 b/g/n |
| Bluetooth | Bluetooth Classic and BLE (original ESP32) |
| GPIO | Up to 34 GPIOs on the original ESP32 chip; board availability varies |
| ADC | 12-bit SAR ADC |
| DAC | 2 × 8-bit DAC (original ESP32) |
| PWM | LED PWM controller, up to 16 channels |
| General-Purpose Hardware Timers | 4 (original ESP32) |
| High-Resolution Software Timer API | `esp_timer`, 1 µs time resolution |
| Communication Interfaces | UART, SPI, I²C, I²S |
| Programming Platforms | Arduino IDE, ESP-IDF |
| USB Programming | CH340 USB-to-UART bridge |


 
 <p align="center">
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi1XK4v_bfJb5ccAlxf0kqGwsnSIONPRoDFdWVbES4NLJnObAcEwJVTAaAeIRq9mDLp12Qaz7OJDBwonpfDCDZyE9-BMQ8R85BD79IEAUv3vqJzPjtGWCwzAKaiZd6XWqq0iYAx6qXS69grQTGXQICHY3izBB7CqFr_9uYKc-iTC4XvjB5Fw0pcdlk2Two/s1600/esp_code.jpg">
</p>

---
## Memory and Firmware Footprint

| Memory / File Type | Total Capacity | Pluto Usage | Usage (%) | Remaining |
|---|---:|---:|---:|---:|
| ESP32 Flash (Total) | 4 MB (4,194,304 bytes) | 1,169,787 bytes (≈ 1.115 MiB) | ≈ 27.9% | ≈ 2.89 MiB |
| Application Flash (Allocated) | 1,310,720 bytes (1.25 MiB) | 1,169,787 bytes (≈ 1.115 MiB) | 89% | 140,933 bytes |
| ESP32 RAM (Global/Dynamic) | 327,680 bytes (320 KiB) | 101,576 bytes (≈ 99.2 KiB) | 30% | 226,104 bytes |
| Hardware Control Layer (Flash) | Application Flash | — | ≈ 28% | — |
| Hardware Control Layer (RAM) | ESP32 RAM | — | ≈ 9% | — |
| Pluto TinyML Engine (Flash) | Application Flash | — | ≈ 61% | — |
| Pluto TinyML Engine (RAM) | ESP32 RAM | — | ≈ 21% | — |
| `pluto_ML_AI.ino.bin` (Firmware Binary) | — | 1,143 KB (reported) | — | — |

> [!WARNING]
> **Memory Usage Depends on Hardware and Configuration**
>
> Pluto's memory footprint depends on three primary factors:
>
> 1. **Microcontroller capabilities:** Available Flash, RAM, CPU architecture, and processing capacity.
> 2. **Hardware control-layer functions:** The number and type of supported functions, such as Bluetooth, GPIO, I²C (SDA/SCL), and other peripherals.
> 3. **TinyML engine configuration:** Adding more hardware control functions can increase the size of the overall system and its supporting code, affecting the resources available to the TinyML engine.
>
> The percentages above are configuration-specific estimates based on the reported build. The TinyML engine figures are calculated by subtracting the estimated hardware control-layer usage from the total reported application Flash and RAM usage.



