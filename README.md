# 1. Team Identity

## 1.1 Studio / Group Name

`Sentinels`

## 1.2 Team Members

| Name                  | Primary Role                    | Secondary Role   | Strengths Brought to the Project       |
| --------------        | ------------------------------- | --------------   | -------------------------------- |
| `Varunraj Bhirud` | `Research` | `Documentation`|`Ideation`|
| `Vibhuti Sawant`| `UI Design`|`Debugging`|`Designing visual platform`|
| `Faiza Shaikh`|`Enhancement research`| `Prototyping`|`Creative thinking`|
| `Shreya Korgaonkar` | `Implementation` | `Debugging`  | `Knowledge of Vitis and Xilinx SDK`|

## 1.3 Project Title

`FPGA-based logic analyzer`

## 1.4 One-Line Pitch

`An FPGA-based logic analyzer that simulates digital circuits and streams real-time input/output waveforms to a laptop via UART for live visualization using Python and matplotlib.`

## 1.5 Expanded Project Idea

`The FPGA Logic Analyzer is a project built on the Xilinx Spartan-7 Boolean board using a MicroBlaze soft-core processor. The system reads input switches through AXI GPIO, computes various digital logic functions (AND, OR, NOT, NAND, NOR, XOR, XNOR) in software using C code running on the MicroBlaze, and periodically streams the input values, computed output, and selected gate type over UART. A Python script on the laptop receives this serial data and plots the logic waveforms in real-time using Matplotlib, providing a live oscilloscope-like view.
This project demonstrates embedded software-based digital logic emulation, MicroBlaze system design in Vivado/SDK, and real-time data visualization, making it a simple yet effective educational tool for understanding digital logic and FPGA-based embedded systems.`

---

# 2. Inspiration

## 2.1 References

| Source Type | Title / Link | What Inspired You |
| :--- | :--- | :--- |
| `[Reference manual]` | `https://www.realdigital.org/doc/02013cd17602c8af749f00561f88ae21` | `Switches pin labelling and configuration` |
| `[Research Paper]` | `Samarasinghe, G. S. (2023). "FPGA-based logic analyzer." International Journal of Mechanics of Solids, 4(1), 15-20.` | `Provided an architectural reference for developing a logic analyzer by interfacing an FPGA with a custom Python GUI via UART communication.`|

## 2.2 Original Twist

**Response:**  
`Most logic analyzers are passive measurement tools — they only capture signals from external circuits. This project is a self-contained system where the FPGA itself generates and simulates the digital circuit behavior (gates, adders), and simultaneously streams the waveform data to a PC for real-time plotting. The combination of on-chip RTL simulation + UART streaming + Python-based waveform visualization in a single integrated workflow makes this an original educational tool.`

---

# 3. Project Intent

## 3.1 User Journey

`Rahul, an electronics student, wants to verify how a half adder behaves across all input combinations. He opens Vivado, selects the "half Adder" mode via a switch configuration on the Spartan-7 Boolean board, and programs the FPGA. The FPGA begins sweeping through input combinations and computing carry and sum outputs in hardware. On his laptop, Rahul runs the Python script, which opens a serial port and starts reading the streamed binary data. Within seconds, a matplotlib window appears, displaying clean square-wave waveforms for each input bit, the sum bits, and the carry-out — updating live as the FPGA cycles through inputs.`

---

# 4. Definition of Success

## 4.1 Definition of "Usable"

`The project is usable when at least one digital circuit (e.g., a basic logic gate) is simulated on the FPGA and its input/output data is correctly transmitted over UART and plotted as waveforms on the laptop screen without data corruption or missing samples.`

## 4.2 Minimum Usable Version

`A working system where a single logic gate (e.g., NAND gate) is synthesized on the FPGA, its inputs and outputs are sampled, transmitted via UART to the laptop, and displayed as a live waveform plot using Python and matplotlib. This validates the full signal chain from FPGA → UART → Python → plot.`

## 4.3 Stretch Features

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

`Input: Digital test vectors (switch positions) are fed as inputs to the synthesized circuit on the FPGA.`

