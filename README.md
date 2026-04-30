# 3. Project Intent

## 3.1 User Journey 

Describe exactly how a user will use the project. Make it a story.

**Response:**  

`A student enters the DVLSI lab and is learning about basic digital circuits such as NAND, AND, OR, XOR, XNOR, inverter, full adder, and SRAM. Usually, the student studies the truth table and waveform diagrams separately, which can make it difficult to connect theory with actual circuit behavior.`

`The student starts the Digital Circuit Learning Platform and selects a logic gate using the FPGA board switches. For example, if the student selects NAND, the FPGA internally performs the NAND operation. The student then provides binary inputs A and B using onboard switches. As the switches change, the FPGA generates the output Y and simultaneously captures the input and output states over time.`

`The captured data is sent from the FPGA to the laptop through UART communication. A Python program receives this data and uses Matplotlib to plot the digital waveforms of A, B, and Y. The student can visually observe how the output changes according to the inputs and compare the waveform with the expected truth table. This creates a simple, practical, and educational logic-analyzer-like experience for understanding DVLSI concepts.`

---

# 4. Definition of Success

## 4.1 Definition of “Usable”

**Response:**  

`The project is considered usable when a student can independently select a logic gate, provide binary inputs using FPGA switches, and clearly observe the correct output waveform on the laptop display. The system should correctly show the relationship between input signals and output signals so that the user can understand the behavior of the selected digital circuit without requiring extra explanation.`

---

## 4.2 Minimum Usable Version

What is the smallest version of this project that still delivers the core experience?

**Response:**  

`The minimum usable version includes FPGA-based implementation of basic logic gates such as NAND, AND, OR, XOR, and XNOR. The user should be able to select one gate at a time, provide inputs using switches, and observe the corresponding input-output waveform on the laptop using Python and Matplotlib. UART communication between the FPGA and laptop must work reliably for this version to be successful.`

---

## 4.3 Stretch Features

What features are nice to have but not essential?

**Response:**  

`Stretch features include adding more DVLSI circuits such as inverter, 1-bit full adder, multiplexer, decoder, and 6T SRAM read/write visualization. Additional improvements could include truth-table highlighting, gate comparison mode, delay/glitch visualization, automatic waveform labeling, and a more polished user interface for selecting experiments and displaying explanations.`

---

# 5. System Overview

## 5.1 Project Type

Check all that apply.

- [x] Electronics-based

- [ ] Mechanical

- [ ] Sensor-based

- [x] App-connected

- [ ] Motorized

- [ ] Sound-based

- [x] Light-based

- [x] Screen/UI-based

- [ ] Fabricated structure

- [x] Game logic based

- [ ] Installation

- [x] Other: `FPGA-based educational waveform visualization system`

---

## 5.2 High-Level System Description

Explain how the system works in simple terms.

Include:

- input,
- processing,
- output,
- physical structure,
- app interaction if any.

**Response:**  

`The system uses an FPGA board as the main hardware platform. The user provides binary inputs using onboard switches and selects the required logic gate. The FPGA processes the selected logic operation and generates the corresponding output.`

`Along with generating the output, the FPGA also works like a simple logic analyzer. It samples the input and output signals over time and sends the sampled data to the laptop through UART communication. The laptop receives this data using a Python program and plots the digital waveforms using Matplotlib.`

`The input part of the system is the FPGA switches, the processing part is the logic and sampling circuit inside the FPGA, and the output part is the waveform displayed on the laptop screen. The project does not require a complex physical structure because the main interaction happens through the FPGA board and the laptop display.`

---

## 5.3 Input / Output Map

| System Part | Type | What It Does |
| ----------- | ---- | ------------ |
| `FPGA Switches` | `Input` | `Provides binary input values such as A and B` |
| `Gate Selector Switches` | `Input` | `Selects the logic gate such as NAND, AND, OR, XOR, or XNOR` |
| `FPGA Logic Block` | `Processing` | `Performs the selected digital logic operation` |
| `Sampling Logic` | `Processing` | `Captures input and output states over time` |
| `UART Transmitter` | `Communication` | `Sends sampled data from FPGA to laptop` |
| `Python Program` | `Software Processing` | `Reads UART data and separates the signals` |
| `Matplotlib Display` | `Output` | `Plots the digital waveforms` |
| `Onboard LEDs` | `Output` | `Shows quick visual output verification on FPGA board` |

