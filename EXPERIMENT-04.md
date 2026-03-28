# EXPERIMENT 04

# AIM

Design and analyze a **CMOS Differential Amplifier with Resistive Load** using **TSMC 180 nm CMOS technology** and characterize the circuit performance using:

- DC Operating Point Analysis  
- Transient Analysis  
- AC Small Signal Analysis  
- Input Common Mode Range  
- Output Common Mode Range  
- Linearity Analysis  

Specifications:

| Parameter | Value |
|----------|------|
| VDD | **0.9 V** |
| VSS | **−0.9 V** |
| Tail Current | **1.22 mA** |
| Channel Length | **180 nm** |
| Load Capacitance | **10 pF** |

Simulation Tool: **LTspice**

---

# COMPONENTS REQUIRED

1. NMOS Transistor (TSMC 180nm Model)  
2. Resistors  
3. Current Source  
4. DC Voltage Sources  
5. Signal Source  
6. Capacitors  

---

# THEORY

Differential amplifiers are widely used in analog integrated circuits. These amplifiers amplify the difference between two input signals and reject common-mode noise.

The differential amplifier consists of:

- Two matched NMOS transistors  
- Tail current source  
- Resistive load  

Differential gain:

$$
A_v = g_m R_D
$$

---

# DIFFERENTIAL AMPLIFIER WITH RESISTIVE LOAD

The resistive load differential amplifier provides:

- Moderate gain  
- Good linearity  
- Simple design  

When differential input is applied:

- Current steers between M1 and M2  
- Output voltage changes at drain nodes  

---

# WORKING PRINCIPLE

When:

$$
V_{in1} > V_{in2}
$$

- M1 conducts more  
- M2 conducts less  

When:

$$
V_{in2} > V_{in1}
$$

- M2 conducts more  
- M1 conducts less  

Thus differential amplification occurs.

---

# CIRCUIT DIAGRAM

<p align="center">
<img src="CIRCUIT04.png" width="500">
</p>

<p align="center">
<b>Fig 1: Differential Amplifier Circuit</b>
</p>

---

# DESIGN CALCULATIONS

# GIVEN PARAMETERS

| Parameter | Value |
|-----------|------|
| VDD | 0.9 V |
| VSS | −0.9 V |
| Power | 2.2 mW |
| Tail Current | 1.22 mA |
| Load Capacitance | 10 pF |

---

# POWER CONSTRAINT

$$
P = V \times I
$$

$$
I_{SS} = \frac{P}{VDD - VSS}
$$

$$
I_{SS} = \frac{2.2mW}{1.8}
$$

$$
I_{SS} = 1.22 mA
$$

---

# DRAIN CURRENT CALCULATION

$$
I_D = \frac{I_{SS}}{2}
$$

$$
I_D = 0.61 mA
$$

---

# LOAD RESISTANCE CALCULATION

$$
R_D = \frac{V_{DD}}{I_D}
$$

$$
R_D = \frac{0.9}{0.61m}
$$

$$
R_D = 1.475 k\Omega
$$

---

# WIDTH CALCULATION

Using MOSFET current equation:

$$
I_D = \frac{1}{2}\mu_nC_{ox}\frac{W}{L}V_{OV}^2
$$

Final Width:

$$
W = 73 \mu m
$$

---

# DC OPERATING POINT

<p align="center">
<img src="OP-POINTEXP04.png" width="500">
</p>

<p align="center">
<b>Fig 2: DC Operating Point</b>
</p>

| Parameter | Value |
|-----------|------|
| Id(M1) | 0.61 mA |
| Id(M2) | 0.61 mA |
| Tail Current | 1.22 mA |

---

# INPUT COMMON MODE RANGE (ICMR)

Minimum:

$$
V_{ICM(min)} = V_S + V_T
$$

$$
V_{ICM(min)} = -0.34V
$$

Maximum:

$$
V_{ICM(max)} = V_D + V_T
$$

$$
V_{ICM(max)} = 0.36V
$$

Final Range:

$$
-0.34V \le V_{ICM} \le 0.36V
$$

---

# OUTPUT COMMON MODE RANGE

Minimum:

$$
V_{OCM(min)} = V_S + V_{OV}
$$

$$
V_{OCM(min)} = -0.36V
$$

Maximum:

$$
V_{OCM(max)} = VDD
$$

$$
V_{OCM(max)} = 0.9V
$$

---

# DIFFERENTIAL INPUT VOLTAGE RANGE