`Processing: The Spartan-7 FPGA (Boolean board) uses a MicroBlaze soft processor running C code to read input switches via AXI GPIO, compute logic gate functions (AND, OR, NAND, NOR, XOR, XNOR) in , and stream the input and output values along with gate name over UART for real-time waveform plotting on a Python/Matplotlib host.`

`Output: The formatted data is transmitted via UART (USB-to-UART bridge on the board) to the laptop's COM port. A Python script reads this stream, parses the signal values, and plots them as time-domain logic waveforms using matplotlib.`

`Physical Structure: The Spartan-7 Boolean board serves as the hardware platform. It connects to the laptop via a standard USB cable (which carries both power and UART data through an on-board USB-UART bridge).`

`App Interaction: A Python script (app.py) running on the laptop handles serial communication (via pyserial) and real-time plotting (via matplotlib). No external app or Wi-Fi is needed.`

## 5.3 Input / Output Map

| System Part                  | Type     | What It Does                                                        |
| ---------------------------- | -------- | ------------------------------------------------------------------- |
| `FPGA Switches`              | `Input`    | `Select circuit mode and manually set input logic levels`             |
| `Logic`                      | `Process`  | `Implements and simulates the digital circuit on-chip`                |
| `UART TX (FPGA → Laptop)`    | `Output`   | `Streams sampled input/output waveform data serially to the laptop`   |
| `Python (pyserial)`          | `Process`  | `Receives and parses serial data from the FPGA`                       |
| `matplotlib (Python)`        | `Output`   | `Plots input and output waveforms in real time on the laptop screen`  |

---

# 6. System Design, Sketches and Visual Planning

## 6.1 Concept Architecture / Sketch / Schematic

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/b6730f54-b78b-44e5-ab81-e15a38a20f08" />

---

## 6.2 Labeled Build Sketch / Architecture / Flow Diagram / Algorithm

<img width="2048" height="1365" alt="image" src="https://github.com/user-attachments/assets/96c74820-6ad7-4389-ad0d-ebefde7544bc" />

## 6.3 Approximate Dimensions

| Dimension        | Value                                                  |
| ---------------- | ------------------------------------------------------ |
| Length           | `~140 mm (Boolean board PCB)`                          |
| Width            | `~95 mm (Boolean board PCB)`                           |
| Height           | `~2 mm`                             |

---

# 7. Electronics Planning

## 7.1 Electronics Used

| Component                              | Quantity | Purpose                                                         |
| -------------------------------------- | --------:| --------------------------------------------------------------- |
| `Xilinx Spartan-7 Boolean Board`       | `1`      | Main FPGA platform for RTL synthesis and UART transmission      |
| `USB Cable (USB-A to Micro-USB)`       | `1`      | Power + UART communication between FPGA board and laptop        |
| `Laptop`                          | `1`      | Runs Python script for serial reading and waveform plotting     |
| `Switches (on-board)`             | `5`      | Select circuit mode and set manual input logic levels           |

## 7.2 Wiring Plan

Describe the main electrical connections.

`The Spartan-7 Boolean board is connected to the laptop via a USB cable. The on-board USB-to-UART bridge exposes the FPGA’s UART as a virtual COM port. The MicroBlaze processor, running C code, reads the on-board switches through AXI GPIO, computes the selected logic function in , and sends the input/output data along with gate information over UART.
No external wiring is required — all inputs come from the onboard switches, outputs are processed internally, and data is transmitted to the laptop through the USB-UART bridge for real-time waveform plotting.`

## 7.3 Circuit Diagram / Architecture Diagram


**Insert image below:**  
<img width="1562" height="729" alt="image" src="https://github.com/user-attachments/assets/062db688-241a-41d0-b6d4-cbf2e3eda879" />

## 7.4 Power Plan

| Question         | Response                                                                                      |
| ---------------- | --------------------------------------------------------------------------------------------- |
| `Power source`     | `USB power from laptop (5V via USB cable to Boolean board)`                                    |
| `Voltage required` | `3.3V / 1.0V internally on FPGA (regulated on-board from 5V USB)`                             |
| `Current concerns` | `Minimal — FPGA logic and UART consume well within USB 500mA limit`                           |
| `Safety concerns`  | `Use a good quality micro-USB cable.`|

