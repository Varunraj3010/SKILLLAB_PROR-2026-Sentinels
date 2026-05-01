# SKILL LAB PRACTICAL HACKATHON

## Final Project README

> **Project Weight:** 100%  
> **Team Size:** 4/3 students  
> **Project Duration:** 16 hours  
> **Total Time Available:** 32 effort-hours per team  
> **Project Type:** Playful, interactive, technology-based experience

---

# Before you begin

## Fork and rename this repository

After forking this repository, rename it using the format:

`SKILLLAB_PROR-2026-TeamName`

### Example

`SKILLLAB_PROR-2026-AuroWizards`

Do not keep the default repository name.

---

# How to use this README

This file is your team's **working project document**.

You must keep updating it throughout the build period.  
By the final review, this README should clearly show:

- your idea,
- your planning,
- your design decisions,
- your technical process,
- your build progress,
- your testing,
- your failures and changes,
- your final outcome.

## Rules

- Fill every section.
- Do not delete headings.
- If something does not apply, write `Not applicable` and explain why.
- Add images, screenshots, sketches, links, and videos wherever useful.
- Update task status and weekly logs regularly.
- Use this file as evidence of process, not only as a final report.

---

# 1. Team Identity

## 1.1 Studio / Group Name

`Sentinels`

## 1.2 Team Members

| Name                  | Primary Role                    | Secondary Role   | Strengths Brought to the Project       |
| --------------        | ------------------------------- | --------------   | -------------------------------- |
| `Varunraj Bhirud` | `Enhancement research` | `Documentation`|`Ideation`|
| `Vibhuti Sawant`| `UI Design`|`Debugging`|`Designing visual platform`|
| `Faiza Shaikh`|`Enhancement research`| `Prototyping`|`Creative thinking`|
| `Shreya Korgaonkar` | `Implementation` | `Debugging`  | `Knowledge of Vitis and Xilinx SDK`|

## 1.3 Project Title

`"FPGA Logic Analyzer"`

`(Simulate. Capture. Visualize.)`

## 1.4 One-Line Pitch

`An FPGA-based logic analyzer that simulates digital circuits — from basic logic gates to adders and SRAMs — and streams real-time input/output waveforms to a laptop via UART for live visualization using Python and matplotlib.`

## 1.5 Expanded Project Idea

In 1–2 paragraphs, explain:

- what your project is,
- what kind of experience it creates,
- what technologies are involved.

**Response:**  
`The FPGA Logic Analyzer is a digital hardware project built on the Xilinx Spartan-7 Boolean board. It simulates the behavior of fundamental digital circuits — including basic logic gates (AND, OR, NOT, XOR, NAND, NOR), combinational circuits (half adder, full adder, 4-bit ripple carry adder), and sequential/memory elements (SRAM). The FPGA generates or receives digital input signals, processes them through synthesized RTL logic, and captures the resulting output waveforms in real time.`

`The captured input and output signal data is transmitted from the FPGA to a laptop over UART (Universal Asynchronous Receiver/Transmitter). A Python script running on the laptop reads the serial data and uses matplotlib to plot the logic waveforms live, providing a visual oscilloscope-like experience. The full stack — from RTL design in Vivado to live Python-based waveform plotting — gives users an end-to-end understanding of digital logic behavior, making it useful as both an educational tool and a lightweight hardware debugging instrument.`

---

# 2. Inspiration

## 2.1 References

List what inspired the project.

| Source Type      | Title / Link                                                                 | What Inspired You                                                                              |
| ---------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `[Tool]`         | `Saleae Logic Analyzer`                                                      | `Professional logic analyzers that capture and visualize digital signals in real time`         |
| `[Platform]`     | `Xilinx Vivado / ILA (Integrated Logic Analyzer)`                            | `On-chip signal capture and waveform viewing built into Vivado for FPGA debugging`             |
| `[Course Work]`  | `FPGA Lab — MicroBlaze, Zynq SoC, UART communication`                        | `Hands-on experience with FPGA-based serial communication and embedded design`                 |

## 2.2 Original Twist

What makes your project original?

**Response:**  
`Most logic analyzers are passive measurement tools — they only capture signals from external circuits. This project is a self-contained system where the FPGA itself generates and simulates the digital circuit behavior (gates, adders, SRAMs), and simultaneously streams the waveform data to a PC for real-time plotting. The combination of on-chip RTL simulation + UART streaming + Python-based waveform visualization in a single integrated workflow makes this an original educational and prototyping tool.`

