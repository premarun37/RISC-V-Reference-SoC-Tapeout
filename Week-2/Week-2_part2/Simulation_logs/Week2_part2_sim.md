# Week 2 – Simulation Logs

This section documents the **environment setup**, **installation steps**, and the commands used to perform both **pre-synthesis** and **post-synthesis** simulations of the BabySoC design.

---

## 1. Environment Setup

Before starting the simulations, install the required packages and clone the BabySoC repository.

### Commands:

```bash
# Update package list
sudo apt update

# Install required tools
sudo apt install make python python3 python3-pip git iverilog gtkwave

# Fix docker permissions (required by some scripts)
sudo chmod 666 /var/run/docker.sock

# Install Python dependencies
pip3 install pyyaml click sandpiper-saas
```

### Clone the BabySoC Repository:

```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC
```

### Create and Activate a Virtual Environment:

```bash
# Create Python virtual environment
python3 -m venv venv

# Activate the virtual environment
source venv/bin/activate
```

All subsequent steps (pre-synthesis and post-synthesis) are run inside this environment.

---

## 2. Pre-Synthesis Simulation

### Commands:

```bash
# Move into the BabySoC directory
cd VSDBabySoC

# Run pre-synthesis simulation
make pre_synth_sim

# View waveforms
gtkwave output/pre_synth_sim/pre_synth_sim.vcd
```

### Explanation:

1. **`cd VSDBabySoC`** – navigates into the cloned BabySoC project directory.
2. **`make pre_synth_sim`** – compiles and simulates the design before synthesis. The simulation produces a `.vcd` (Value Change Dump) file with digital waveform data.
3. **`gtkwave ...pre_synth_sim.vcd`** – opens the waveform in GTKWave for analyzing reset, clock, and output behavior.

**Log Location:**

```
output/pre_synth_sim/pre_synth_sim.vcd
```

---

## 3. Post-Synthesis Simulation

### Commands:

```bash
# Still inside VSDBabySoC directory
# Run post-synthesis simulation
make post_synth_sim

# View waveforms
gtkwave output/post_synth_sim/post_synth_sim.vcd
```

### Explanation:

1. **`make post_synth_sim`** – compiles and simulates the design after synthesis (mapped netlist). This reflects gate-level design behavior.
2. **`gtkwave ...post_synth_sim.vcd`** – opens the post-synthesis waveform, enabling comparison with pre-synthesis results.

**Log Location:**

```
output/post_synth_sim/post_synth_sim.vcd
```

---

## 4. Notes

* Both simulations highlight important signals:

  * **`clk`** → Clock signal from PLL driving the system.
  * **`reset`** → Initialization signal bringing modules to a known state.
  * **`out`** → Output signal from the DAC model.

* **Pre-synthesis** validates functional correctness of the RTL design.

* **Post-synthesis** ensures correctness after gate-level mapping.

