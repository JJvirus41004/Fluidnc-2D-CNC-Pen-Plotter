# Custom FluidNC Configuration for 2D CNC Pen Plotter ✍️

This repository contains a **custom FluidNC configuration and usage workflow**
for a **2D CNC pen plotter** built around an **ESP32 (WROOM-32)**,
**A4988 stepper motor drivers**, and a **servo-based pen plotting mechanism**.

Rather than using FluidNC as-is, this setup required **custom configuration work**
to support a **2-axis (X–Y) plotter with a servo-controlled pen lift** running on a
**non-standard, custom-designed PCB**.

The configuration format used here was **not directly compatible with the latest
FluidNC examples**. A working structure had to be derived by **referencing older
FluidNC commits**, then adapted to match the hardware constraints, pin mappings,
and plotting behavior of this machine.

---

## 🎯 Purpose of This Repository

This project focuses on **configuration engineering and system integration**, not
on modifying FluidNC firmware itself.

Key objectives include:
- Adapting FluidNC for a **2D-only CNC pen plotter** (no traditional Z-axis)
- Implementing a **servo-based pen up/down mechanism** in place of a Z motor
- Customizing `config.yaml` for a **custom ESP32 PCB**
- Mapping ESP32 GPIOs to **A4988 stepper drivers and servo control circuitry**
- Creating a **repeatable YAML + G-code workflow** for plotting
- Documenting the reasoning, constraints, and trade-offs behind configuration choices

This is intentionally a **configuration-first project**, demonstrating how
complex CNC behavior can be achieved through careful setup rather than firmware changes.

---

## 📌 Quick Access

- ⚙️ **FluidNC Configuration**  
  👉 [View custom config.yaml](./config/config.yaml)

- 🧾 **Example G-code Files**  
  👉 [Browse G-code examples](./gcode/)

- 📄 **Documentation & Notes**  
  👉 [Read documentation](./docs/README.md)

- 🔌 **Hardware Pin Mapping**  
  👉 [View ESP32 ↔ Driver mapping](./hardware/pin_mapping.md)

---

## 🧠 Why This Matters

While FluidNC provides a powerful foundation, real machines often deviate from
standard examples due to hardware and mechanical constraints.

This project highlights practical challenges such as:
- Working with **legacy-compatible configuration formats**
- Adapting firmware configuration to **custom PCBs**
- Reducing a CNC system to **2 controlled axes**
- Replacing a motorized Z-axis with a **servo-based pen plotting mechanism**
- Aligning **hardware behavior, YAML configuration, and G-code execution**

The repository serves as a reference for adapting FluidNC to **non-traditional CNC
machines**, particularly lightweight plotters and experimental platforms.
