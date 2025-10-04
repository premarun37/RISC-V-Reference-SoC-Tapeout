# Week 2 – Part 1: SoC Fundamentals & Functional Modelling

## 1. What is a System-on-Chip (SoC)?

A System-on-Chip (SoC) is an integrated circuit (IC) that consolidates multiple system-level components into a single chip. Instead of having a separate CPU, memory, and peripherals on different boards, all essential parts are tightly packed into one silicon die.

This integration brings major advantages:

* **Reduced size:** Smaller form factor compared to board-level designs.
* **Lower power consumption:** Shorter interconnections reduce energy use.
* **Improved performance:** Faster communication between modules due to on-chip interconnects.
* **Cost efficiency:** Fewer external components lead to cheaper manufacturing at scale.

SoCs are widely found in smartphones, embedded systems, IoT devices, and automotive applications. For example, Qualcomm Snapdragon and Apple’s M-series are high-performance SoCs used in consumer electronics.

---

## 2. Components of a Typical SoC

1. **Central Processing Unit (CPU):**

   * The “brain” of the SoC, responsible for executing instructions.
   * Can be based on architectures like ARM, RISC-V, or x86.
   * Often includes multiple cores for parallel execution.

2. **Memory Subsystem:**

   * **Volatile memory (RAM):** Temporary storage for instructions and data during program execution.
   * **Non-volatile memory (ROM/Flash):** Stores firmware, bootloaders, or embedded applications permanently.
   * Cache memory is also integrated to speed up CPU access.

3. **Peripherals:**

   * Provide interfaces to the outside world.
   * Examples:

     * UART (serial communication)
     * GPIO (general-purpose input/output pins)
     * SPI / I²C (for connecting sensors and low-speed devices)
     * Timers, ADC/DACs for control applications

4. **Interconnect (Bus or Network-on-Chip):**

   * Acts as the communication backbone connecting CPU, memory, and peripherals.
   * Examples: AMBA (Advanced Microcontroller Bus Architecture), AXI, or custom interconnect fabrics.

These components together form a self-contained computing system on one chip.

---

## 3. Why BabySoC?

BabySoC is a **simplified learning model** that mimics the structure of a real SoC without unnecessary complexity. Its purpose is educational:

* Strips down the design to a minimal set of modules (CPU, memory, a few peripherals).
* Allows beginners to focus on **dataflow, reset, and clocking concepts** before diving into full-scale industrial SoCs.
* Serves as a sandbox for practicing simulation and understanding hardware interactions.

By studying BabySoC, we gain the **conceptual foundation** to later scale up to advanced SoCs with multiple cores, caches, and complex interconnects.

---

## 4. Role of Functional Modelling

Functional modelling is the **first validation stage** before RTL design and physical implementation.

### Why it matters:

* **Verification of logic:** Ensures design intent is correct before wasting effort on detailed RTL.
* **Early debugging:** Errors are cheaper to fix at this stage.
* **System-level perspective:** Helps visualize how modules interact as a whole.

### Tools Used:

* **Icarus Verilog (iverilog):** For compiling and simulating Verilog code.
* **GTKWave:** For viewing simulation waveforms, checking reset/clock signals, and analyzing dataflow.

### Key operations validated in functional modelling:

* **Reset operation:** All modules initialize to known states.
* **Clocking:** Synchronization of events across the SoC.
* **Dataflow:** Proper communication between CPU, memory, and peripherals.

Without functional modelling, errors could propagate into RTL design and later into silicon, leading to costly failures.

---

## 5. Summary

A System-on-Chip integrates CPU, memory, peripherals, and interconnect into a compact, efficient chip. BabySoC is a stripped-down learning platform that introduces students to these fundamentals without overwhelming complexity. Through **functional modelling** using Icarus Verilog and GTKWave, one can verify system behavior early and build confidence before diving into RTL and physical design.

This step forms the **foundation of SoC design learning**, bridging the gap between high-level theory and hands-on hardware verification.