$$
V_{id(max)} = \sqrt{2}V_{OV}
$$

$$
V_{id(max)} = 0.48V
$$

---

# TRANSIENT ANALYSIS

<p align="center">
<img src="TA-EXP04.png" width="720">
</p>

<p align="center">
<b>Fig 3: Linear Region</b>
</p>

| Parameter | Value |
|-----------|------|
| Vin | 19.97 mV |
| Vout | 167.61 mV |

---

# NON LINEAR REGION

<p align="center">
<img src="NL-EXP04.png" width="720">
</p>

<p align="center">
<b>Fig 4: Non Linear Region</b>
</p>

Input:

±300 mV

Observation:

- Output clipping  
- Non linear behavior  

---

# THEORETICAL GAIN

$$
A_v = g_mR_D
$$

$$
A_v = 5.38
$$

---

# SIMULATION GAIN

$$
A_v = \frac{V_{out}}{V_{in}}
$$

$$
A_v = 8.39
$$

---

# AC ANALYSIS

<p align="center">
<img src="AC-EXP04.png" width="720">
</p>

<p align="center">
<b>Fig 5: AC Frequency Response</b>
</p>

---

# MIDBAND GAIN

$$
Gain = 12.48 dB
$$

$$
A_v = 4.21
$$

---

# −3 dB CUTOFF FREQUENCY

$$
f_H = 12.11 MHz
$$

---

# BANDWIDTH

$$
BW = 12.11 MHz
$$

---

# UNITY GAIN BANDWIDTH

<p align="center">
<img src="UGB-EXP04.png" width="720">
</p>

<p align="center">
<b>Fig 6: Unity Gain Frequency</b>
</p>

$$
UGB = 47.78 MHz
$$

---

# COMPARISON TABLE

| Parameter | Theoretical | Simulation |
|-----------|-------------|------------|
| Gain | 5.38 | 4.21 |
| Bandwidth | — | 12.11 MHz |
| UGB | — | 47.78 MHz |

---

# REASON FOR DIFFERENCE

Difference occurs due to:

- Channel length modulation  
- Parasitic capacitances  
- Device mismatch  
- Non ideal current source  

---

# RESULT

The CMOS Differential amplifier with resistive load was successfully designed and analyzed using TSMC 180 nm technology.

---

# INFERENCE

The differential amplifier achieved moderate gain and bandwidth. Linear operation was observed for small signals, while large signals resulted in nonlinear behavior. Simulation results closely match theoretical calculations.
# NON-LINEAR ANALYSIS

<p align="center">
<img src="NL-EXPO4-02.png" width="700">
</p>

<p align="center">
<b>Fig 5: Non Linear Operation</b>
</p>

For large differential input:

$$
V_{in} = \pm 300mV
$$

Output waveform becomes distorted indicating nonlinear operation.

Differential input range:

$$
V_{id(max)} = \sqrt{2}V_{OV}
$$

$$
V_{id(max)} = 1.414 \times 0.392
$$

$$
V_{id(max)} = 0.554V
$$

Since applied input:

$$
V_{id} = 600mV
$$

$$
600mV > 554mV
$$

Therefore amplifier enters **non-linear region**.

Observation:

- Output waveform distortion observed  
- One transistor enters triode region  
- Linear amplification no longer maintained  

---

# COMPARISON OF THEORETICAL AND SIMULATED GAIN

| Parameter | Theoretical | Simulation |
|-----------|-------------|------------|
| Gain | 44.7 dB | 5.54 dB |
| Linear Gain | 172 | 1.89 |

---

# REASON FOR DIFFERENCE

The difference between theoretical and simulated gain occurs due to:

- Channel length modulation  
- Parasitic capacitances  
- Finite output resistance  
- Non-ideal current mirror  
- Device mismatch  

---

# INFERENCE

The CMOS differential amplifier with active load was successfully designed and analyzed. The circuit achieved stable DC biasing and proper operation in saturation region. Small signal gain obtained from simulation was lower than theoretical due to parasitic and non-ideal effects. The amplifier demonstrated good bandwidth and high unity gain bandwidth. Linear operation was observed for small signals, while large input signals resulted in nonlinear distortion. Active load differential amplifier provides improved performance compared to resistive load differential amplifier.

---

# RESULT

The CMOS Differential Amplifier with Active Load was successfully designed using TSMC 180 nm technology and analyzed using DC, transient and AC simulations. The amplifier achieved moderate gain and very high bandwidth with proper saturation operation.
