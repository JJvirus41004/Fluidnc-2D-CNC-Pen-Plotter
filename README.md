# Custom FluidNC Configuration for 2D CNC Pen Plotter ✍️

This repository contains a **custom FluidNC configuration and usage workflow**
for a **2D CNC pen plotter** built around an **ESP32 (WROOM-32)**,
**A4988 stepper motor drivers**, and a **servo-based pen plotting mechanism**.

The setup was validated on **real hardware**, including testing on an existing
**3D printer motion system**, intentionally operating it as a **2-axis machine**
(X–Y only) while replacing the Z-axis with a **servo-controlled pen lift**.

The configuration used here was **not directly compatible with the latest
FluidNC examples**. A working structure had to be derived by referencing
**older FluidNC commits**, then carefully adapted to match a custom PCB,
motor drivers, servo behavior, and plotting workflow.

---

## 🎯 Purpose of This Repository

This project focuses on **configuration engineering, integration, and validation**
rather than modifying FluidNC firmware itself.

Key objectives include:
- Adapting FluidNC for a **2D-only CNC pen plotter**
- Replacing a traditional Z-axis motor with a **servo-based pen plotting mechanism**
- Customizing `config.yaml` for a **non-standard, custom ESP32 PCB**
- Mapping ESP32 GPIOs to **A4988 stepper drivers (STEP, DIR, ENABLE) and servo control**
- Building a **reproducible YAML + G-code workflow**
- Capturing real-world issues, fixes, and design decisions encountered over time

This is intentionally a **configuration-first project**, demonstrating how
complex CNC behavior can be achieved through careful setup and validation
rather than firmware rewrites.

---

## 🧪 Validation & Real-World Testing

The configuration was **tested and validated on physical hardware**, not in
simulation.

Validation steps included:
- Running the setup on a **real 3D printer motion system**, using only the
  X and Y axes while disabling the original Z-axis
- Verifying stepper direction, enable logic, and motion correctness
- Testing servo-based pen up/down behavior during plotting
- Executing repeated test patterns to observe accuracy and repeatability

A significant amount of time was spent debugging **motor direction and enable
behavior**, including issues caused by **incorrect DIR and ENABLE logic levels**.
Small mistakes in these signals resulted in motors not moving, moving in the
wrong direction, or remaining permanently disabled — issues that were resolved
only through iterative testing and careful configuration changes.

These experiences are documented to help others avoid similar pitfalls.

---

## 📡 File Upload & Execution Workflow

This setup leverages **FluidNC’s flexible file handling and connectivity options**:

- 📂 **SD Card Support**  
  G-code files can be stored directly on an SD card, allowing frequently used
  patterns and test files to be preloaded and executed without re-uploading.

- 🌐 **Local Wi-Fi (Wireless Uploads)**  
  Using FluidNC’s built-in web interface, G-code files can be uploaded wirelessly
  over a local Wi-Fi connection and executed directly from a browser.

- 🔌 **Direct Connection (USB / Serial)**  
  G-code can also be uploaded and streamed via direct USB connection when needed.

This combination allowed flexible testing, quick iteration, and reliable execution
during validation.

---

## 🧾 G-code Examples

The repository includes **example G-code files** used during testing and validation,
such as basic shapes and motion patterns.

These examples were used to:
- Verify axis scaling and direction
- Test pen lift and drop timing
- Observe motion smoothness and repeatability
- Confirm correct interaction between YAML configuration and machine behavior

---

## 📌 Quick Access

- ⚙️ **FluidNC Configuration**  
  👉 [View custom config.yaml](./config/config.yaml)

- 🧾 **Example G-code Files**  
  👉 [Browse G-code examples](./gcode/)

- 📄 **Documentation & Project Notes**  
  👉 [Read documentation](./docs/README.md)

- 🔌 **Hardware Pin Mapping**  
  👉 [View ESP32 ↔ Driver mapping](./hardware/pin_mapping.md)

---

## 🧠 Why This Matters

While FluidNC provides a powerful foundation, real machines often diverge from
reference designs due to hardware, mechanical, and electrical constraints.

This repository reflects:
- Long-term **iteration and debugging on real hardware**
- The importance of **signal correctness (STEP / DIR / ENABLE)**
- Practical use of **legacy-compatible configuration formats**
- Integration of **SD card storage, Wi-Fi uploads, and direct connections**
- Alignment between **hardware behavior, YAML configuration, and G-code execution**

It serves as a reference for adapting FluidNC to **non-traditional CNC machines**,
especially lightweight 2D plotters and experimental platforms.