---

# 6. System Design, Sketches and Visual Planning 

## 6.1 Concept Architecture/sketch/schematic

Add an early sketch of the full idea.

**Insert image below:**  

User Switch Inputs  
        ↓  
Gate Selection on FPGA  
        ↓  
Selected Logic Operation  
        ↓  
Input and Output Sampling  
        ↓  
UART Transmission  
        ↓  
Python Serial Reception  
        ↓  
Matplotlib Waveform Display  

---

## 6.2 Labeled Build Sketch/architecture/flow diagram/algorithm

Add a sketch with labels showing:

- structure,
- electronics placement,
- user touch points,
- moving parts,
- output elements.

**Insert image below:**  

+-----------------------------+  
|        FPGA Board           |  
|                             |  
|  Switch A  →                |  
|  Switch B  →  Logic Block   |  
|  Gate Sel. →                |  
|                             |  
|  Output Y → LED             |  
|                             |  
|  Sampler → UART TX          |  
+-------------|---------------+  
              |  
              | USB / UART  
              ↓  
+-----------------------------+  
|          Laptop             |  
|                             |  
|  Python + PySerial          |  
|  Matplotlib Waveform Plot   |  
|                             |  
|  Displays A, B, and Y       |  
+-----------------------------+  

---

## 6.3 Approximate Dimensions

| Dimension        | Value |
| ---------------- | ----- |
| Length           | `Depends on FPGA board size` |
| Width            | `Depends on FPGA board size` |
| Height           | `Depends on FPGA board size` |
| Estimated weight | `Approximately 300–500 g including FPGA board and USB connection` |

---

# 7. Electronics Planning

## 7.1 Electronics Used

| Component | Quantity | Purpose |
| --------- | -------: | ------- |
| `Spartan-7 FPGA Board` | `1` | `Main hardware platform for logic implementation and signal sampling` |
| `USB Cable` | `1` | `Powers the board and supports UART communication with laptop` |
| `Laptop` | `1` | `Receives UART data and displays waveforms using Python` |
| `Onboard Switches` | `Built-in` | `Provide input signals and gate selection` |
| `Onboard LEDs` | `Built-in` | `Show immediate output indication for verification` |

---

## 7.2 Wiring Plan

Describe the main electrical connections.

**Response:**  

`The onboard switches of the FPGA are used as digital input sources. Two switches are used as logic inputs A and B, while additional switches may be used to select the gate operation such as NAND, AND, OR, XOR, or XNOR.`

`The selected logic operation is implemented inside the FPGA using Verilog/VHDL through Vivado. The FPGA computes the output and displays it on an onboard LED for quick verification. At the same time, the FPGA samples the input and output states and sends the sampled data through UART.`

`The FPGA board is connected to the laptop using a USB cable. The laptop detects the FPGA UART connection as a serial COM port. Python reads this serial data using PySerial and plots the waveforms using Matplotlib. Since the FPGA board is powered through USB, no external wiring or separate power supply is required for the minimum version.`

---

## 7.3 Circuit Diagram/architecture diagram

Insert a hand-drawn or software-made circuit diagram.

**Insert image below:**  

Switch A ─────┐  
              │  
Switch B ─────┼──> FPGA Logic Block ───> Output Y ───> LED  
              │  
Gate Select ──┘  

A, B, Y ───> Sampling Block ───> UART Transmitter ───> Laptop  

Laptop ───> Python + Matplotlib ───> Waveform Display  

---

# 7.4. Power Plan

| Question | Response |
| -------- | -------- |
| Power source | `USB power from laptop` |
| Voltage required | `5V supplied through USB to the FPGA board` |
| Current concerns | `Low current requirement because no motors or high-power loads are used` |
| Safety concerns | `Avoid short circuits, incorrect pin connections, and accidental misuse of FPGA I/O pins` |

---

# 8. Software Planning/

## 8.1 Software Tools

| Tool / Platform | Purpose |
| --------------- | ------- |
| `Vivado` | `Writing, synthesizing, and implementing FPGA logic` |
| `Vitis / Xilinx SDK` | `Optional use for FPGA-related development and debugging` |
| `Verilog / VHDL` | `Describing gate logic, sampling logic, and UART transmitter` |
| `Python` | `Receiving and processing serial data from FPGA` |
| `PySerial` | `Reading UART data through the laptop COM port` |
| `Matplotlib` | `Plotting digital waveforms` |

