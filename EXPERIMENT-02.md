# EXPERIMENT 02

# AIM

Design and analyze a **CMOS amplifier configuration using NMOS transistor with PMOS active load** using **TSMC 180 nm CMOS technology** and characterize the performance of the designed circuit under the following specifications:

VDD = 1.2 V  
ID = 250 µA  
CL = 0.5 pF  
L = 360 nm  

The circuit performance is verified using:

1. DC Operating Point Analysis  
2. Transient Analysis  
3. AC Small Signal Analysis  

using **LTspice**.

---

# COMPONENTS REQUIRED

1. PMOS transistor (TSMC 180nm model)  
2. NMOS transistor (TSMC 180nm model)  
3. Source resistor RS  
4. DC voltage sources  
5. Signal voltage source  
6. Capacitor CL  

---

# THEORY

MOSFETs are the fundamental building blocks of modern integrated circuits. CMOS technology combines both **NMOS and PMOS transistors**, enabling high performance with low power consumption.

In this experiment, a **CMOS amplifier configuration** is designed where:

- **NMOS transistor acts as the amplifying device**
- **PMOS transistor acts as an active load**
- **Source degeneration resistor (RS)** helps stabilize the bias point

Advantages of this configuration include:

1. High voltage gain  
2. Improved bias stability  
3. Reduced distortion due to source degeneration  
4. High input impedance  

For proper amplifier operation, MOSFETs must operate in the **saturation region**, where they behave as voltage-controlled current sources and provide linear amplification.

---

# SATURATION CONDITIONS

## NMOS Saturation Condition

VGS > VT  

VDS ≥ VOV  

Where

VOV = VGS − VT

---

## PMOS Saturation Condition

VSG > |VT|  

VSD ≥ VOV  

Where

VOV = VSG − |VT|

---

# PROCEDURE

### 1. Include Technology Model

The TSMC 180 nm model library was included in LTspice using:

```
.lib tsmc018.lib
```

---

### 2. Build the CMOS Amplifier Circuit

The circuit consists of:

- PMOS transistor connected to **VDD**
- NMOS transistor connected to **source resistor**
- Output taken at the **drain node**
- Bias voltages applied to transistor gates
- Load capacitor connected at output

---

### 3. Initial Device Parameters

The channel length was fixed as:

L = 360 nm

Initial width values were calculated theoretically.

---

### 4. DC Operating Point Analysis

The **.op command** was executed in LTspice to determine:

- Drain current  
- Output voltage  
- Node voltages  

---

### 5. Bias Adjustment

Transistor widths were adjusted until the required operating point was obtained:

ID ≈ 250 µA  
Vout ≈ 0.8 V  

---

### 6. Transient Analysis

A small sinusoidal signal was applied to the input and **.tran analysis** was performed to observe time-domain amplification.

---

### 7. AC Small Signal Analysis

AC magnitude was set to **1 V**, and **.ac analysis** was performed to determine:

- Midband gain  
- Frequency response  
- Bandwidth  

---

# DESIGN CALCULATIONS

## 1. Drain Current Selection

The design drain current was selected as:

ID = 250 µA

---

## 2. Source Resistor Calculation

Voltage across the source resistor:

VRS = 0.2 V

Using Ohm’s law:

RS = VRS / ID

RS = 0.2 / (250 × 10⁻⁶)

RS = 800 Ω

---

## 3. Output Voltage Selection

The output voltage is selected as:

Vout = VDD/2 + IDRS

Vout = 0.6 + 0.2

Vout = 0.8 V

---

## 4. Gate Bias Voltage

For NMOS:

VGS ≈ 0.61 V

Source voltage:

VS = IDRS

VS = 0.2 V

Therefore

VB1 = VGS + VS

VB1 = 0.61 + 0.2

VB1 = 0.81 V

---

## 5. Device Dimensions

After theoretical calculations and iterative simulation adjustments:

Wn = 30 µm  
Wp = 128.5 µm  
L = 360 nm

