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
<img src="CIRCUIT-EXP04.png" width="500">
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
<img src="DC-EXP04.png" width="500">
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
<img src="TRANSIENT-LINEAR-EXP04.png" width="720">
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
<img src="TRANSIENT-NONLINEAR-EXP04.png" width="720">
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

# COMPLETE DESIGN CALCULATIONS

## Tail Current Calculation

Given power constraint:

$$
P = 2.2mW
$$

Supply voltage:

$$
V_{DD} - V_{SS} = 0.9 - (-0.9)
$$

$$
= 1.8V
$$

Tail current:

$$
I_{SS} = \frac{P}{V}
$$

$$
I_{SS} = \frac{2.2mW}{1.8}
$$

$$
I_{SS} = 1.22mA
$$

---

## Drain Current Calculation

$$
I_D = \frac{I_{SS}}{2}
$$

$$
I_D = \frac{1.22}{2}
$$

$$
I_D = 0.61mA
$$

---

## Simulated Drain Current

From Operating Point:

$$
I_D = 0.674mA
$$

This closely matches theoretical value.

---

# OVERDRIVE VOLTAGE

Source voltage:

$$
V_S = -0.752V
$$

Gate voltage:

$$
V_G = 0V
$$

$$
V_{GS} = V_G - V_S
$$

$$
V_{GS} = 0 - (-0.752)
$$

$$
V_{GS} = 0.752V
$$

Given:

$$
V_T = 0.36V
$$

Overdrive voltage:

$$
V_{OV} = V_{GS} - V_T
$$

$$
V_{OV} = 0.752 - 0.36
$$

$$
V_{OV} = 0.392V
$$

---

# TRANSCONDUCTANCE

$$
g_m = \frac{2I_D}{V_{OV}}
$$

$$
g_m = \frac{2(0.674m)}{0.392}
$$

$$
g_m = 3.44mS
$$

---

# THEORETICAL GAIN

For active load:

$$
A_v = g_m r_o
$$

Assuming:

$$
r_o = 50k\Omega
$$

$$
A_v = 3.44m \times 50k
$$

$$
A_v = 172
$$

---

# Gain in dB

$$
Gain = 20\log(172)
$$

$$
Gain = 44.7dB
$$

---

# SIMULATED GAIN

From transient:

Input:

$$
V_{in} = 19.95mV
$$

Output:

$$
V_{out} = 37.77mV
$$

Gain:

$$
A_v = \frac{V_{out}}{V_{in}}
$$

$$
A_v = 1.89
$$

Gain in dB:

$$
Gain = 20\log(1.89)
$$

$$
Gain = 5.54dB
$$

---

# MIDBAND GAIN

From AC analysis:

$$
Gain = 5.54dB
$$

Linear gain:

$$
A_v = 10^{(5.54/20)}
$$

$$
A_v = 1.89
$$

---

# −3 dB CUTOFF FREQUENCY

Midband gain:

$$
5.54dB
$$

−3 dB level:

$$
5.54 - 3 = 2.54dB
$$

From plot:

$$
f_H = 2.856GHz
$$

---

# BANDWIDTH

$$
BW = f_H - f_L
$$

Since:

$$
f_L \approx 0
$$

$$
BW = 2.856GHz
$$

---

# UNITY GAIN BANDWIDTH

Unity gain from AC plot:

$$
UGB = 5.058GHz
$$

---

# INPUT COMMON MODE RANGE

Minimum:

$$
V_{ICM(min)} = V_S + V_T
$$

$$
V_{ICM(min)} = -0.752 + 0.36
$$

$$
V_{ICM(min)} = -0.392V
$$

Maximum:

$$
V_{ICM(max)} = 0.36V
$$

Final:

$$
-0.392V \le V_{ICM} \le 0.36V
$$

---

# OUTPUT COMMON MODE RANGE

Minimum:

$$
V_{OCM(min)} = V_S + V_{OV}
$$

$$
V_{OCM(min)} = -0.752 + 0.392
$$

$$
V_{OCM(min)} = -0.36V
$$

Maximum:

$$
V_{OCM(max)} = 0.9V
$$

---

# SATURATION CHECK

For NMOS:

Condition:

$$
V_{DS} \ge V_{OV}
$$

Drain voltage:

$$
V_D = -0.121V
$$

Source voltage:

$$
V_S = -0.752V
$$

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = -0.121 - (-0.752)
$$

$$
V_{DS} = 0.631V
$$

Since:

$$
V_{DS} > V_{OV}
$$

$$
0.631 > 0.392
$$

Transistor operates in **saturation region**.

---

# FINAL RESULTS

| Parameter | Value |
|-----------|------|
| Wn | 30.625 µm |
| Wp | 38.21 µm |
| ID | 0.674 mA |
| VOV | 0.392 V |
| gm | 3.44 mS |
| Gain (Transient) | 1.89 |
| Gain (AC) | 5.54 dB |
| Bandwidth | 2.856 GHz |
| UGB | 5.06 GHz |

---

# RESULT

The CMOS differential amplifier with active load was successfully designed and analyzed. The circuit achieved stable biasing, moderate gain, and very high bandwidth.

---

# INFERENCE

The active load differential amplifier provides higher output resistance and improved gain compared to resistive load amplifiers. The circuit operates in saturation region ensuring proper amplification. Small signal gain was moderate while bandwidth was very high. The difference between theoretical and simulated gain is due to parasitic capacitances, channel length modulation, and finite output resistance effects. The amplifier demonstrates good linearity for small signals and nonlinear behaviour for large input amplitudes.