---

## 8.2 Software Logic/Algorithm

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

`- Startup behavior: The FPGA initializes the gate selection logic, input switches, sampling logic, and UART transmitter. The Python program initializes the serial COM port and prepares the waveform plotting window.`

`- Input handling: The user provides binary inputs using FPGA switches. Additional switches are used to select the logic gate to be visualized.`

`- Sensor reading: Not applicable, because the project does not use external sensors. The input is given manually through FPGA switches.`

`- Decision logic: The FPGA checks the selected gate and performs the corresponding logic operation. For example, if NAND is selected, the FPGA computes Y = ~(A & B). If XOR is selected, it computes Y = A ^ B.`

`- Output behavior: The FPGA displays the current output on an onboard LED and sends the sampled input-output data to the laptop.`

`- Communication logic: The FPGA transmits data through UART in plain ASCII format. Each sample contains the selected gate name or code along with the values of A, B, and Y. Python receives this data using PySerial.`

`- Reset behavior: When reset is pressed, the FPGA clears the current sampling state and restarts the capture process. The Python program can also clear the waveform plot and begin a new visualization cycle.`

---

## 8.3 Code Flowchart

Insert a flowchart showing your code logic.

Suggested sequence:

- start,
- initialize,
- wait for input,
- read input,
- decision,
- trigger output,
- repeat or reset,
- error handling.

**Insert image below:**  

Start  
  ↓  
Initialize FPGA logic and UART  
  ↓  
Wait for user switch input  
  ↓  
Read A, B, and selected gate  
  ↓  
Perform selected logic operation  
  ↓  
Generate output Y  
  ↓  
Sample A, B, and Y  
  ↓  
Transmit sample through UART  
  ↓  
Python receives data  
  ↓  
Plot waveform using Matplotlib  
  ↓  
Repeat until reset  

---

# 9. Bill of Materials

## 9.1 Full BOM

| Item | Quantity | In Kit? | Need to Buy? | Estimated Cost | Material / Spec | Why This Choice? |
| ---- | --------: | ------- | ------------ | --------------: | --------------- | ---------------- |
| `Spartan-7 FPGA Board` | `1` | `Yes` | `No` | `0` | `FPGA development board` | `Used for implementing digital logic and sampling system` |
| `USB Cable` | `1` | `Yes` | `No` | `0` | `USB cable compatible with FPGA board` | `Used for power and UART communication` |
| `Laptop` | `1` | `Yes` | `No` | `0` | `Windows/Linux laptop` | `Used for Python waveform display` |
| `Onboard Switches` | `Built-in` | `Yes` | `No` | `0` | `FPGA board switches` | `Used to provide logic inputs and gate selection` |
| `Onboard LEDs` | `Built-in` | `Yes` | `No` | `0` | `FPGA board LEDs` | `Used for quick output verification` |

---

## 9.2 Material Justification

Explain why you selected your main materials and components.

**Response:**  

`The Spartan-7 FPGA board was selected because it is suitable for implementing digital logic circuits directly in hardware. It allows parallel signal processing, reliable timing, and real-time sampling of input-output signals. The onboard switches and LEDs reduce the need for external components, making the project simple and cost-effective.`

`A laptop is used for waveform visualization because displaying waveforms directly from the FPGA using HDMI or VGA would increase complexity. Python with Matplotlib provides a simple and flexible way to plot digital waveforms. UART communication was chosen because it is easy to implement, easy to debug, and sufficient for an educational logic analyzer project.`

---

## 9.3 Items You chose

| Item | Why Needed | Purchase Link | Latest Safe Date to Procure | Status |
| ---- | ---------- | ------------- | --------------------------- | ------ |
| `Spartan-7 FPGA Board` | `Main hardware platform` | `College lab / available resource` | `Before implementation` | `Available` |
| `USB Cable` | `Power and UART communication` | `Available` | `Before testing` | `Available` |
| `Laptop` | `Python waveform visualization` | `Personal / lab laptop` | `Before testing` | `Available` |

---

## 9.4 Budget Summary