---

# 8.  Planning

## 8.1  Tools

| Tool / Platform         | Purpose                                                          |
| ----------------------- | ---------------------------------------------------------------- |
| `Xilinx Vivado`         | `MicroBlaze, AXI GPIO & UART integration, synthesis, implementation, and bitstream generation`  |
| `Vitis`        | `Hardware description language for logic circuit implementation`   |
| `Python`            | `Serial communication and waveform plotting on the laptop`         |
| `pyserial `     | `Reading UART data from the FPGA via the COM port`                 |
| `matplotlib`    | `Real-time plotting of logic waveforms`                            |

## 8.2  Logic / Algorithm

### Python Script Breakdown

- **Startup Behavior**
  - Opens the serial port (`COM13` at 9600 baud)
  - Initializes three deques (`A`, `B`, `Y`) with 50 zero values as waveform history
  - Prints connection status and instructions to the user
  - Sets up a dark-themed Matplotlib figure with 3 subplots

- **Input Handling**
  - Reads incoming data line by line using
  - Parses comma-separated values received from the FPGA
  - Uses try-except to handle corrupted or incomplete data gracefully

- **Sensor Reading**
  - Continuously checks for new UART data
  - Reads input switches (SW0, SW1) and computed output from MicroBlaze
  - Also reads the currently selected gate name

- **Decision Logic**
  - Validates that the line contains valid data
  - Checks that exactly 4 values are received before processing
  - Updates the current gate and appends new values to the waveform buffers

- **Output Behavior**
  - Updates three live step waveforms (Input A, Input B, and Logic Output)
  - Displays the currently selected gate in the plot title
  - Prints received data to console for debugging
  - Uses clear LOW/HIGH labels on Y-axis for better readability

- **Communication Logic**
  - Uses `pyserial` to communicate with the FPGA via UART
  - Reads data asynchronously inside the animation loop
  - Processes all pending data in the serial buffer each frame

- **Reset Behavior**
  - Waveform buffers are automatically reset to zeros when the script starts
  - No runtime reset functionality implemented
  - Serial port is closed when the plot window is closed

### SDK code breakdown

### Python Script Breakdown

- **Startup Behavior**
  - Opens the serial port (`COM13` at `9600` baud).
  - Initializes four rolling buffers using `deque`: `A`, `B`, `OUT`, and `CARRY`.
  - Each buffer stores only the latest `50` samples.
  - Prints connection status and switch/gate instructions in the terminal.
  - Sets up a dark-themed Matplotlib window with four waveform subplots.

- **Input Handling**
  - Reads UART data line by line from the FPGA.
  - Expects comma-separated ASCII data in the format:
  
    A, B, OUT, CARRY, GATE

  - Example received packet:

    1,0,1,0,XOR

  - Uses `try-except` so corrupted or incomplete UART data does not crash the program.

- **Serial Data Reading**
  - Continuously checks whether new UART data is available using `ser.in_waiting`.
  - Reads switch input values `A` and `B`.
  - Reads the computed output from the FPGA/MicroBlaze.
  - Reads the carry signal and currently selected gate name.

- **Decision Logic**
  - Ignores invalid lines and startup messages such as `Ready`.
  - Processes only packets that contain exactly five values.
  - Converts input/output values into integers.
  - Updates the selected gate name based on the received packet.

- **Waveform Buffering**
  - Appends new samples to the `A`, `B`, `OUT`, and `CARRY` buffers.
  - Uses a fixed-size rolling window of `50` samples.
  - Old samples are automatically removed when new samples arrive.
  - Data is stored temporarily in memory only and is not permanently saved to disk.

- **Output Behavior**
  - Updates four live step waveforms:
    - `SW0 (A)`
    - `SW1 (B)`
    - `OUT / SUM`
    - `CARRY`
  - Displays the currently selected gate in the plot title.
  - Labels logic levels as `LOW` and `HIGH` for readability.
  - Prints received values in the terminal for debugging.