---

# CIRCUIT

![Image description](CIRCUIT01-EXP02.png)

---

# DC ANALYSIS

DC analysis determines the **operating point (Q-point)** of the MOSFET amplifier and verifies that the transistors operate in the **saturation region**.

This ensures proper amplification and stable circuit operation.

---

# Q-POINT VERIFICATION USING DC OPERATING POINT ANALYSIS

Using the **.op command** in LTspice, the following values were obtained:

Drain current

ID = 0.000250418 A ≈ 250 µA

Output voltage

Vout = 0.798442 V

Theoretical output voltage

Vout = 0.8 V

The simulated value closely matches the theoretical design target, confirming correct biasing.


---

![Image description](Q-POINT01-EXP02.png)

# TRANSIENT ANALYSIS

Transient analysis studies the response of the circuit to time-varying input signals.

From waveform measurements:

Maximum output voltage

Vmax = 930.23 mV

Minimum output voltage

Vmin = 634.74 mV

Output peak-to-peak voltage

Vout(pp) = Vmax − Vmin

Vout(pp) = 930.23 − 634.74

Vout(pp) = 295.49 mV

Input signal amplitude

Vin(pp) = 20 mV

---



# Voltage Gain Calculation

Voltage gain:

Av = Vout(pp) / Vin(pp)

Av = 295.49 / 20

Av ≈ 14.77 V/V

---

# Gain in Decibels

Gain(dB) = 20 log10(Av)

Gain = 20 log10(14.77)

Gain ≈ 23.38 dB

---
![Image description](TRANSIENTVOUT01-EXP02.png)

# AC ANALYSIS – GAIN AND BANDWIDTH CALCULATION

AC analysis determines the **frequency response of the amplifier**.

From the AC plot:

Midband gain ≈ 23.7 dB

Convert to linear scale:

Av = 10^(23.7 / 20)

Av ≈ 15.34 V/V

---
![Image description](AC01-EXP02.png)

## Bandwidth

The −3 dB bandwidth occurs at approximately:

BW ≈ 15 MHz

This is the frequency where the gain drops by **3 dB from the midband gain**.

---
![Image description](BW01-EXP02.png)

## Unity Gain Bandwidth

Unity Gain Bandwidth is given by:

UGB = Av × BW

UGB = 15.34 × 15 MHz

UGB ≈ 230 MHz

From the AC simulation plot, the unity gain frequency observed is approximately:

UGB ≈ 244 MHz

The slight difference occurs due to **parasitic capacitances and non-ideal transistor behavior**.

---
![Image description](UGB01-EXP02.png)

# RESULT

The CMOS amplifier using **NMOS transistor with PMOS active load** was successfully designed and simulated using **TSMC 180 nm technology**.

DC operating point analysis confirmed a drain current of approximately **250 µA** and an output voltage close to **0.8 V**, validating correct biasing.

Transient analysis showed amplified output with approximately **295 mV peak-to-peak output voltage**, giving a voltage gain of about **14.77 V/V (23.38 dB)**.

AC analysis provided a **midband gain of approximately 23.7 dB** and a **bandwidth of around 15 MHz**. The calculated unity gain bandwidth was approximately **230 MHz**, which closely matched the simulated unity gain frequency of about **244 MHz**.

---

# INFERENCE

The experiment successfully demonstrated the design and analysis of a **CMOS amplifier using NMOS as the amplifying device and PMOS as the active load**.

DC analysis confirmed that the transistors operate in the saturation region, ensuring proper biasing. Transient analysis verified signal amplification, while AC analysis validated the expected gain and bandwidth characteristics.

The close agreement between theoretical calculations and simulation results confirms the effectiveness of CMOS amplifier design using **LTspice and TSMC 180 nm technology**.


# EXPERIMENT 03

# AIM

Design and analyze a **CMOS amplifier with PMOS active load and NMOS current source biasing** using **TSMC 180 nm CMOS technology** and characterize the circuit performance using:

- **DC Operating Point Analysis**
- **Transient Analysis**
- **AC Small Signal Analysis**

Specifications:

| Parameter | Value |
|----------|------|
| Supply Voltage | **VDD = 1.2 V** |
| Drain Current | **ID = 250 µA** |
| Load Capacitance | **CL = 0.5 pF** |
| Channel Length | **L = 360 nm** |

Simulation tool used: **LTspice**

---

# COMPONENTS REQUIRED

1. PMOS transistor (TSMC 180nm model)  
2. NMOS transistor (TSMC 180nm model)  
3. DC voltage sources  
4. Signal voltage source  
5. Capacitor CL  

---

# THEORY

MOSFETs form the fundamental building blocks of modern integrated circuits. CMOS technology combines **NMOS and PMOS devices** to achieve high performance with low power consumption.

In this circuit:

- **M1 (PMOS)** acts as an **active load**
- **M3 (NMOS)** acts as the **amplifying transistor**
- **M4 (NMOS)** acts as a **current source**

This configuration provides:

- High output resistance  
- Stable biasing  
- High input impedance  

However, because of **source degeneration caused by the current source transistor**, the voltage gain may reduce compared to a simple common source amplifier.

---

# SATURATION CONDITIONS

### NMOS Saturation

$$
V_{GS} > V_T
$$

$$
V_{DS} \ge V_{OV}
$$

where

$$
V_{OV} = V_{GS} - V_T
$$

---

### PMOS Saturation

$$
V_{SG} > |V_T|
$$

$$
V_{SD} \ge V_{OV}
$$

where

$$
V_{OV} = V_{SG} - |V_T|
$$

---

# PROCEDURE

### 1. Include Technology Model

The TSMC 180 nm model library was included using:

```
.lib tsmc018.lib
```

---

### 2. Build CMOS Amplifier Circuit

The circuit consists of:

- PMOS transistor connected to **VDD**
- NMOS transistor acting as **gain stage**
- NMOS transistor acting as **current source**
- Output taken from the **drain node**
- Load capacitor connected at the output

---

# DESIGN CALCULATIONS

## 1. Output Voltage Selection

The output voltage is chosen as:

$$
V_{out} = \frac{V_{DD}}{2} + V_{OS}
$$

Given:

$$
V_{OV} = 0.25V
$$

Taking:

$$
V_{OS} = 0.3V
$$

Therefore:

$$
V_{out} = 0.6 + 0.3 = 0.9V
$$

---

## 2. Drain Current Selection

Design current:

**ID = 250 µA**

---

## 3. Bias Voltage for PMOS

$$
V_{SG} = V_{OV} + |V_{TP}|
$$

$$
V_{SG} = 0.25 + 0.39
$$

$$
V_{SG} = 0.64V
$$

Since

$$
V_{SG} = V_S - V_G
$$

$$
0.64 = 1.2 - V_G
$$

$$
V_G = 0.56V
$$

Therefore

**VB1 = 0.56 V**

---

## 4. Bias Voltage for NMOS Current Source

$$
V_{OV} = V_{GS} - V_T
$$

$$
0.25 = V_{GS} - 0.36
$$

$$
V_{GS} = 0.61V
$$

$$
V_{B2} = V_{GS} + V_{OS}
$$

$$
V_{B2} = 0.61 + 0.3
$$

$$
V_{B2} = 0.91V
$$

---

# DEVICE DIMENSIONS

### Initial Calculated Widths

| Parameter | Value |
|----------|------|
| Wn | **12.5 µm** |
| Wp | **29.57 µm** |
| L | **360 nm** |

---

### Final Width After Adjustment

| Parameter | Value |
|----------|------|
| Wn | **31.5 µm** |
| Wp | **74.8 µm** |
| L | **360 nm** |

---

# CIRCUIT

<p align="center">
<img src="CIRCUIT.png" width="420">
</p>

<p align="center">
<b>Fig 1: CMOS Amplifier Circuit</b>
</p>