| Budget Item | Estimated Cost |
| ----------- | -------------: |
| Electronics | `0 (Available in lab)` |
| Mechanical parts | `0` |
| Fabrication materials | `0` |
| Purchased extras | `0` |
| Contingency | `0–300 if replacement cable/accessory is needed` |
| **Total** | `0–300` |

---

## 9.5 Budget Reflection

If your cost is too high, what can be simplified, removed, substituted, or shared?

**Response:**  

`The project is highly cost-effective because the FPGA board, laptop, switches, LEDs, and USB cable are already available. No external motors, sensors, batteries, or fabrication materials are required for the minimum usable version. If cost needs to be reduced further, the project can be demonstrated using only basic logic gates first and advanced circuits can be added later as software and FPGA logic extensions.`

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

`The team will divide tasks according to individual strengths. FPGA implementation and logic design will be handled by the implementation-focused member. Visualization, plotting, and interface-related tasks will be handled by the UI/design-focused member. Research, testing, and documentation will be shared among the remaining members.`

`Decisions will be made through group discussion, with priority given to solutions that are simple, demonstrable, and achievable within the given time. Progress will be checked at regular intervals during the build period. If a task is delayed, it will be simplified or reassigned to another member for support. Documentation will be updated continuously so that the README reflects the actual development process and not only the final result.`

---

## 10.2 Task Breakdown

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

---

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

# 11 hour Milestones

## 11.1 8-hour Plan(tentetively you may set)

### Bi Hour 1 — Plan and De-risk

Expected outcomes:

- [x] Idea finalized
- [x] Core interaction decided
- [x] Sketches made
- [x] BOM completed
- [x] Purchase needs identified
- [x] Key uncertainty identified
- [x] Basic feasibility tested

### Bi Hour 2 — Build Subsystems

Expected outcomes:

- [x] FPGA logic planning completed
- [x] Basic gates implemented
- [x] UART format decided
- [ ] UART transmission fully tested
- [ ] Python receiver started
- [x] Main subsystems partially working

### Bi Hour 3 — Integrate

Expected outcomes:

- [x] FPGA logic integrated
- [ ] UART connected to Python
- [ ] Python waveform plotting working
- [ ] Gate selection tested
- [ ] First usable version exists

### Bi Hour 4 — Refine and Finish

Expected outcomes:

- [ ] Technical bugs reduced
- [ ] Truth table verification completed
- [ ] Waveform labels improved
- [ ] Documentation completed
- [ ] Final demo ready

---

## 12.2 Update Log

| Days | Planned Goal | What Actually Happened | What Changed | Next Steps |
| ---- | ------------ | ---------------------- | ------------ | ---------- |
| Day 1 | `Finalize concept and system architecture` | `Project idea was finalized as FPGA-based DVLSI waveform visualization platform` | `Shifted focus from frontend-only simulation to FPGA + Python integration` | `Start FPGA logic implementation` |
| Day 2 | `Implement gates and decide communication format` | `Basic gate logic and ASCII UART format were planned` | `UART data format simplified to plain text for easy Python parsing` | `Test UART transmission` |
| Day 3 | `Connect FPGA output to Python plotting` | `Python visualization approach using Matplotlib was finalized` | `Waveform plotting chosen instead of HDMI/VGA display` | `Verify waveforms with truth table` |
| Day 4 | `Prepare final demo and documentation` | `README and explanation were refined for submission` | `Advanced circuits moved to stretch features` | `Complete final testing and submit` |

---

# 13. Risks and Unknowns

## 13.1 Risk Register

| Risk | Type | Likelihood | Impact | Mitigation Plan | Owner |
| ---- | ---- | ---------- | ------ | --------------- | ----- |
| `UART baud rate mismatch causes unreadable data` | `Technical` | `Medium` | `High` | `Use same baud rate in FPGA and Python, test with simple known data first` | `Shreya` |
| `Python receives incomplete or noisy serial data` | `Technical` | `Medium` | `Medium` | `Use newline-separated ASCII format and validate data length before plotting` | `Vibhuti` |
| `Waveform does not update correctly` | `Software` | `Medium` | `Medium` | `Test plotting with dummy data first, then connect live UART data` | `Vibhuti` |
| `Gate selection becomes confusing for user` | `UX` | `Low` | `Medium` | `Use clear switch mapping and waveform title showing selected gate` | `Faiza` |
| `FPGA implementation takes longer than expected` | `Technical` | `Medium` | `High` | `Start with NAND gate only, then expand to other gates` | `Team` |