- **Half Adder Handling**
  - For normal logic gates, the third waveform represents the gate output.
  - For Half Adder mode (`HADD`), the third waveform represents `SUM`.
  - The fourth waveform represents `CARRY` only in Half Adder mode.
  - For normal gates, carry remains `0`.

- **Communication Logic**
  - Uses `pyserial` for UART communication between the FPGA and laptop.
  - Uses Matplotlib animation to repeatedly update the waveform display.
  - Processes all pending UART data in the serial buffer during each animation frame.

- **Reset Behavior**
  - Waveform buffers are initialized to zeros when the script starts.
  - No separate runtime reset button is implemented.
  - The serial port is closed after the Matplotlib window is closed.

## 8.3 Code Flowchart

Insert a flowchart showing your code logic.

**Insert image below:**  
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/928b48d9-36db-4ed6-87e6-96d0f26e1373" />

---

# 9. Bill of Materials

## 9.1 Full BOM

| Item                                  | Quantity | In Kit? | Need to Buy? | Estimated Cost | Material / Spec                  | Why This Choice?                          |
| ------------------------------------- | --------:| ------- | ------------ | --------------:| -------------------------------- | ----------------------------------------- |
| `Xilinx Spartan-7 Boolean Board`      | `1`      | `Yes`   | `No`         | `0`            | `Spartan-7 XC7S50`               | `Lab-provided FPGA board for the project` |
| `USB Cable (USB-A to Micro-USB)`      | `1`      | `Yes`   | `No`         | `0`            | `Standard Micro-USB`             | `Power + UART over single cable`          |
| `Laptop`                         | `1`      | `Yes`   | `No`         | `0`            | `Any OS with Python 3 + Vivado`  | `Waveform display and Vivado toolchain`   |
| `Python Libraries (pyserial, matplotlib)` | `—` | `No` | `No (free)` | `0`       | `pip installable`                | `Serial communication and waveform plot`  |

## 9.2 Material Justification

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

Not applicable — the entire project uses lab-provided hardware (Spartan-7 Boolean board, USB cable, laptop) and free open-source  tools (Vivado, Python, pyserial, matplotlib). There are no procurement costs.

---

# 10. Planning the Work

## 10.1 Team Working Agreement

Tasks are split by domain: FPGA RTL design and Vivado implementation is handled primarily by one member, while Python serial communication and waveform plotting is handled by the other. Both members participate in integration and testing. Decisions are made jointly during short sync-ups at the start and end of each work session. Progress is tracked by checking off tasks in Section 10.2. If a task is delayed, the other member assists or the scope is reduced to the MVP (single gate simulation). Documentation is maintained continuously in this README throughout the build period.

| Task ID | Task | Owner | Estimated Hours | Deadline | Dependency | Status |
| ------- | ---- | ----- | ---------------: | -------- | ---------- | ------ |
| T1 | `Finalize project concept`          | `Team` | `2` | `Day 1` | `None` | `Done` |
| T2 | `Design logic gate selection system`| `Shreya` | `1` | `Day 1` | `T1` | `In progress` |
| T3 | `Implement basic gates on FPGA`     | `Shreya` | `2.5` | `Day 1` | `T2` | `In progress` |
| T4 | `Create UART data format`           | `Shreya/Vibhuti` | `2` | `Day 1` | `T3` | `In progress` |
| T5 | `Develop Python serial receiver`    | `Vibhuti` | `1` | `Day 1` | `T4` | `Done` |
| T6 | `Plot waveforms using Matplotlib`   | `Vibhuti / Faiza` | `3` | `Day 1` | `T5` | `In progress` |
| T7 | `Test truth table correctness`      | `Varunraj / Faiza` | `3` | `Day 2` | `T3, T6` | `Pending` |
| T8 | `Complete documentation`            | `Varunraj` | `3` | `Day 2` | `Testing` | `In progress` |
| T9 | `Final demo preparation`            | `Team` | `2` | `Day 2` | `All tasks` | `Pending` |

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

# 11. Hour Milestones

