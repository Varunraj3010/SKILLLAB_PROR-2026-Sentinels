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

`An FPGA-based logic analyzer that simulates digital circuits and streams real-time input/output waveforms to a laptop via UART for live visualization using Python and matplotlib.`

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
`Most logic analyzers are passive measurement tools — they only capture signals from external circuits. This project is a self-contained system where the FPGA itself generates and simulates the digital circuit behavior (gates, adders), and simultaneously streams the waveform data to a PC for real-time plotting. The combination of on-chip RTL simulation + UART streaming + Python-based waveform visualization in a single integrated workflow makes this an original educational and prototyping tool.`

---

# 3. Project Intent

## 3.1 User Journey

Describe exactly how a user will use the project. Make it a story.

**Response:**  
`Rahul, an electronics student, wants to verify how a 4-bit adder behaves across all input combinations. He opens Vivado, selects the "4-bit Adder" mode via a switch configuration on the Spartan-7 Boolean board, and programs the FPGA. The FPGA begins sweeping through input combinations and computing carry and sum outputs in hardware. On his laptop, Rahul runs the Python script, which opens a serial port and starts reading the streamed binary data. Within seconds, a matplotlib window appears, displaying clean square-wave waveforms for each input bit, the sum bits, and the carry-out — updating live as the FPGA cycles through inputs. Rahul can now visually confirm glitches, propagation behavior, and output correctness without needing an oscilloscope or external logic analyzer.`

---

# 4. Definition of Success

## 4.1 Definition of "Usable"

`The project is usable when at least one digital circuit (e.g., a basic logic gate) is simulated on the FPGA and its input/output data is correctly transmitted over UART and plotted as waveforms on the laptop screen without data corruption or missing samples.`

## 4.2 Minimum Usable Version

What is the smallest version of this project that still delivers the core experience?

**Response:**  
`A working system where a single logic gate (e.g., NAND gate) is synthesized on the FPGA, its inputs and outputs are sampled, transmitted via UART to the laptop, and displayed as a live waveform plot using Python and matplotlib. This validates the full signal chain from FPGA → UART → Python → plot.`

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
`Input: Digital test vectors (switch positions) are fed as inputs to the synthesized circuit on the FPGA.`

`Processing: The Spartan-7 FPGA (Boolean board) runs RTL logic implemented in Verilog/VHDL — simulating logic gates or adders. It samples both the inputs and the computed outputs at regular intervals and formats them into a serial data stream.`

`Output: The formatted data is transmitted via UART (USB-to-UART bridge on the board) to the laptop's COM port. A Python script reads this stream, parses the signal values, and plots them as time-domain logic waveforms using matplotlib.`

`Physical Structure: The Spartan-7 Boolean board serves as the hardware platform. It connects to the laptop via a standard USB cable (which carries both power and UART data through an on-board USB-UART bridge).`

`App Interaction: A Python script (app.py) running on the laptop handles serial communication (via pyserial) and real-time plotting (via matplotlib). No external app or Wi-Fi is needed.`

## 5.3 Input / Output Map

| System Part                  | Type     | What It Does                                                        |
| ---------------------------- | -------- | ------------------------------------------------------------------- |
| `FPGA Switches`              | `Input`    | `Select circuit mode and manually set input logic levels`             |
| `RTL Logic (Verilog/VHDL)`   | `Process`  | `Implements and simulates the digital circuit on-chip`                |
| `UART TX (FPGA → Laptop)`    | `Output`   | `Streams sampled input/output waveform data serially to the laptop`   |
| `Python (pyserial)`          | `Process`  | `Receives and parses serial data from the FPGA`                       |
| `matplotlib (Python)`        | `Output`   | `Plots input and output waveforms in real time on the laptop screen`  |

---

# 6. System Design, Sketches and Visual Planning

## 6.1 Concept Architecture / Sketch / Schematic

Add an early sketch of the full idea.

Insert image below:  

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
| `Laptop`                          | `1`      | Runs Python script for serial reading and waveform plotting     |
| `Switches (on-board)`             | `—`      | Select circuit mode and set manual input logic levels           |

## 7.2 Wiring Plan

Describe the main electrical connections.

**Response:**  
`The Spartan-7 Boolean board is connected to the laptop via a USB cable. The on-board USB-to-UART bridge exposes the FPGA's UART TX/RX pins to the laptop as a virtual COM port. The FPGA's UART TX pin (mapped in the XDC constraints file) is internally connected to this bridge.`

`Within the FPGA fabric, the synthesized RTL module takes input from the on-board DIP switches and drives output to on-board LEDs and to the UART formatter module. The UART formatter serializes the sampled input/output bus values at a configured baud rate and sends them out through the TX line.`

`No external wiring or breadboarding is required — the entire signal path is internal to the board or handled through the USB cable.`

## 7.3 Circuit Diagram / Architecture Diagram

Insert a hand-drawn or software-made circuit diagram.