---

# 3. Project Intent

## 3.1 User Journey

Describe exactly how a user will use the project. Make it a story.

**Response:**  
`Rahul, an electronics student, wants to verify how a 4-bit ripple carry adder behaves across all input combinations. He opens Vivado, selects the "4-bit Adder" mode via a switch configuration on the Spartan-7 Boolean board, and programs the FPGA. The FPGA begins sweeping through input combinations and computing carry and sum outputs in hardware. On his laptop, Rahul runs the Python script, which opens a serial port and starts reading the streamed binary data. Within seconds, a matplotlib window appears, displaying clean square-wave waveforms for each input bit, the sum bits, and the carry-out — updating live as the FPGA cycles through inputs. Rahul can now visually confirm glitches, propagation behavior, and output correctness without needing an oscilloscope or external logic analyzer.`

---

# 4. Definition of Success

## 4.1 Definition of "Usable"

`The project is usable when at least one digital circuit (e.g., a basic logic gate) is simulated on the FPGA and its input/output data is correctly transmitted over UART and plotted as waveforms on the laptop screen without data corruption or missing samples.`

## 4.2 Minimum Usable Version

What is the smallest version of this project that still delivers the core experience?

**Response:**  
`A working system where a single logic gate (e.g., AND gate) is synthesized on the FPGA, its inputs and outputs are sampled, transmitted via UART to the laptop, and displayed as a live waveform plot using Python and matplotlib. This MVP validates the full signal chain from FPGA → UART → Python → plot.`

## 4.3 Stretch Features

What features are nice to have but not essential?

- Support for multiple circuit modules selectable via FPGA switches (gate selector)
- SRAM read/write simulation with address and data waveform display
- Triggering support in Python (start capture on a specific signal edge)
- A simple GUI instead of raw matplotlib for waveform display
- Exportable waveform data as CSV or VCD (Value Change Dump) for further analysis

---

# 5. System Overview

## 5.1 Project Type

Check all that apply.

- [x] Electronics-based

- [ ] Mechanical

- [ ] Sensor-based

- [ ] App-connected

- [ ] Motorized

- [ ] Sound-based

- [ ] Light-based

- [x] Screen/UI-based

- [ ] Fabricated structure

- [ ] Game logic based

- [ ] Installation

- [x] Other: FPGA / Digital Hardware Design

## 5.2 High-Level System Description

Explain how the system works in simple terms.

Include:

- input,
- processing,
- output,
- physical structure,
- app interaction if any.

**Response:**  
`Input: Digital test vectors (switch positions or internally generated patterns) are fed as inputs to the synthesized circuit on the FPGA.`

`Processing: The Spartan-7 FPGA (Boolean board) runs RTL logic implemented in Verilog/VHDL — simulating logic gates, adders, or SRAMs. It samples both the inputs and the computed outputs at regular intervals and formats them into a serial data stream.`

`Output: The formatted data is transmitted via UART (USB-to-UART bridge on the board) to the laptop's COM port. A Python script reads this stream, parses the signal values, and plots them as time-domain logic waveforms using matplotlib.`

`Physical Structure: The Spartan-7 Boolean board serves as the hardware platform. It connects to the laptop via a standard USB cable (which carries both power and UART data through an on-board USB-UART bridge).`

`App Interaction: A Python script (waveform_viewer.py) running on the laptop handles serial communication (via pyserial) and real-time plotting (via matplotlib). No external app or Wi-Fi is needed.`

## 5.3 Input / Output Map

| System Part                  | Type     | What It Does                                                        |
| ---------------------------- | -------- | ------------------------------------------------------------------- |
| `FPGA Switches`              | `Input`    | `Select circuit mode and manually set input logic levels`             |
| `RTL Logic (Verilog/VHDL)`   | `Process`  | `Implements and simulates the digital circuit on-chip`                |
| `UART TX (FPGA → Laptop)`    | `Output`   | `Streams sampled input/output waveform data serially to the laptop`   |
| `Python (pyserial)`          | `Process`  | `Receives and parses serial data from the FPGA`                       |
| `matplotlib (Python)`        | `Output`   | `Plots input and output waveforms in real time on the laptop screen`  |
| `FPGA LEDs`                  | `Output`   | `Visual confirmation of output logic levels on-board`                 |