## 11.1 8-Hour Plan (tentative)

### Bi Hour 1

Expected outcomes:

- [x] Idea finalized
- [x] Core interaction decided (gate simulation + UART + matplotlib)
- [x] System block diagram sketched
- [x] BOM completed
- [ ] Vivado project created and Boolean board constraints loaded
- [ ] Key uncertainty identified (UART baud rate stability, Python COM port setup)
- [ ] Basic feasibility tested (Hello World UART transmit)

### Bi Hour 2 — Build Subsystems

Expected outcomes:

- [x] Basic feasibility tested (Hello World UART transmit from MicroBlaze)
- [x] MicroBlaze system created with AXI GPIO and UART in Vivado
- [x] C code implemented for switch reading, logic computation, and UART transmission
- [ ] Python script successfully reads serial data using pyserial
- [ ] Matplotlib waveform plotting works with live data

### Bi Hour 3 — Integrate

Expected outcomes:

- [x] Bitstream programmed to Boolean board
- [x] FPGA transmitting live data over UART
- [x] Python script receives and plots live gate waveforms
- [x] First working demo: NAND gate input/output plotted live

### Bi Hour 4 — Refine and Finish

Expected outcomes:
- [x] Live display of waveform
- [x] Waveform display cleaned up
- [ ] Documentation completed
- [x] Final build ready for review

## 12. Update Log

| Days | Planned Goal | What Actually Happened | What Changed | Next Steps |
|------|--------------|------------------------|--------------|----------|
| Day 1 | Finalize concept and system architecture | Project finalized as FPGA-based Logic Analyzer using MicroBlaze + live waveform visualization | Shifted from pure RTL to MicroBlaze + C  implementation for faster development | Create MicroBlaze system in Vivado and write basic C code |
| Day 2 | Implement logic, UART communication, and Python visualization | MicroBlaze C code for gate logic + UART transmission completed. Python script with pyserial + Matplotlib live plotting successfully implemented | Dropped browser-based dashboard in favor of Matplotlib for simplicity and real-time performance. Logic functions implemented in C instead of Verilog RTL | Testing with different gate combinations and preparing documentation |

---


# 13. Risks and Unknowns

## 13.1 Risk Register

| Risk | Type | Likelihood | Impact | Mitigation Plan | Owner |
|------|------|------------|--------|-----------------|-------|
| UART baud rate mismatch causes corrupted data | Technical | Medium | High | Fix baud rate at 9600 (or 115200) in both MicroBlaze C code and Python script | Vibhuti/Shreya |
| Incorrect FPGA pin constraints for switches or UART | Technical | Medium | High | Double-check XDC constraints file with Boolean board documentation for GPIO and UART pins | Vibhuti/Shreya |
| COM port (COM13) not recognized or already in use | Technical | Medium | High | Close Vivado Serial Terminal and other tools before running Python script; verify port in Device Manager | Varunraj/Faiza |
| Matplotlib waveform plot not updating smoothly |  | Low | Medium | Reduce MAX_POINTS, optimize animation interval, and limit data processing per frame |Vibhuti|
| Logic output does not match expected truth table | Technical | Low | High | Thoroughly test each gate with all input combinations in C code and verify on hardware | Varunraj |
| MicroBlaze system fails to generate bitstream or program | Technical | Medium | High | Validate AXI GPIO and UART IP configuration in Vivado Block Design before generating bitstream | Faiza/Shreya |

## 13.2 Biggest Unknown Right Now

The biggest uncertainty at this stage is whether the UART communication works reliably between the MicroBlaze processor and the Python script. Although the MicroBlaze system has been created and the C code is ready, successful programming and live data transmission depend on correct UART setup and stable communication over COM13.
Once the bitstream is generated and the board is connected, the Python script using pyserial and Matplotlib can be tested with real data from the FPGA.

---

# 14. Testing

## 14.1 Technical Testing Plan