**Insert image below:**  
<img width="1562" height="729" alt="image" src="https://github.com/user-attachments/assets/062db688-241a-41d0-b6d4-cbf2e3eda879" />

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
| `Laptop`                         | `1`      | `Yes`   | `No`         | `0`            | `Any OS with Python 3 + Vivado`  | `Waveform display and Vivado toolchain`   |
| `Python Libraries (pyserial, matplotlib, numpy)` | `—` | `No` | `No (free)` | `0`       | `pip installable`                | `Serial communication and waveform plot`  |

## 9.2 Material Justification

Explain why you selected your main materials and components.

**Response:**  
The Spartan-7 Boolean board was chosen as the lab-standard FPGA platform for this project, equipped with sufficient LUT resources for synthesizing adders. Its on-board USB-UART bridge eliminates the need for any external USB-to-serial adapter. Python was chosen for the laptop-side application due to its rich ecosystem — pyserial handles serial communication cleanly, matplotlib enables rapid live plotting, and numpy facilitates efficient signal buffering.

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
| T2 | `Design logic gate selection system` | `Shreya` | `1` | `Day 1` | `T1` | `In progress` |
| T3 | `Implement basic gates on FPGA` | `Shreya` | `2.5` | `Day 1` | `T2` | `In progress` |
| T4 | `Create UART data format` | `Shreya/Vibhuti` | `2` | `Day 1` | `T3` | `In progress` |
| T5 | `Develop Python serial receiver` | `Vibhuti` | `1` | `Day 1` | `T4` | `Done` |
| T6 | `Plot waveforms using Matplotlib` | `Vibhuti / Faiza` | `3` | `Day 1` | `T5` | `In progress` |
| T7 | `Test truth table correctness` | `Varunraj / Faiza` | `3` | `Day 2` | `T3, T6` | `Pending` |
| T8 | `Complete documentation` | `Varunraj` | `3` | `Day 2` | `Testing` | `In progress` |
| T9 | `Final demo preparation` | `Team` | `2` | `Day 2` | `All tasks` | `Pending` |

## 10.3 Responsibility Split

| Area | Main Owner | Support Owner |
| ---- | ---------- | ------------- |
| Concept | `Faiza` | `Shreya` |
| Electronics | `Shreya` | `Faiza` |
| Coding | `Vibhuti` | `Varunraj` |
| Visualization | `Vibhuti` | `Varunraj` |
| Testing | `Shreya` | `Vibhuti` |
| Documentation | `Varunraj` | `-` |

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

## 12. Update Log

| Days | Planned Goal | What Actually Happened | What Changed | Next Steps |
| ---- | ------------ | ---------------------- | ------------ | ---------- |
| Day 1 | `Finalize concept and system architecture` | `Project idea was finalized as an FPGA-based live logic analyzer and waveform visualization dashboard` | `Shifted focus from frontend-only simulation to real FPGA + UART + browser-based visualization` | `Start FPGA RTL implementation` |
| Day 2 | `Implement gates and decide communication format` | `Basic logic gate operations and UART packet format were planned` | `UART data format was simplified to comma-separated ASCII text for easy Python parsing` | `Test UART output using serial terminal` |
| Day 3 | `Build software dashboard` | `Python Flask backend and HTML/CSS/JavaScript frontend were created in VS Code` | `Display method changed from Matplotlib plotting to a browser-based live waveform dashboard` | `Connect backend to COM13 serial data` |
| Day 4 | `Implement FPGA UART transmission` | `Verilog RTL modules for logic selection, baud generation, and UART transmission were created in Vivado` | `Pure RTL FPGA implementation was selected as the main implementation path` | `Fix constraints and generate bitstream` |
| Day 5 | `Prepare final demo and documentation` | `README, flowchart, testing plan, and build documentation were refined` | `Advanced/stretch features were separated from the core demo` | `Complete final hardware testing and record demo output` |

---


# 13. Risks and Unknowns

## 13.1 Risk Register

| Risk | Type | Likelihood | Impact | Mitigation Plan | Owner |
| ---- | ---- | ---------- | ------ | --------------- | ----- |
| `UART baud rate mismatch causes corrupted waveform data` | `Technical` | `Medium` | `High` | Keep FPGA baud generator and Python backend baud rate fixed at 115200; verify using a serial terminal before running the dashboard | `Member 1` |
| `Incorrect FPGA pin constraints prevent bitstream generation` | `Technical` | `Medium` | `High` | Verify clock, switch, and UART TX pins from the Spartan-7 board documentation before implementation | `Member 1` |
| `COM13 not recognized or occupied by another program` | `Technical` | `Medium` | `High` | Close Vivado serial terminal or other COM port tools before running the Flask backend; verify COM13 in Device Manager | `Member 2` |
| `Browser dashboard does not update smoothly` | `Software` | `Low` | `Medium` | Limit stored samples, use periodic fetch requests, and keep waveform rendering lightweight using JavaScript Canvas | `Member 2` |
| `FPGA output does not match truth table` | `Technical` | `Low` | `High` | Test each logic mode using all input combinations and compare A, B, Y, and Carry with expected values | `Member 1` |
| `UART TX pin mapping is incorrect` | `Technical` | `Medium` | `High` | Confirm the actual FPGA package pin for UART TX rather than relying only on board labels | `Member 1` |