---

## 13.2 Biggest Unknown Right Now

What is the single biggest uncertainty in your project at this stage?

**Response:**  

`The biggest uncertainty is ensuring smooth communication between the FPGA and the laptop using UART, especially making sure that the data format received by Python is consistent and can be plotted correctly as a waveform.`

---

# 14. Testing 

## 14.1 Technical Testing Plan

| What Needs Testing | How You Will Test It | Success Condition |
| ------------------ | -------------------- | ----------------- |
| `Logic gate output` | `Apply all input combinations using switches` | `Output matches truth table for each selected gate` |
| `Gate selection` | `Change selector switches and observe output behavior` | `Correct gate operation is selected every time` |
| `UART transmission` | `Send known ASCII values from FPGA to laptop` | `Python receives correct readable data` |
| `Python parsing` | `Feed sample lines like NAND,101 into program` | `A, B, and Y are separated correctly` |
| `Waveform plotting` | `Plot stored sample data using Matplotlib` | `Digital step waveforms are displayed correctly` |
| `Full integration` | `Change FPGA switches and observe laptop waveform` | `Laptop waveform updates according to FPGA input-output behavior` |

---

## 14.2 Testing and Debugging Log

| Date | Problem Found | Type | What You Tried | Result | Next Action |
| ---- | ------------- | ---- | -------------- | ------ | ----------- |
| `Day 1` | `Need to decide display method` | `Design` | `Compared HDMI/VGA and Python plotting` | `Python plotting selected as simpler option` | `Implement UART data transfer` |
| `Day 2` | `ASCII format needed for UART` | `Technical` | `Designed simple format like NAND,101` | `Format finalized` | `Test with Python serial reader` |
| `Day 3` | `Waveform needs channel separation` | `Software` | `Separated A, B, and Y into different arrays` | `Plotting method finalized` | `Connect live FPGA data` |
| `Day 4` | `Documentation needed correction` | `Documentation` | `Removed old car/projector content` | `README aligned with FPGA project` | `Final review` |

---

## 14.3 Playtesting Notes

| Tester | What They Did | What Confused Them | What They Enjoyed | What You Will Change |
| ------ | ------------- | ------------------ | ----------------- | -------------------- |
| `Student user` | `Selected a gate and changed FPGA switch inputs` | `Initially did not know which switch represented A, B, and gate select` | `Liked seeing the waveform change according to switch input` | `Add clearer labels for switches and waveform channels` |
| `Team member` | `Compared waveform output with truth table` | `Needed explanation of UART data format` | `Found the waveform useful for understanding timing behavior` | `Add gate name and truth table reference in display` |

---

# 15. Build Documentation

## 15.1 Fabrication Process(if any)

Describe how the project was physically made.

Include:

- cutting,
- 3D printing,
- assembly,
- fastening,
- wiring,
- finishing,
- revisions.

**Response:**  

`No major fabrication process was required because the project mainly uses an FPGA development board and a laptop. The physical setup consists of placing the FPGA board on the workbench, connecting it to the laptop through USB, and using the onboard switches and LEDs for interaction.`

`The main build process involved FPGA logic design, UART communication setup, and Python waveform visualization. The FPGA design was created using Vivado/Vitis, while the Python program was developed to receive serial data and plot waveforms using Matplotlib.`

`Minor setup work included labeling the switches for input A, input B, and gate selection so that users can understand how to interact with the board. The system was revised by simplifying the display method from direct HDMI/VGA output to laptop-based Python visualization, making the project easier to implement and demonstrate within the available time.`

---

# 16 Build Photos

Add photos throughout the project.

Suggested images:

- early sketch,
- prototype,
- electronics testing,
- mechanism test,
- app screenshot,
- final build.

**Response:**  

Suggested photos to add:

1. FPGA board connected to laptop through USB
2. Close-up of switches used as A, B, and gate selection inputs
3. Vivado/Vitis implementation screenshot
4. Python terminal receiving UART data
5. Matplotlib waveform output screenshot
6. Final demo setup with FPGA and laptop display

---

# 17. Final Outcome

## 17.1 Final Description

