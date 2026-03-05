# NOT COMPLETED

# EXPERIMENT 02

# AIM

Design and analyze a **CMOS amplifier configuration** using **TSMC 180nm CMOS technology** and characterize the performance of the designed circuit using:

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
6. Capacitor (CL)

---

# THEORY

MOSFETs are the fundamental building blocks of modern electronic integrated circuits. CMOS technology uses both **NMOS and PMOS transistors**, allowing high performance with low power consumption.

In this experiment, a **CMOS amplifier** is implemented where:

* **NMOS transistor acts as the amplifying device**
* **PMOS transistor acts as an active load**
* **Source degeneration resistor (RS)** provides bias stability

Advantages of this configuration:

* High voltage gain
* Improved bias stability
* Reduced distortion due to source degeneration
* High input impedance

For proper amplifier operation, MOSFETs must operate in the **saturation region**, where they behave as voltage-controlled current sources.

---

# SATURATION CONDITIONS

### NMOS Saturation Condition

VGS > VT

VDS ≥ VOV

where

VOV = VGS − VT

---

### PMOS Saturation Condition

VSG > |VT|

VSD ≥ VOV

where

VOV = VSG − |VT|

---

# PROCEDURE

1. **Include Technology Model**

The TSMC 180nm model library was included in LTspice using:

.lib tsmc018.lib

---

2. **Build the CMOS Amplifier Circuit**

The circuit consists of:

* PMOS transistor connected to **VDD**
* NMOS transistor connected to **source resistor**
* Output taken at the **drain node**
* Bias voltages applied to the transistor gates

---

3. **Initial Device Parameters**

The channel length was fixed as:

L = 360 nm

Initial width values were chosen based on theoretical calculations.

---

4. **DC Operating Point Analysis**

The .op command was executed in LTspice to determine:

* Drain current
* Output voltage
* Node voltages

---

5. **Bias Adjustment**

Transistor widths were adjusted until the required operating point was achieved:

ID ≈ 250 µA
Vout ≈ 0.8 V

---

6. **Transient Analysis**

A small sinusoidal signal was applied to the input and **.tran analysis** was performed to observe time-domain amplification.

---

7. **AC Small Signal Analysis**

AC magnitude was set to **1 V**, and **.ac analysis** was used to obtain:

* Midband gain
* Frequency response
* Bandwidth

---

# DESIGN CALCULATIONS

## 1. Drain Current Selection

The design drain current was selected as:

ID = 250 µA

---

## 2. Source Resistor Calculation

Voltage across the source resistor:

VRS = 0.2 V

Using Ohm's law:

RS = VRS / ID

RS = 0.2 / (250 × 10⁻⁶)

RS = 800 Ω

---

## 3. Output Voltage Selection

The output voltage was chosen as:

Vout = VDD / 2 + IDRS

Vout = 0.6 + 0.2

Vout = 0.8 V

---

## 4. Gate Bias Voltage

For NMOS:

VGS = 0.61 V

Source voltage:

VS = IDRS = 0.2 V

Therefore:

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

![Circuit](CIRCUIT.png)

---

# DC ANALYSIS

DC analysis determines the **operating point (Q-point)** of the MOSFET amplifier and verifies that the transistors operate in the **saturation region**.

This ensures proper amplification and stable circuit operation.

---

# Q-POINT VERIFICATION USING DC OPERATING POINT ANALYSIS

Using the .op command in LTspice, the following values were obtained:

Drain current ID = 0.000250418 A ≈ 250 µA

Output voltage Vout = 0.798 V

Theoretical output voltage:

Vout = 0.8 V

The simulated value closely matches the theoretical design target, confirming correct biasing.

---

# TRANSIENT ANALYSIS

Transient analysis studies the response of the circuit to time-varying input signals.

From the waveform cursors:

Maximum output voltage

Vmax = 930.23 mV

Minimum output voltage

Vmin = 634.66 mV

Output peak-to-peak voltage:

Vout(pp) = Vmax − Vmin

Vout(pp) = 930.23 − 634.66

Vout(pp) = 295.57 mV

Input signal amplitude:

Vin(pp) = 20 mV

---

# Voltage Gain Calculation

Voltage gain:

Av = Vout(pp) / Vin(pp)

Av = 295.57 / 20

Av = 14.77 V/V

---

# Gain in Decibels

Gain(dB) = 20 log10(Av)

Gain = 20 log10(14.77)

Gain ≈ 23.38 dB

---

# AC ANALYSIS – GAIN AND FREQUENCY RESPONSE

AC analysis determines the **frequency response of the amplifier**.

From the AC plot:

Midband gain ≈ 23.7 dB

Measured at approximately:

f ≈ 10 kHz

The amplifier maintains a constant gain in the midband region before gradually decreasing at higher frequencies.

---

# RESULT

The CMOS amplifier was successfully designed and simulated using **TSMC 180 nm technology**.

DC operating point analysis confirmed a drain current of **250 µA** and an output voltage of **0.798 V**, which closely matches the theoretical value of **0.8 V**.

Transient analysis showed an amplified output signal with **295.57 mV peak-to-peak output**.

The calculated voltage gain from transient analysis was **14.77 V/V**, corresponding to **23.38 dB**.

AC analysis indicated a **midband gain of approximately 23.7 dB**, confirming correct amplifier operation.

---

# INFERENCE

The experiment successfully demonstrated the design and analysis of a **CMOS amplifier using an NMOS amplifying transistor and a PMOS active load**.

DC analysis verified correct biasing in the saturation region.
Transient analysis confirmed proper signal amplification.
AC analysis validated the expected gain and frequency response of the amplifier.

The close agreement between theoretical calculations and simulation results confirms the effectiveness of CMOS amplifier design using LTspice.