| What Needs Testing | How You Will Test It | Success Condition |
|--------------------|----------------------|-------------------|
| Logic gate operations in C code | Change switches and observe output in Python console and plot | Output matches expected truth table for the  |
| UART communication from MicroBlaze | Run Python script and check serial data in console | Clean data is received without corruption |
| Switch input reading | Toggle onboard switches | Correct Input A and Input B values are shown in the plot and console |
| Real-time waveform plotting | Run the full Python script and change switch positions | Waveforms for A, B, and Output update smoothly in Matplotlib |
| Gate selection logic | Use SW2, SW3, SW4 to select different gates | Correct gate name appears in plot title and output matches selected gate |
| Overall system stability | Run the system continuously for 5–10 minutes while changing inputs | No crashes, no corrupted data, and consistent behavior |

## 14.2 Testing and Debugging Log

| Date | Problem Found | Type | What You Tried | Result | Next Action |
|------|---------------|------|----------------|--------|-------------|
| Day 1 | COM port not connecting in Python script | Technical | Changed COM port number and checked Device Manager | COM13 detected but "Access Denied" error occurred | Close all other serial tools before running script |
| Day 1 | No data appearing in Matplotlib plot | Technical | Added debug prints and checked serial baud rate | Data was being sent but animation wasn't updating | Increased animation interval and optimized animate() function |
| Day 2 | Waveform plot lagging / not smooth |  | Reduced MAX_POINTS and increased update interval | Plot became smoother but less responsive | Fine-tune update rate and deque size for better balance |


---


## 14.3 Playtesting Notes

| Tester | What They Did | What Confused Them | What They Enjoyed | What You Will Change |
|--------|---------------|--------------------|-------------------|----------------------|
| Friend/Colleague|Toggled switches to test logic gates and waveforms|Delay in plot update and unclear switch mapping|Real-time waveform visualization|Add switch labels and improve plot speed|
| Self (Developer)| Tested all gate modes for long duration|Occasional Matplotlib freezing|Plot feedback|Live updating of waveform|

---

# 15. Build Documentation

## 15.1 Fabrication Process

No major physical fabrication was required because the project uses a Spartan-7 FPGA development board and a laptop. The physical setup consists of connecting the FPGA board to the laptop through the onboard USB-UART interface. The board switches are used as digital inputs, and the laptop displays the live waveform dashboard.

The main build process involved two parts: FPGA development and software dashboard development. On the FPGA side, Verilog modules were created in Vivado for selecting Boolean operations, generating baud rates, and transmitting UART data. On the software side, a Python script was developed in VS Code using the pyserial and matplotlib libraries. This script reads serial UART data from COM13 and generates a live, animated graphical interface to display the logic waveforms in real-time.

The project serves as a complete and presentation-friendly logic analyzer. By utilizing Matplotlib's animation capabilities, the system is highly interactive and observable, allowing users to view the active logic gate, real-time input states, and the resulting output waveform simultaneously in a single, dark-themed graphical window.

## 16. Build Photos

Schematic:-
<img width="1562" height="729" alt="image" src="https://github.com/user-attachments/assets/689be433-5bbd-4bc5-a676-98fab7607334" />

Matplotlib waveform:-
<img width="1439" height="700" alt="image" src="https://github.com/user-attachments/assets/6ffd74f1-5f1d-4136-8af7-8804905ea1c9" />

Full setup:-
<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/cbbd2e84-67a1-46a1-bbe0-e654acaced32" />



---

# 17. Final Outcome

## 17.1 Final Description

The final project is a real-time, interactive logic analyzer built using a hardware-software co-design approach. A Spartan-7 FPGA development board acts as the hardware processor, reading physical switch inputs to evaluate various digital logic circuits, including basic Boolean gates and a half adder. The FPGA transmits the input states and the computed outputs via a USB-UART interface to a connected laptop. On the software side, a custom Python script utilizes the pyserial and matplotlib libraries to parse the incoming UART data and render a live, scrolling waveform dashboard. This allows users to visually monitor the logic transitions and system states in real-time through an animated graphical interface.

## 17.2 What Works Well

Stable Serial Communication: The UART bridge between the FPGA and the Python backend is reliable, ensuring that switch state changes are transmitted accurately without significant packet loss or latency.

