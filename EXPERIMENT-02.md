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