---

# DC ANALYSIS

DC analysis determines the **operating point (Q-point)** of the MOSFET amplifier.

---

# Q-POINT VERIFICATION

### Using Calculated Width

Simulation produced:

**Drain Current**

ID ≈ **99.7 µA**

**Output Voltage**

Vout ≈ **0.8758 V**

The difference from theoretical values occurs due to:

- Short channel effects  
- Mobility degradation  
- Channel length modulation  
- Non-ideal BSIM transistor model

---

### After Width Adjustment

Final simulation results:

| Parameter | Value |
|----------|------|
| Drain Current | **ID ≈ 249.77 µA** |
| Output Voltage | **Vout ≈ 0.9047 V** |

These values closely match the design targets.

---

# TRANSIENT ANALYSIS

Transient analysis observes circuit response for time-varying input signals.

<p align="center">
<img src="TRANSIENT.png" width="720">
</p>

<p align="center">
<b>Fig 2: Transient Response</b>
</p>

---

### Output Peak-to-Peak Voltage

Maximum output voltage:

**Vmax = 913.417 mV**

Minimum output voltage:

**Vmin = 896.056 mV**

$$
V_{out(pp)} = V_{max} - V_{min}
$$

$$
V_{out(pp)} = 913.417 - 896.056
$$

$$
V_{out(pp)} = 17.36mV
$$

---

### Input Signal

**Vin(pp) = 19.11 mV**

---

# Theoretical Gain

*(To be filled based on theoretical small-signal analysis)*

---

# Simulation Gain

$$
A_v = \frac{V_{out(pp)}}{V_{in(pp)}}
$$

$$
A_v = \frac{17.36}{19.11}
$$

$$
A_v ≈ 0.908 \; V/V
$$

---

### Gain in Decibels

$$
Gain(dB) = 20\log_{10}(A_v)
$$

$$
Gain ≈ -0.83 dB
$$

The gain is slightly less than unity because of **source degeneration introduced by the current source transistor.**

---

# AC ANALYSIS – GAIN AND BANDWIDTH

AC analysis determines the **frequency response of the amplifier.**

<p align="center">
<img src="AC_ANALYSIS.png" width="720">
</p>

<p align="center">
<b>Fig 3: AC Frequency Response</b>
</p>

---

## Midband Gain

From the flat region of the Bode plot:

**Gain ≈ −0.845 dB**

Convert to linear scale:

$$
A_v = 10^{\frac{-0.845}{20}}
$$

$$
A_v ≈ 0.908 \; V/V
$$

---

## −3 dB Bandwidth

From the AC plot:

**BW ≈ 104.75 MHz**

This corresponds to the frequency where the gain falls **3 dB below the midband gain.**

---

## Unity Gain Frequency

In this circuit the **unity gain (0 dB) frequency is not observed.**

Reason:

- Midband gain is **less than 1 (negative dB)**  
- Therefore the gain **never crosses 0 dB**  
- The circuit behaves more like a **source-degenerated amplifier stage**

---

# RESULT

The CMOS amplifier with PMOS active load and NMOS current source biasing was successfully designed and simulated using **TSMC 180 nm technology**.

The **DC operating point** showed:

- **Drain current ≈ 249.77 µA**
- **Output voltage ≈ 0.9047 V**

Transient analysis produced a gain of approximately:

**0.908 V/V**

AC analysis showed:

- **Midband gain ≈ −0.845 dB**
- **Bandwidth ≈ 104.75 MHz**

---

# INFERENCE

The CMOS amplifier was successfully designed and analyzed using LTspice.

DC analysis confirmed correct biasing in the saturation region. Transient analysis verified signal amplification, while AC analysis revealed wide bandwidth but slightly reduced gain due to source degeneration.

Differences between theoretical and simulated values arise from **non-ideal transistor effects such as channel length modulation, parasitic capacitances, and mobility degradation in the TSMC 180 nm model.**