---

# 6. System Design, Sketches and Visual Planning

## 6.1 Concept Architecture / Sketch / Schematic

Add an early sketch of the full idea.

Insert image below:  
`[Upload image and link here]`

```

```

## 6.2 Labeled Build Sketch / Architecture / Flow Diagram / Algorithm

Add a sketch with labels showing:

- structure,
- electronics placement,
- user touch points,
- output elements.

**Insert image below:**  
<img width="2048" height="1365" alt="image" src="https://github.com/user-attachments/assets/96c74820-6ad7-4389-ad0d-ebefde7544bc" />



## 6.3 Approximate Dimensions

| Dimension        | Value                                                  |
| ---------------- | ------------------------------------------------------ |
| Length           | `~152.4 mm (Boolean board PCB)`                          |
| Width            | `~152.4 mm (Boolean board PCB)`                           |
| Height           | `~2.24 mm (with connectors)`                             |

---

# 7. Electronics Planning

## 7.1 Electronics Used

| Component                              | Quantity | Purpose                                                         |
| -------------------------------------- | --------:| --------------------------------------------------------------- |
| `Xilinx Spartan-7 Boolean Board`       | `1`      | Main FPGA platform for RTL synthesis and UART transmission      |
| `USB Cable (USB-A to Micro-USB)`       | `1`      | Power + UART communication between FPGA board and laptop        |
| `Laptop / PC`                          | `1`      | Runs Python script for serial reading and waveform plotting     |
| `DIP Switches (on-board)`             | `—`      | Select circuit mode and set manual input logic levels           |
| `LEDs (on-board)`                     | `—`      | Real-time output indicator for logic levels on the board        |

## 7.2 Wiring Plan

Describe the main electrical connections.

**Response:**  
`The Spartan-7 Boolean board is connected to the laptop via a USB cable. The on-board USB-to-UART bridge exposes the FPGA's UART TX/RX pins to the laptop as a virtual COM port. The FPGA's UART TX pin (mapped in the XDC constraints file) is internally connected to this bridge.`

`Within the FPGA fabric, the synthesized RTL module takes input from the on-board DIP switches and drives output to on-board LEDs and to the UART formatter module. The UART formatter serializes the sampled input/output bus values at a configured baud rate and sends them out through the TX line.`

`No external wiring or breadboarding is required — the entire signal path is internal to the board or handled through the USB cable.`

## 7.3 Circuit Diagram / Architecture Diagram

Insert a hand-drawn or software-made circuit diagram.

**Insert image below:**  
`[Upload image and link here]`

## 7.4 Power Plan

| Question         | Response                                                                                      |
| ---------------- | --------------------------------------------------------------------------------------------- |
| `Power source`     | `USB power from laptop (5V via USB cable to Boolean board)`                                    |
| `Voltage required` | `3.3V / 1.0V internally on FPGA (regulated on-board from 5V USB)`                             |
| `Current concerns` | `Minimal — FPGA logic and UART consume well within USB 500mA limit`                           |
| `Safety concerns`  | `Avoid hot-plugging with incorrect USB cables; ensure USB-UART drivers are correctly installed`|

---

# 8. Software Planning

## 8.1 Software Tools

| Tool / Platform         | Purpose                                                          |
| ----------------------- | ---------------------------------------------------------------- |
| `Xilinx Vivado`         | `RTL design, synthesis, implementation, and bitstream generation`  |
| `Vitis`        | `Hardware description language for logic circuit implementation`   |
| `Python`            | `Serial communication and waveform plotting on the laptop`         |
| `pyserial `     | `Reading UART data from the FPGA via the COM port`                 |
| `matplotlib`    | `Real-time plotting of logic waveforms`                            |
| `numpy`        | `Signal data buffering and manipulation`                           |

## 8.2 Software Logic / Algorithm

Describe what the code must do.

Include:

- startup behavior,
- input handling,
- sensor reading,
- decision logic,
- output behavior,
- communication logic,
- reset behavior.

**Response:**  

- **Startup behavior (FPGA):**  
   Upon powering the Spartan-7 board, the system initiates a Power-On Reset (POR) sequence using a 4-cycle Global Set/Reset (GSR) shift register (rst_sr). This ensures all internal flip-flops, UART transmission state machines, and SRAM cell registers initialize to a known, stable zero state before accepting inputs.

