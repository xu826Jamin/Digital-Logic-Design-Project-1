# Digital-Logic-Design-Project-1
## Part 1: Digital Logic Gates & CMOS Analysis
[cite_start]**Course:** CompEng 2DI4 - Laboratory 1 [cite: 1]
[cite_start]**Objective:** Establish proficiency with High-Speed CMOS (HC) integrated circuits and verify fundamental logic gate theorems. [cite: 34, 79]

### 1. CMOS Logic Level Characterization
- **Assumptions**: All logic levels are defined by the High-Speed CMOS (HC) family; [cite_start]TTL/LS standards are considered incompatible for these experiments. [cite: 95, 96]
- [cite_start]**Conditions**: VCC is maintained at 5.0V; voltages between 0.98V and 3.15V are indeterminate and strictly avoided to prevent circuit instability. [cite: 88, 93, 94]
- [cite_start]**Voltage Threshold Analysis**: Determined the experimental switching threshold of a NAND gate using a 100kHz triangular wave input (3.3V pk-pk, 1.65V DC offset). [cite: 98, 102]

- [cite_start]**Switching Point**: Observed the output transition at an input voltage of **1.80V** using digital oscilloscope cursor measurements. [cite: 287, 288]
- [cite_start]**Performance Evaluation**: Confirmed that the automatic measuring function does not perfectly match theoretical HIGH-SPEED CMOS levels due to transition delays. [cite: 286, 289]

### 2. Universal Gate Implementation
- [cite_start]**NAND Logic Versatility**: Built and verified five distinct circuits using the **sn74HC00** to demonstrate NAND gates as universal building blocks. [cite: 78, 112]
- [cite_start]**Logic Functions**: Experimentally confirmed implementation of **NOT** ($F_1 = x'$), **AND** ($F_2 = xy$), **OR** ($F_3 = x+y$), and **XOR** ($F_5 = x \oplus y$). [cite: 291, 292, 293, 295]
- [cite_start]**Truth Table Verification**: Validated all logical operations through physical switch inputs and LED monitoring; successfully verified Milestone 2 with Figure 5 (OR of 3 ANDs). [cite: 112, 113, 294, 296]

### 3. Advanced Logical Operations
- [cite_start]**Parity Generation**: Constructed a parity detector using XOR gates to identify odd bit sequences ($F_{Parity}$ is HI when the count of 1s in input $wxyz$ is odd). [cite: 184, 185, 188, 302]
- [cite_start]**Equality Detection**: Engineered a coincidence circuit using XNOR and NAND logic; verified that $F_{equality}$ is HI only when 3-bit numbers $abc$ and $xyz$ are identical. [cite: 199, 201, 202, 303]
- [cite_start]**Controllable Inversion**: Verified the **sn74HC86** XOR gate as a "controllable inverter"—when control input $y=0$, input $x$ passes unchanged; when $y=1$, input $x$ is complemented. [cite: 175, 176, 300, 301]

### 4. Propagation Delay & Oscillators
- [cite_start]**Ring Oscillator Construction**: Connected an odd number of inversions (4 NOT gates + 1 NAND) in a feedback loop to generate a self-sustaining periodic signal. [cite: 225, 226, 235]

- [cite_start]**Timing Analysis**: Measured an average delay per inverter of **7.6125ns** based on the recorded frequency of 16.4MHz. [cite: 306, 309]
- [cite_start]**Datasheet Comparison**: The measured delay correlates closely with the typical value of **9ns** specified in the sn74HC00 datasheet. [cite: 307, 309]
- [cite_start]**Logic Substitution Analysis**: If the NAND was replaced with a NOR (with enable HI), the output would remain constant at **LO (0)** because a NOR gate with any input HI always outputs LO. [cite: 241, 314]

### Mathematical Foundations (LaTeX)
#### Average Gate Propagation Delay
[cite_start]$$t_{avg\_delay} = \frac{\text{Period}}{2 \cdot N_{\text{inverters}}}$$ [cite: 226, 306]

#### Universal NAND Transformation (XOR)
[cite_start]The XOR function $F_5 = x \oplus y$ is logically necessary to match Figure 6, derived via NAND-only implementation: [cite: 156, 295]
$$F_5 = \text{NAND}(\text{NAND}(x, \text{NAND}(x, y)), \text{NAND}(y, \text{NAND}(x, y)))$$
[cite_start]$$F_5 = (x \cdot (x \cdot y)')' \cdot (y \cdot (x \cdot y)')' = xy' + x'y$$ [cite: 295, 299]

#### Parity Calculation
[cite_start]For a 4-bit word $wxyz$: [cite: 188]
[cite_start]$$F_{Parity} = (w \oplus x) \oplus (y \oplus z)$$ [cite: 198]