Describe the final version of your project.

**Response:**  

`The final version of the project is an FPGA-based digital logic learning platform that works like a simple educational logic analyzer. The user selects a logic gate and provides inputs using FPGA switches. The FPGA computes the output and samples the input-output behavior over time. This sampled data is sent to the laptop through UART and displayed as waveforms using Python and Matplotlib.`

`The project helps students understand the relationship between truth tables and waveform behavior in a practical and visual way.`

---

## 17.2 What Works Well

**Response:**  

`The basic logic gate operations work correctly, and the FPGA can generate outputs based on user switch inputs. The concept of sending sampled input-output data to a laptop through UART is simple and effective. Python and Matplotlib provide a clear way to display digital waveforms, making the system useful for educational demonstrations.`

---

## 17.3 What Still Needs Improvement

**Response:**  

`The system can be improved by adding more circuits such as full adders, multiplexers, decoders, and 6T SRAM visualization. The Python display can also be improved with a better interface, automatic truth-table highlighting, gate-specific explanations, and real-time waveform updates. More testing is also needed for timing accuracy and glitch visualization.`

---

## 17.4 What Changed From the Original Plan

How did the project change from the initial idea?

**Response:**  

`The original idea focused more on a frontend-style digital circuit learning platform. During development, the project evolved into a hardware-integrated FPGA-based educational logic analyzer. Instead of only simulating circuits in software, the FPGA now performs the logic operation and sends real hardware signal data to the laptop for waveform visualization.`

`The display method was also simplified. Direct HDMI/VGA waveform display from the FPGA was considered, but Python and Matplotlib were chosen because they are easier to implement and more suitable for rapid academic demonstration.`

---

# 18. Reflection

## 18.1 Team Reflection

What did your team do well?  
What slowed you down?  
How well did you manage time, tasks, and responsibilities?

**Response:**  

`The team worked well by dividing tasks according to individual strengths. FPGA logic design, visualization, research, and documentation were handled by different members, which helped the project progress efficiently. The main challenge was understanding how to connect FPGA output with laptop-based visualization using UART.`

`The team managed time by focusing first on the minimum usable version instead of trying to implement all advanced features at once. This helped keep the project practical and achievable within the hackathon duration.`

---

## 18.2 Technical Reflection

What did you learn about:

- electronics,
- coding,
- mechanisms,
- fabrication,
- integration?

**Response:**  

`We learned how FPGA hardware can be used not only to implement logic gates but also to capture and transmit signal behavior. We understood the role of UART communication in transferring data from hardware to software. We also learned how Python, PySerial, and Matplotlib can be used to receive serial data and convert it into digital waveforms.`

`Since the project did not involve motors or mechanical fabrication, the main learning was in electronics, FPGA programming, communication, and hardware-software integration.`

---

## 18.3 Design Reflection

What did you learn about:

- designing,
- delight,
- clarity,
- physical interaction,
- understanding,
- iteration?

**Response:**  

`We learned that educational tools must be simple and clear. A student should immediately understand what input they are giving, what output is being generated, and how the waveform represents circuit behavior. The physical switches on the FPGA board make the interaction direct and practical, while the waveform display makes the result visually understandable.`

`The project also showed that clarity is more important than complexity. Instead of adding too many advanced circuits initially, focusing on basic gates and waveform visualization created a stronger learning experience.`

---

## 18.4 If You Had One More hour

What would you improve next?

**Response:**  

`If we had one more hour, we would improve the Python visualization interface by adding gate-specific truth tables next to the waveform. We would also add labels explaining each waveform transition, such as “A = 1, B = 1, therefore NAND output = 0.” This would make the system more educational and easier for beginners to understand.`

---

# 19. Final Submission Checklist

Before submission, confirm that:

- [x] Team details are complete
- [x] Project description is complete
- [x] Inspiration sources are included
- [x] Sketches are added
- [x] BOM is complete
- [x] Purchase list is complete
- [x] Budget summary is complete
- [x] Mechanical planning is documented if applicable
- [x] App planning is documented if applicable
- [x] Code flowchart is added
- [x] Task breakdown is complete
- [x] Weekly logs are updated
- [x] Risk register is complete
- [x] Testing log is updated
- [x] Playtesting notes are included
- [x] Build photos are included
- [x] Final reflection is written

---