Real-Time Visualization: The Matplotlib animation effectively captures and displays the digital waveforms. The dark-themed interface provides a clean, responsive, and visually distinct representation of the active logic gates and their corresponding input/output signals.

Hardware-Software Integration: The system successfully bridges physical hardware interactions (flipping switches on the Spartan-7 board) with immediate, readable software feedback on the laptop screen.

## 17.3 What Still Needs Improvement

Hardware Component Expansion: The current Verilog implementation is limited to basic gates and a half adder. The system needs to be expanded to include the originally planned complex modules, specifically the full adder and SRAM integration.

## 17.4 What Changed From the Original Plan

Hardware Scope Reduction: The initial plan was highly ambitious, aiming to implement basic logic gates, a half adder, a full adder, and SRAM. Due to time and development constraints, the hardware scope was scaled back. We completed and integrated the basic logic gates and the half adder, but the full adder and SRAM modules were deferred.

Software Interface Pivot: The original concept called for a complete live web dashboard built with HTML, CSS, and JavaScript. During development, this was revised to a Python Matplotlib-based animated graphical interface. This pivot provided a more immediate, reliable, and straightforward method for rendering live serial data plots while still fulfilling the core requirement of real-time waveform visualization.

---

# 18. Reflection

## 18.1 Team Reflection

1. Our team excelled at hardware-software co-design and task delegation. By clearly separating the project into two distinct domains—the Microblaze + SDK code block design development in Vivado and the Python data parsing in VS Code, we were able to work on the hardware logic and software visualization in parallel. We also successfully tackled the core technical challenge of the project: establishing a stable, reliable UART communication bridge between the Spartan-7 board and the laptop (terminal), which allowed the real-time Matplotlib animation to run smoothly without dropping data. We also achieve a live waveform with real-time gate switching properties.
2. The communication error between the board and the laptop's COM port is due to both programs running at once.
3. The responsibilities were divided in such a way that two members were working on the implementation, and the other 2 members were assisting with the debugging and the research part


## 18.2 Technical Reflection

Electronics: Learned to map theoretical digital logic and a half-adder to physical FPGA hardware, and how to configure GPIO pins and UART for hardware-level communication using MicroBlaze and SDK.

Coding: Bridged two programs by writing Verilog in Vivado for parallel hardware logic, and Python in VS Code (using pyserial and matplotlib) for live data visualization.

Integration: Successfully connected an embedded board to a desktop app by designing a reliable serial data protocol, and learned the practical importance of scaling down project scope to ensure a stable final system.

## 18.3 Design Reflection
 
Designing: Learned how to design a complete hardware-software architecture, specifically mapping a reliable data pipeline from physical FPGA switches, through a UART bridge, to a desktop graphical interface.

Clarity: Realized the necessity of clarity in both data and UI—from formatting clean, predictable serial strings (like A, B, Output, Gate).

Physical Interaction: Experienced the value of tactile input; physically interacting with the Spartan-7 board's switches made testing and demonstrating the logic gates much more intuitive than pure software simulation.

Understanding: Bridged the gap between theory and reality, gaining a concrete understanding of how abstract Boolean truth tables translate into physical hardware voltage states and asynchronous data streams.

Iteration: Learned the crucial role of agile iteration, successfully pivoting away from a complex web dashboard to a reliable Matplotlib UI, and scaling down from a full adder to a working half-adder to ensure a functional final prototype.

## 18.4 If You Had One More Hour

We would make the visualization dashboard more interactive and include the digital circuit for a half-adder and SRAM

---

# 19. Final Submission Checklist

Before submission, confirm that:

- [x] Team details are complete
- [x] Project description is complete
- [x] Inspiration sources are included
- [x] Sketches/block diagrams are added
- [x] BOM is complete
- [x] Budget summary is complete
- [x] Vivado schematic (microblaze) screenshot is added
- [x] Code flowchart is added
- [x] Task breakdown is complete
- [x] Update log is filled in
- [x] Risk register is complete
- [x] Testing log is updated
- [x] Build photos are included
- [x] Final reflection is written

---