- **Input handling (FPGA):**  
  Input handling operates continuously on every positive clock edge. The system reads the states of the 16 onboard slide switches (sw[15:0]). The switches are logically partitioned: sw[15:14] act as the mode selector (multiplexer control), sw[13:12] toggle advanced debugging features, and sw[2:0] act as the physical inputs (A, B, Cin, WL, D, WE) routed directly to the logic circuits. A 2-Flip-Flop synchronizer safely handles the physical debouncing and edge detection for sw[0].

- **Sensor/State Reading:**  
  While the system does not utilize external environmental sensors, it actively "senses" and captures internal hardware metrics. It calculates propagation delay by counting clock cycles between an input edge and an output change, and acts as a glitch detector by measuring pulse widths on the input pins to flag anomalies shorter than 50ns (5 clock cycles).

- **Decision Logic:**
    The core decision logic is handled by a high-speed multiplexer (implemented as a case statement). Based on the mode bits (sw[15:14]), the logic instantly decides which digital circuit (Inverter, Logic Gates, 1-bit Full Adder, or 6T SRAM model) has active control over the output buses. All logic gates are evaluated in parallel continuously, but the decision logic determines which result is latched for output.
  
- **Output Behavior:**
    Output behavior is split into two immediate hardware responses. First, the resulting logic states are routed directly to the onboard LEDs (led[5:0]) for instantaneous visual feedback. Second, the input and output states are converted from binary to hexadecimal and routed to a 1kHz multiplexed 7-segment display driver, driving the anodes and cathodes to display the current states.

- **Communication Logic:**
    The communication logic relies on an 8N1 UART transmitter operating at 115200 baud. A periodic timer checks whether 200ms has passed or if any physical switch has changed state. If either condition is true, a trigger fires. The system latches the current inputs, outputs, mode string, and metrics, formatting them into a strict 72-byte JSON string (e.g., {"m":"GATE","i":"01","o":"3F",...}\n). A 3-state Finite State Machine (FSM) then kicks in, shifting this packet out byte-by-byte to the PC.

- **Reset Behavior:**
    When the internal reset is triggered, the system immediately aborts any active UART transmissions and resets the packet FSM to the IDLE state. The internal 6T SRAM behavioral latch (sram_q), propagation counters, glitch flags, and edge detection synchronizers are forcefully cleared to 0, readying the board for a fresh experiment.

## 8.3 Code Flowchart

Insert a flowchart showing your code logic.

**Insert image below:**  
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/37810154-e481-41ca-bc97-08edd52d618d" />
---

# 9. Bill of Materials

## 9.1 Full BOM

| Item                                  | Quantity | In Kit? | Need to Buy? | Estimated Cost | Material / Spec                  | Why This Choice?                          |
| ------------------------------------- | --------:| ------- | ------------ | --------------:| -------------------------------- | ----------------------------------------- |
| `Xilinx Spartan-7 Boolean Board`      | `1`      | `Yes`   | `No`         | `0`            | `Spartan-7 XC7S50`               | `Lab-provided FPGA board for the project` |
| `USB Cable (USB-A to Micro-USB)`      | `1`      | `Yes`   | `No`         | `0`            | `Standard Micro-USB`             | `Power + UART over single cable`          |
| `Laptop / PC`                         | `1`      | `Yes`   | `No`         | `0`            | `Any OS with Python 3 + Vivado`  | `Waveform display and Vivado toolchain`   |
| `Python Libraries (pyserial, matplotlib, numpy)` | `—` | `No` | `No (free)` | `0`       | `pip installable`                | `Serial communication and waveform plot`  |

## 9.2 Material Justification

Explain why you selected your main materials and components.

**Response:**  
The Spartan-7 Boolean board was chosen as it is the lab-standard FPGA platform for this project, equipped with adequate LUT resources for synthesizing adders and small SRAMs. Its on-board USB-UART bridge eliminates the need for any external USB-to-serial adapter. Python was chosen for the laptop-side application due to its rich ecosystem — `pyserial` handles serial communication cleanly, `matplotlib` enables rapid live plotting, and `numpy` facilitates efficient signal buffering. The entire BOM is zero additional cost as all components are available in the lab kit.

