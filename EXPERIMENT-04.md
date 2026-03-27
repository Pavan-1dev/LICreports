# Experiment 04  
# CMOS Differential Amplifier with Resistive Load

---

# AIM

To design and analyze a CMOS differential amplifier with resistive load using TSMC 180nm technology and characterize the performance in terms of:

- Gain  
- Bandwidth  
- Unity Gain Bandwidth  
- Input Common Mode Range  
- Output Common Mode Range  
- Linearity  

---

# INTRODUCTION

Differential amplifiers are one of the most fundamental building blocks in analog integrated circuits. These amplifiers amplify the difference between two input signals while rejecting common-mode signals. Due to this property, differential amplifiers are widely used in operational amplifiers, comparators, and analog signal processing circuits.

The CMOS differential amplifier with resistive load provides moderate gain and good linearity. It is commonly used in low-power analog circuits.

---

# THEORY — DIFFERENTIAL AMPLIFIER WITH RESISTIVE LOAD

A differential amplifier consists of:

- Two matched NMOS transistors  
- Tail current source  
- Resistive load  

The differential input voltage is applied to the gates of both transistors. The current steers between the two transistors depending on the input voltage.

Differential gain is given by:

\[
A_v = g_m R_D
\]

Where:

- \( g_m \) = transconductance  
- \( R_D \) = load resistance  

---

# WORKING PRINCIPLE

When differential input is applied:

- If \( V_{in1} > V_{in2} \) → M1 conducts more
- If \( V_{in2} > V_{in1} \) → M2 conducts more

This causes:

- Output1 decreases
- Output2 increases

Thus differential amplification occurs.

---

# CIRCUIT DIAGRAM

![Figure 1: Differential Amplifier Circuit](circuit-diagram.png)

---

# DESIGN CALCULATIONS

# GIVEN PARAMETERS

| Parameter | Value |
|-----------|------|
| VDD | 0.9 V |
| VSS | -0.9 V |
| Power Constraint | 2.2 mW |
| Tail Current | 1.22 mA |
| Channel Length | 180 nm |
| Load Capacitance | 10 pF |

---

# POWER CONSTRAINT

\[
P = V \times I
\]

\[
I_{SS} = \frac{P}{VDD - VSS}
\]

\[
I_{SS} = \frac{2.2mW}{1.8}
\]

\[
I_{SS} = 1.22 mA
\]

---

# DRAIN CURRENT CALCULATION

\[
I_D = \frac{I_{SS}}{2}
\]

\[
I_D = 0.61 mA
\]

---

# LOAD RESISTANCE CALCULATION

\[
R_D = \frac{V_{DD}}{I_D}
\]

\[
R_D = \frac{0.9}{0.61m}
\]

\[
R_D = 1.475 k\Omega
\]

---

# WIDTH CALCULATION

Using MOSFET current equation:

\[
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} V_{OV}^2
\]

Final Width:

\[
W = 73 \mu m
\]

---

# DC OPERATING POINT

![Figure 2: DC Operating Point](dc-operating-point.png)

| Parameter | Value |
|-----------|------|
| Id(M1) | 0.61 mA |
| Id(M2) | 0.61 mA |
| Vout1 | 0.00025 V |
| Vout2 | 0.00025 V |
| Tail Current | 1.22 mA |

---

# INPUT COMMON MODE RANGE

Minimum:

\[
V_{ICM(min)} = V_S + V_T
\]

\[
V_{ICM(min)} = -0.34V
\]

Maximum:

\[
V_{ICM(max)} = V_D + V_T
\]

\[
V_{ICM(max)} = 0.36V
\]

Final Range:

\[
-0.34V \le V_{ICM} \le 0.36V
\]

---

# OUTPUT COMMON MODE RANGE

Minimum:

\[
V_{OCM(min)} = V_S + V_{OV}
\]

\[
V_{OCM(min)} = -0.36V
\]

Maximum:

\[
V_{OCM(max)} = VDD
\]

\[
V_{OCM(max)} = 0.9V
\]

---

# DIFFERENTIAL INPUT VOLTAGE RANGE

\[
V_{id(max)} = \sqrt{2}V_{OV}
\]

\[
V_{id(max)} = 0.48V
\]

---

# TRANSIENT ANALYSIS

## Linear Region

![Figure 3: Linear Region Waveform](linear-waveform.png)

| Parameter | Value |
|-----------|------|
| Vin | 19.97 mV |
| Vout | 167.61 mV |
| Gain | 8.39 |

---

## Non Linear Region

![Figure 4: Non Linear Waveform](nonlinear-waveform.png)

Input:

±300 mV

Observation:

- Output clipping  
- Nonlinear behavior  

---

# THEORETICAL GAIN

\[
A_v = g_m R_D
\]

Theoretical Gain:

\[
A_v = 5.38
\]

---

# TRANSIENT GAIN

\[
A_v = 8.39
\]

---

# AC ANALYSIS

![Figure 5: AC Gain Plot](ac-plot.png)

---

# MIDBAND GAIN

\[
Gain = 12.48 dB
\]

\[
A_v = 4.21
\]

---

# CUTOFF FREQUENCY

Upper cutoff:

\[
f_H = 12.11 MHz
\]

---

# BANDWIDTH

\[
BW = 12.11 MHz
\]

---

# UNITY GAIN BANDWIDTH

![Figure 6: Unity Gain Frequency](ugb.png)

\[
UGB = 47.78 MHz
\]

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
- Non-ideal current source  

---

# INFERENCE

The CMOS differential amplifier with resistive load was successfully designed and analyzed. The amplifier achieved moderate gain and bandwidth. Simulation results closely matched theoretical calculations. The circuit demonstrated good linearity for small signals and nonlinear behavior for large signals.

---
