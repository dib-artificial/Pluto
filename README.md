# Pluto — A Natural Language Model Designed Toward General Intelligence TinyML AI

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

---
 
 <p align="center">
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhDeFP5nmIg39YnzMugLUT2XHQysJa51j70RrCQwSHBYMPhhQzk5CBLesmZpXMaiZdL2MHTVJvgt_HZupGpjxnREkcAgWFJ6mmqLCWNP53R6KtpSvblnh85J5YX_cicgST64XnLXkwXslqVpkPZ1qCl-Z91I_3EpHElXe-98wi1Mo2Hy0nPrW4GWQSWHPE/s1600/esp_code_data.jpg">
</p>

## Memory and Firmware Footprint

The Pluto firmware is evaluated in three configurations: the Hardware Control Layer, the Pluto TinyML Engine, and the complete integrated firmware.

### Memory Usage Summary

| Memory / File Type | Total Capacity | Used | Usage (%) | Remaining |
|---|---:|---:|---:|---:|
| Hardware Control Layer — Flash | 1,310,720 bytes (1.25 MiB) | 378,948 bytes (≈ 370.1 KiB) | 28% | 931,772 bytes |
| Hardware Control Layer — RAM | 327,680 bytes (320 KiB) | 31,100 bytes (≈ 30.4 KiB) | 9% | 296,580 bytes |
| Pluto TinyML Engine — Flash | 1,310,720 bytes (1.25 MiB) | 806,788 bytes (≈ 787.9 KiB) | 61% | 503,932 bytes |
| Pluto TinyML Engine — RAM | 327,680 bytes (320 KiB) | 69,564 bytes (≈ 67.9 KiB) | 21% | 258,116 bytes |
| Complete Firmware — Flash | 1,310,720 bytes (1.25 MiB) | 1,174,724 bytes (≈ 1.12 MiB) | 89% | 135,996 bytes |
| Complete Firmware — RAM | 327,680 bytes (320 KiB) | 100,380 bytes (≈ 98.0 KiB) | 30% | 227,300 bytes |
| `pluto_ML_AI.ino.bin` — Firmware Binary | — | 1,148 KB (reported) | — | — |

### Build Report: Hardware Control Layer

```text
Sketch uses 378948 bytes (28%) of program storage space.
Maximum is 1310720 bytes.

Global variables use 31100 bytes (9%) of dynamic memory,
leaving 296580 bytes for local variables.
Maximum is 327680 bytes.
```

The Hardware Control Layer manages hardware-facing functions such as Bluetooth communication, GPIO, I²C (SDA/SCL), and other supported peripheral operations.

### Build Report: Pluto TinyML Engine

```text
Sketch uses 806788 bytes (61%) of program storage space.
Maximum is 1310720 bytes.

Global variables use 69564 bytes (21%) of dynamic memory,
leaving 258116 bytes for local variables.
Maximum is 327680 bytes.
```

The Pluto TinyML Engine provides the core instruction-processing functionality. Its reported memory usage represents the engine configuration tested in this build.

### Build Report: Complete Integrated Firmware

```text
Sketch uses 1174724 bytes (89%) of program storage space.
Maximum is 1310720 bytes.

Global variables use 100380 bytes (30%) of dynamic memory,
leaving 227300 bytes for local variables.
Maximum is 327680 bytes.

pluto_ML_AI.ino.bin = 1148 KB
```

This build report represents the integrated firmware containing the hardware control layer and Pluto TinyML Engine.

> [!WARNING]
> **Memory Measurements and Build Configuration**
>
> The memory figures above were obtained by compiling the Hardware Control Layer, Pluto TinyML Engine, and complete firmware in separate configurations.
>
> When components are compiled separately, their memory usage may differ from their usage in the integrated firmware. Compiler optimizations, shared code, linked libraries, global variables, and build configuration can affect the results.
>
> Therefore, the individual component measurements should not be expected to add up exactly to the integrated firmware measurements.
>
> Pluto's overall memory footprint depends on:
>
> 1. **Microcontroller capabilities:** Available Flash, RAM, CPU architecture, and processing capacity.
> 2. **Hardware control functions:** The number and type of supported functions, including Bluetooth, GPIO, I²C, and other peripherals.
> 3. **TinyML engine configuration:** Adding more control-layer functions can increase the size of the overall system and its supporting code, potentially affecting the TinyML engine's implementation and resource requirements.
>
> All reported values are specific to the tested ESP32 hardware and build configurations.





