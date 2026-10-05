# Pluto — A Natural Language Model Designed Toward General Intelligence

<p align="center">
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjfFumYblOJGu4pKNwpMDNlA4oIBKXIH7s5IsITul3uC08ZWFP1CgTSKPVpA40JpGc9WXhCiOsp5zpe7cmJrldSbJW-8k8zahRKjiTzcErRowrgG32LbL1sQZVcBA6eInDKg8REafIteX_tka9otnZCZ469k4XK2rGNxhhFtzcWsaUYjDbpb-AqbUBH63M/s1600/PLUTO_LOGO.jpg" width="180">
</p>

<p align="center">
  <strong>Pluto — Talk to your hardware instead of programming it.</strong>
</p>

---

## What is Pluto?

[![Pluto Demo](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiW3KlIfi_Hhf8eYrGOzF6er0ST4rB214ZeWKomQER4jtvd0Z9VI4qR_i6fprcAkuSyj1S9OpzT44TnY0i49wtsDRgqGCN63u0iDd1AQyeJ9_4nN0ymLYeS0nWAKW7U2RuMP22NmA-uy_InK8iv5rORhmT2A0IZjoIRok-2Hi444K8-LgEnlU6LwpNqUmU/s1600/pluto_ai_th.jpg)](https://www.youtube.com/watch?v=TATQVDR8HoY)


**Pluto is a Natural Language system designed to run directly inside microcontrollers (MCUs) and control the hardware from within the chip itself — without requiring traditional programming for every new task.**

Pluto is designed to operate with an extremely small memory footprint and can run effectively with approximately **0.5 MB of RAM**.

## Supported Hardware

Pluto currently supports the following MCU and embedded platforms:

- **Arduino Mega**
- **ESP32**
- **Raspberry Pi**
- **STM32**

Pluto is designed to be adaptable across different microcontroller and embedded hardware architectures, allowing the same natural-language control concept to be applied across multiple platforms.

## How Pluto Works

Pluto is designed to allow users to control hardware through natural-language instructions instead of writing traditional firmware code.

The user describes what they want to do, and Pluto interprets the instruction, organizes the required operations, and executes them through the connected MCU and hardware.

### Example: — Gyroscope + Servo Motor

Suppose a gyroscope sensor is connected to the **SDA/SCL** pins, and a servo motor is connected to **Pin 15**.

The user can simply tell Pluto:

> "I connected a gyroscope sensor to your SDA and SCL pins, and a servo motor to Pin 15. Keep the servo balanced at 0 degrees."

Pluto interprets the instruction and performs the required hardware operations.

```text
User:
"I connected a gyroscope sensor to SDA/SCL and a servo motor
to Pin 15. Keep the servo balanced at 0 degrees."

        ↓

Pluto Understanding

        ↓

I²C → Gyroscope
Pin 15 → Servo Motor

        ↓

Read Gyroscope
        ↓
Process Orientation
        ↓
Calculate Required Servo Position
        ↓
Control Servo

```

# PLUTO is a revolutionary architecture designed to operate directly on MCUs, enabling intelligent, real-time control of hardware at the embedded level. Unlike conventional systems that rely on pattern matching, Pluto is designed to emulate the structure of human thought—transforming natural language into structured reasoning and actionable instructions. This makes Pluto more than an embedded control architecture; it represents a direct step toward bringing AGI-inspired reasoning into the world of edge devices and autonomous machines.

<p align="center">
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgc22GwoFwX21ftEeICQQ_NbWpzSJqTC8JPP5En7U0uA7X-3mACbanXQZtXvKMWXABr4v843Yuzo_aScsAtZP4HkfUn3sWMavipawIpC7PQ9M4Cowoi5oapfhk_gBnPi7LN3G2eGzEsTICGWH0e1R3a8IQRUg6Voupl0yMonK26p0Zh0fQnXi2ORzx8JyM/s1600/block_d.png">
</p>

## Get Pluto

Pluto is available as a **physical hardware product**.

<p align="center">
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjyxPSXvv19HQfH4xyJ9JFE16Ci-HXgehL5g4-K5FGMS2iv__etasNIq81SyBKWIrnjWhtvE_1ASC1cQb9WFxLCYa9hZRUkIb34Zg24R0MrT9qPsNWVGCgxAwzRQ42u_5VY31nI_vhr22Ry-1ZKoBDCFVrpK0Oikks0C1u8CQ6Da9MY80yOjeJ-AijkKfA/s1600/pluto_product.jpg">
</p>

### Pluto 0.1

**$450 USD**

[**Buy Pluto 0.1 →**](https://nazdev.gumroad.com/l/pluto_0_1)
---

### Pluto 0.3

**$799 USD**

[**Buy Pluto 0.3 →**](https://nazdev.gumroad.com/l/pluto_0_3)
---

Its core purpose is simple:

> **Instead of programming the microcontroller, communicate with it using natural language.**

Pluto is designed to be adaptable across a wide range of MCU architectures. The system can interpret natural-language instructions and convert them into structured hardware operations that the microcontroller can execute.

### Long-Term Memory

For persistent data storage, Pluto can work with an external **32 KB non-volatile FRAM** connected through I²C:

**MB85RC256V I²C Non-Volatile FRAM**

This memory can be used to retain user-defined tasks, instructions, states, and other persistent information even when the MCU is powered off.

### No Third-Party AI APIs

Pluto is designed to operate **without relying on third-party AI APIs or external cloud AI services**.

The goal is to keep the core intelligence and hardware-control process directly on the embedded system.

### Beyond Pattern Matching

Pluto is not designed around conventional keyword or simple pattern-matching approaches.

Instead, Pluto is being developed around a structured **natural-language understanding and reasoning approach**, inspired by how humans interpret instructions, understand relationships between actions, and organize tasks before execution.

This makes Pluto more than a simple command parser.

We see Pluto as an **early exploration toward AGI-like intelligence at the edge** — bringing natural-language understanding, task organization, and hardware control directly into embedded systems.

---

### Core Idea

**Natural Language → Understanding → Structured Instruction → Hardware Execution**

Pluto's long-term goal is to make embedded hardware programmable through **communication rather than traditional code**.




---

## Future Development

Pluto is currently under active development.

We are working toward **Pluto 1.5 Flash** and **Pluto 2.5**, with a major expansion of Pluto's capabilities.

The future versions are being designed to run directly on smartphones and use a portion of the phone's available system resources. Pluto 1.5 Flash and Pluto 2.5 are planned to use approximately **2 GB of RAM and 10 GB of storage** from the host smartphone, rather than requiring dedicated memory and storage hardware.

For example, on a smartphone with **8 GB of RAM**, Pluto may use approximately **2 GB of the available RAM** while running, with the remaining system resources available to the smartphone and other applications.

The goal is for Pluto to understand and process user instructions in a more human-like way and use that understanding to perform tasks.

Pluto will be designed to communicate directly with the smartphone and control a wide range of external hardware and embedded systems.



### The Long-Term Vision

Pluto is not intended to operate primarily through simple pattern matching.

The long-term objective is to develop a system capable of **understanding information, reasoning about instructions, organizing tasks, and taking appropriate actions** in a way that is closer to human information processing.

This development represents our exploration toward **AGI (Artificial General Intelligence)** — bringing more general-purpose intelligence from software systems into real-world hardware interaction.

---

## Support Pluto Development

Pluto is an independent research and development project.

If you are interested in supporting the development of future Pluto versions, hardware integration, and embedded intelligence, you can support the project or get in touch with us.

**Development support, collaboration, and early-access opportunities will be announced as the project progresses.**

### Links

🌐 **Website:** [Visit us](https://dibsoftiot.com/)

💼 **LinkedIn:** [Follow LinkedIn](https://www.linkedin.com/in/nazmul-agi/)

---

### Support the Development

If you would like to support the ongoing development of Pluto:

[**Support Pluto Development →**](https://nazdev.gumroad.com/l/support)

---

<p align="center">
  <strong>Pluto — Talk to your hardware instead of programming it.</strong>
</p>