## 9.3 Items to Procure

| Item                 | Why Needed               | Purchase Link | Latest Safe Date to Procure | Status       |
| -------------------- | ------------------------ | ------------- | --------------------------- | ------------ |
| `Not applicable`     | `All items are in-lab`   | `—`           | `—`                         | `—`          |

## 9.4 Budget Summary

| Budget Item           | Estimated Cost |
| --------------------- | -------------: |
| Electronics           | `₹0`           |
| Mechanical parts      | `₹0`           |
| Fabrication materials | `₹0`           |
| Purchased extras      | `₹0`           |
| Contingency           | `₹0`           |
| **Total**             | `₹0`           |

## 9.5 Budget Reflection

If your cost is too high, what can be simplified, removed, substituted, or shared?

**Response:**  
Not applicable — the entire project uses lab-provided hardware (Spartan-7 Boolean board, USB cable, laptop) and free open-source software tools (Vivado, Python, pyserial, matplotlib). There are no procurement costs.

---

# 10. Planning the Work

## 10.1 Team Working Agreement

Write how your team will work together.

Include:

- how tasks are divided,
- how decisions are made,
- how progress will be checked,
- what happens if a task is delayed,
- how documentation will be maintained.

**Response:**  
Tasks are split by domain: FPGA RTL design and Vivado implementation is handled primarily by one member, while Python serial communication and waveform plotting is handled by the other. Both members participate in integration and testing. Decisions are made jointly during short sync-ups at the start and end of each work session. Progress is tracked by checking off tasks in Section 10.2. If a task is delayed, the other member assists or the scope is reduced to the MVP (single gate simulation). Documentation is maintained continuously in this README throughout the build period.

| Task ID | Task | Owner | Estimated Hours | Deadline | Dependency | Status |
| ------- | ---- | ----- | ---------------: | -------- | ---------- | ------ |
| T1 | `Finalize project concept` | `Team` | `2` | `Day 1` | `None` | `Done` |
| T2 | `Design logic gate selection system` | `Shreya` | `3` | `Day 1` | `T1` | `In progress` |
| T3 | `Implement basic gates on FPGA` | `Shreya` | `4` | `Day 2` | `T2` | `In progress` |
| T4 | `Create UART data format` | `Varunraj / Shreya` | `3` | `Day 2` | `T3` | `Pending` |
| T5 | `Develop Python serial receiver` | `Vibhuti` | `3` | `Day 2` | `T4` | `Pending` |
| T6 | `Plot waveforms using Matplotlib` | `Vibhuti / Faiza` | `4` | `Day 3` | `T5` | `Pending` |
| T7 | `Test truth table correctness` | `Varunraj / Faiza` | `3` | `Day 3` | `T3, T6` | `Pending` |
| T8 | `Complete documentation` | `Varunraj` | `3` | `Day 4` | `Testing` | `In progress` |
| T9 | `Final demo preparation` | `Team` | `2` | `Day 4` | `All tasks` | `Pending` |

## 10.3 Responsibility Split

| Area | Main Owner | Support Owner |
| ---- | ---------- | ------------- |
| Concept | `Faiza` | `Varunraj` |
| Electronics | `Shreya` | `Faiza` |
| Coding | `Shreya` | `Vibhuti` |
| Visualization | `Vibhuti` | `Varunraj` |
| Testing | `Varunraj` | `Faiza` |
| Documentation | `Varunraj` | `Faiza` |

---


---

# 11. Hour Milestones

## 11.1 8-Hour Plan (tentative)

### Bi Hour 1 — Plan and De-risk

Expected outcomes:

- [x] Idea finalized
- [x] Core interaction decided (gate simulation + UART + matplotlib)
- [x] System block diagram sketched
- [x] BOM completed
- [x] Vivado project created and Boolean board constraints loaded
- [ ] Key uncertainty identified (UART baud rate stability, Python COM port setup)
- [x] Basic feasibility tested (Hello World UART transmit)

### Bi Hour 2 — Build Subsystems

Expected outcomes:

- [ ] RTL gate modules written and simulated in Vivado
- [ ] UART TX module written and tested in simulation
- [ ] Python pyserial script reads dummy data from COM port
- [ ] matplotlib waveform plot renders static data correctly

### Bi Hour 3 — Integrate

Expected outcomes:

- [ ] Bitstream programmed to Boolean board
- [ ] FPGA transmitting live data over UART
- [ ] Python script receives and plots live gate waveforms
- [ ] First working demo: AND gate input/output plotted live

### Bi Hour 4 — Refine and Finish

Expected outcomes:

- [ ] Adder modules integrated and waveforms verified
- [ ] SRAM module attempted (stretch goal)
- [ ] Waveform display cleaned up (labels, colors, axis formatting)
- [ ] Documentation completed
- [ ] Final build ready for review

## 12 Update Log

| Days | Planned Goal | What Actually Happened | What Changed | Next Steps |
| ---- | ------------ | ---------------------- | ------------ | ---------- |
| Day 1 | `Finalize concept and system architecture` | `Project idea was finalized as FPGA-based DVLSI waveform visualization platform` | `Shifted focus from frontend-only simulation to FPGA + Python integration` | `Start FPGA logic implementation` |
| Day 2 | `Implement gates and decide communication format` | `Basic gate logic and ASCII UART format were planned` | `UART data format simplified to plain text for easy Python parsing` | `Test UART transmission` |
| Day 3 | `Connect FPGA output to Python plotting` | `Python visualization approach using Matplotlib was finalized` | `Waveform plotting chosen instead of HDMI/VGA display` | `Verify waveforms with truth table` |
| Day 4 | `Prepare final demo and documentation` | `README and explanation were refined for submission` | `Advanced circuits moved to stretch features` | `Complete final testing and submit` |

---


# 13. Risks and Unknowns

## 13.1 Risk Register

| Risk                                                                 | Type        | Likelihood | Impact | Mitigation Plan| Owner      |
| -------------------------------------------------------------------- | ----------- | ---------- | ------ | ----------------------------------------------------------------------------------------------------- | ---------- |
| `UART baud rate mismatch causes corrupted waveform data`             | `Technical` | `Medium`   | `High` | Match baud rate exactly on both FPGA and Python side; add a known start byte for frame synchronization | `Member 1` |
| `Python matplotlib not fast enough for real-time updates`            | `Technical` | `Medium`   | `Medium` | Use `plt.pause()` with a small interval; consider buffering N samples before plotting               | `Member 2` |
| `Vivado timing constraints fail for UART at target frequency`        | `Technical` | `Low`      | `High` | Use a clock divider for UART baud generation; avoid relying on PLL for low baud rates               | `Member 1` |
| `COM port not recognized on laptop (driver issue)`                   | `Technical` | `Low`      | `High` | Pre-install CH340/CP2102 USB-UART drivers; test connection before building further                  | `Member 2` |
| `SRAM simulation too large for Spartan-7 LUT resources`              | `Technical` | `Medium`   | `Low`  | Reduce SRAM depth (e.g., 16×8 bits); use FPGA BRAM primitives instead of LUT-based RAM             | `Member 1` |

## 13.2 Biggest Unknown Right Now

What is the single biggest uncertainty in your project at this stage?

**Response:**  
`The biggest uncertainty is whether the Python-side real-time plotting will be fast enough to display waveforms smoothly at the chosen UART transmission rate. If matplotlib updates are too slow relative to the incoming data rate, frames may be dropped or the plot may lag significantly. This will need to be tested early and may require adjusting the FPGA's data transmission interval.`

---

# 14. Testing

## 14.1 Technical Testing Plan

| What Needs Testing                         | How You Will Test It                                                                      | Success Condition                                                                                       |
| ------------------------------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `UART transmission from FPGA`              | `Connect to laptop and use a serial terminal (e.g., PuTTY or CoolTerm) to read raw bytes` | `Correct bytes received matching expected input/output values`                                          |
| `Python serial reader`                     | `Send known test frames from a mock source and verify parsed values`                      | `All fields decoded correctly with no frame sync errors`                                                |
| `Waveform plot (static)`                   | `Plot pre-recorded data arrays and verify visual correctness`                             | `Square wave waveforms render correctly with proper logic levels (0/1)`                                 |
| `Live gate simulation (AND gate)`          | `Toggle FPGA switches and observe waveform changes in real time on the laptop`            | `Waveform updates within < 200 ms of switch toggle; output matches expected truth table`               |
| `Adder simulation`                         | `Feed all 16 input combinations to 4-bit adder and compare waveform output to truth table`| `Sum and carry outputs match expected values for all input combinations`                               |
| `SRAM read/write (stretch)`                | `Write known data to address locations, then read back and verify on the waveform display` | `Read data matches written data; address and data bus waveforms are correctly displayed`               |