## 13.2 Biggest Unknown Right Now

**Response:**  
`The biggest uncertainty at this stage is whether the FPGA UART TX pin and board constraints are correctly mapped for the selected Spartan-7 device. The RTL logic has been created, but successful bitstream generation and live waveform output depend on correct clock, switch, and UART pin assignments. Once the bitstream is generated and the board is connected through COM13, the Python Flask dashboard can be tested with real FPGA data.`

---

# 14. Testing

## 14.1 Technical Testing Plan

| What Needs Testing | How You Will Test It | Success Condition |
| ------------------ | -------------------- | ----------------- |
| `Verilog logic operations` | `Simulate or manually test switch combinations for AND, OR, XOR, and Half Adder modes` | `Output Y and Carry match the expected truth table` |
| `UART baud generation` | `Check that FPGA baud generator uses the same baud rate as Python backend, preferably 115200` | `Serial data is readable without corrupted characters` |
| `UART transmission from FPGA` | `Connect board through USB and open COM13 in a serial terminal such as PuTTY or CoolTerm` | `Packets like AND,1,0,0,0 are received correctly` |
| `Python Flask serial backend` | `Run app.py and check whether COM13 shows CONNECTED` | `Backend receives FPGA UART packets and stores samples` |
| `Browser waveform dashboard` | `Open http://127.0.0.1:5000 and toggle FPGA switches` | `A, B, Y/SUM, and Carry waveforms update live` |
| `Gate output verification` | `Test all input combinations for each selected gate mode` | `Displayed output matches the expected Boolean operation` |
| `Half Adder verification` | `Set Half Adder mode and test A/B combinations 00, 01, 10, 11` | `SUM = A XOR B and Carry = A AND B` |
| `CSV export` | `Click Export CSV on the dashboard after receiving samples` | `waveform.csv is generated with Gate, A, B, Y, and C fields` |

## 14.2 Testing and Debugging Log

| Date | Problem Found | Type | What You Tried | Result | Next Action |
| ---- | ------------- | ---- | -------------- | ------ | ----------- |
| `Day 1` | `Need to decide display method` | `Design` | `Compared VGA/HDMI, Matplotlib, and browser dashboard approaches` | `Browser dashboard selected as the most flexible option` | `Build Flask backend and frontend UI` |
| `Day 2` | `Need simple UART format` | `Technical` | `Designed ASCII packet format like AND,1,0,0,0` | `Format finalized for easy backend parsing` | `Implement UART transmitter in Verilog` |
| `Day 3` | `Waveform needs channel separation` | `Software` | `Separated A, B, Y/SUM, and Carry into independent waveform channels` | `Dashboard waveform structure finalized` | `Connect live FPGA data` |
| `Day 4` | `Synthesis issue due to switch width mismatch` | `RTL` | `Corrected switch mapping and top module input width` | `Synthesis passed` | `Run implementation and generate bitstream` |
| `Day 5` | `Bitstream issue due to invalid UART TX pin` | `Constraints` | `Reviewed .xdc pin assignments and identified UART TX package pin issue` | `Constraint file requires correction` | `Confirm actual UART TX FPGA package pin from board documentation` |

---


## 14.3 Playtesting Notes

| Tester      | What They Did                                    | What Confused Them                            | What They Enjoyed                                 | What You Will Change                          |
| ----------- | ------------------------------------------------ | --------------------------------------------- | ------------------------------------------------- | --------------------------------------------- |
| `[Write here]` | `Toggled switches and observed waveform plot` | `[Write here]`                               | `[Write here]`                                   | `[Write here]`                                |

---

# 15. Build Documentation

## 15.1 Fabrication Process

**Response:**  
`No major physical fabrication was required because the project uses a Spartan-7 FPGA development board and a laptop. The physical setup consists of connecting the FPGA board to the laptop through the onboard USB-UART interface. The board switches are used as digital inputs, and the laptop displays the live waveform dashboard.`

`The main build process involved two parts: FPGA RTL development and software dashboard development. On the FPGA side, Verilog modules were created in Vivado for selecting Boolean operations, generating baud rates, and transmitting UART data. On the software side, a Python Flask backend was developed in VS Code to read UART data from COM13, and a browser-based frontend was created using HTML, CSS, and JavaScript Canvas to display live waveforms.`

`The project was revised from a simple plotting-based idea to a more complete live web dashboard. This made the system more interactive and presentation-friendly because the waveform, connection status, sample count, selected mode, and CSV export can all be viewed from a single browser interface.`

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
- [x] Sketches/block diagrams are added
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

