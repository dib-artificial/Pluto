# TinyML AI - (Pluto Engine): A natural language model designed for general intelligence that can directly control microchips.



> [!NOTE]
> To provide a detailed explanation of how our new model functions and its internal structure, the entire presentation has been divided into 4 sections:
>
> ---
>
> **01 — Overview**
>
> An overview of how TinyML AI (the Pluto Engine) operates within a microchip, including further details.
>
> ---
>
> **02 — Engine Functionality**
>
> A discussion on how the Pluto Engine functions.
>
> ---
>
> **03 — Training & Limitations**
>
> How the Pluto Engine is trained, and the limitations of its capabilities when running on a microchip.
>
> ---
>
> **04 — Applications & Industries**
>
> Potential applications and sectors where the Pluto Engine can be utilized.

## 01 — Overview (This section provides a detailed walkthrough, including experiments using an ESP32 device.)

> [!NOTE]
> My language is Bengali; I write articles in Bengali first and then translate them into English. If you have any trouble understanding something, please feel free to send me a direct message on LinkedIn. https://www.linkedin.com/in/nazmul-agi/


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


## Hardware Specifications (The module we used)

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

## Hardware Control & Understanding

The current TinyML AI device (Pluto Engine) includes the following features, though some are limited.

- **GPIO** — Digital HIGH / LOW input and output
- **PWM** — Variable duty-cycle control for LEDs, motors, and other devices
- **I²C** — Communication with sensors, displays, memory, and peripheral devices
- **SPI** — High-speed communication with compatible peripherals (Limited)
- **Servo** — Position control and movement sequences
- **Analog I/O** — Reading analog sensors and generating hardware responses
- **Timers / Frequency** — Hardware timing, pulse and frequency generation
- **Sensors** — Processing sensor data and using it in conditional decisions

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

---


## I²C Sensor Detection Benchmark: ESP32 vs Pluto - TinyML AI

This benchmark compares a conventional ESP32 I²C address scan with Pluto processing a natural-language instruction to identify connected I²C sensors.

### Test Instruction

```text
Check how many sensors are connected to I2C SDA GPIO 21 and GPIO 22 (SDA - SCL)
```

**Pluto's response:**

```text
One address is found here (0x76)
```

The detected I²C address was `0x76`.

### Benchmark Results

| Metric | ESP32 Pure I²C Scan | Pluto Engine |
|---|---:|---:|
| Execution scope | Direct I²C address scanning | Natural-language processing and task execution |
| SDA pin | GPIO 21 | GPIO 21 |
| SCL pin | GPIO 22 | GPIO 22 |
| I²C clock | 100 kHz | 100 kHz |
| Addresses checked | 1–126 | Determined by Pluto's implementation |
| Devices detected | 1 | 1 address reported |
| Average execution time* | ~18.801 ms | ~110.133 ms |
| Relative execution time | 1× | ~5.86× |

\* The ESP32 average is calculated from the 18 supplied scan results. The Pluto average is calculated from the 19 supplied results (Tests 031–049), not the complete 50-run dataset.

### Understanding the Difference

A conventional ESP32 I²C scanner directly checks device addresses and reports which devices acknowledge communication.

Pluto performs additional work before or during hardware interaction, including processing the natural-language instruction and executing its internal task workflow.

Consequently, Pluto's total execution time is expected to be higher than that of a direct I²C scan. The approximately 5.86× difference in this sample should not be interpreted as Pluto's hardware-control layer being 5.86× slower, because the two measurements cover different amounts of processing.

### Pluto Benchmark Code

The following code measures the elapsed time of each Pluto function call over 50 iterations.

```cpp
for (int i = 0; i < 50; i++) {

    int64_t startTime = esp_timer_get_time();

    pluto("Check how many sensors are connected to I2C SDA GPIO 21 and GPIO 22 (SDA - SCL)");

    int64_t endTime = esp_timer_get_time();

    int64_t elapsedUs = endTime - startTime;

    Serial.printf(
      "Test %03d | %lld us | %.3f ms\n",
      i,
      (long long)elapsedUs,
      elapsedUs / 1000.0
    );
}
```

The measured interval begins immediately before calling `pluto()` and ends when that function returns. Therefore, the result represents the time spent inside the complete function call, including any processing and hardware operations performed synchronously by it.

### Important Warnings and Limitations

**1. Different benchmark scopes**

The pure ESP32 scanner measures direct I²C address scanning, whereas Pluto's measurement includes its instruction-processing workflow. These figures are useful for understanding end-to-end latency, but they are not an isolated comparison of the two systems' hardware-scanning performance.

**2. Results depend on configuration**

Execution time may vary with the ESP32 board, Arduino core version, compiler optimizations, I²C clock, enabled control functions, and the number of addresses or devices checked. Results should be compared under documented, consistent conditions.

**3. RAM usage is not reported in this benchmark**

This benchmark measures elapsed execution time only. It does not measure peak RAM consumption.

Repeated tests may reuse cached data, previously allocated memory, retained task state, or other resources from earlier runs. As a result, simply checking free RAM before and after each function call would not necessarily reveal Pluto's actual peak RAM requirements.

A separate memory benchmark would be needed to investigate heap usage, minimum free heap, stack requirements, and memory retained between runs. These metrics should be measured and reported separately from execution time.

**4. Results are specific to the tested configuration**

The reported values describe the supplied ESP32 test results and Pluto configuration. They should not be treated as universal performance figures for all supported microcontrollers or Pluto versions.

### Conclusion

In the supplied samples, a conventional ESP32 I²C scan completed in approximately 18.8 ms, while Pluto's full instruction-processing workflow took approximately 110.1 ms.

The additional time reflects the broader scope of Pluto's task processing and should be evaluated alongside its hardware-control capabilities, memory requirements, and the complexity of the requested instruction.

---