## 14.2 Testing and Debugging Log

| Date | Problem Found | Type | What You Tried | Result | Next Action |
| ---- | ------------- | ---- | -------------- | ------ | ----------- |
| `Day 1` | `Need to decide display method` | `Design` | `Compared HDMI/VGA and Python plotting` | `Python plotting selected as simpler option` | `Implement UART data transfer` |
| `Day 2` | `ASCII format needed for UART` | `Technical` | `Designed simple format like NAND,101` | `Format finalized` | `Test with Python serial reader` |
| `Day 3` | `Waveform needs channel separation` | `Software` | `Separated A, B, and Y into different arrays` | `Plotting method finalized` | `Connect live FPGA data` |
| `Day 4` | `Documentation needed correction` | `Documentation` | `Removed old car/projector content` | `README aligned with FPGA project` | `Final review` |

---


## 14.3 Playtesting Notes

| Tester      | What They Did                                    | What Confused Them                            | What They Enjoyed                                 | What You Will Change                          |
| ----------- | ------------------------------------------------ | --------------------------------------------- | ------------------------------------------------- | --------------------------------------------- |
| `[Write here]` | `Toggled switches and observed waveform plot` | `[Write here]`                               | `[Write here]`                                   | `[Write here]`                                |

---

# 15. Build Documentation

## 15.1 Fabrication Process (if any)

Describe how the project was physically made.

**Response:**  
`No major fabrication process was required because the project mainly uses an FPGA development board and a laptop. The physical setup consists of placing the FPGA board on the workbench, connecting it to the laptop through USB, and using the onboard switches and LEDs for interaction.`

`The main build process involved FPGA logic design, UART communication setup, and Python waveform visualization. The FPGA design was created using Vivado/Vitis, while the Python program was developed to receive serial data and plot waveforms using Matplotlib.`

`Minor setup work included labeling the switches for input A, input B, and gate selection so that users can understand how to interact with the board. The system was revised by simplifying the display method from direct HDMI/VGA output to laptop-based Python visualization, making the project easier to implement and demonstrate within the available time.`

## 16. Build Photos

Add photos throughout the project.

Suggested images:

- Vivado RTL schematic screenshot,
- Vivado simulation waveform screenshot,
- Boolean board programmed and running,
- Python terminal showing received serial data,
- matplotlib waveform window screenshot,
- full setup (board + laptop side by side).

`[Upload images and link here]`

---

# 17. Final Outcome

## 17.1 Final Description

Describe the final version of your project.

**Response:**  
`[Write here after project completion]`

## 17.2 What Works Well

`[Write here after project completion]`

## 17.3 What Still Needs Improvement

`[Write here after project completion]`

## 17.4 What Changed From the Original Plan

How did the project change from the initial idea?

**Response:**  
`[Write here after project completion]`

---

# 18. Reflection

## 18.1 Team Reflection

What did your team do well?  
What slowed you down?  
How well did you manage time, tasks, and responsibilities?

**Response:**  
`[Write here after project completion]`

## 18.2 Technical Reflection

What did you learn about:

- electronics,
- coding,
- mechanisms,
- fabrication,
- integration?

**Response:**  
`[Write here after project completion]`

## 18.3 Design Reflection

What did you learn about:

- designing,
- delight,
- clarity,
- physical interaction,
- understanding,
- iteration?

**Response:**  
`[Write here after project completion]`

## 18.4 If You Had One More Hour

What would you improve next?

**Response:**  
`[Write here after project completion]`

---

# 19. Final Submission Checklist

Before submission, confirm that:

- [x] Team details are complete
- [x] Project description is complete
- [x] Inspiration sources are included
- [x] Sketches / block diagrams are added
- [x] BOM is complete
- [x] Budget summary is complete
- [ ] Vivado RTL schematic screenshot is added
- [ ] Vivado simulation waveform screenshot is added
- [x] Code flowchart is added
- [x] Task breakdown is complete
- [ ] Update log is filled in
- [x] Risk register is complete
- [ ] Testing log is updated
- [ ] Build photos are included
- [ ] Final reflection is written

---

