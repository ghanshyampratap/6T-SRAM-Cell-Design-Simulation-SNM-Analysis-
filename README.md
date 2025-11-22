# 🧪 6T SRAM Cell Design, Simulation & SNM Analysis Cadence Virtuoso

## 📝 Abstract
Static Random Access Memory (SRAM) is one of the most significant memory devices used for storing data on-chip. SRAM plays a crucial role in VLSI chips due to its **high storage density**, **fast access time**, and suitability for **low-power applications**.  

This project presents the **design and implementation of a 6T SRAM cell** including:
- Schematic  
- DC Analysis  
- Layout  
- Static Noise Margin (SNM) analysis  

All simulations were performed using **Cadence Virtuoso** in a **90nm CMOS technology**. The SNM curves were analyzed to determine the stability and performance of the 6T SRAM cell.

---

## 📘 Introduction
There are multiple types of semiconductor memory as shown in Fig. 1.

### 📷 Fig 1 – Memory Hierarchy  
<img width="416" height="151" alt="image" src="https://github.com/user-attachments/assets/f9baeb6a-1947-4868-ba24-62631397a4d0" />


SRAM is widely used in battery-operated and low-power devices because of its:
- Low area requirement  
- Low read/write delay  
- No refresh circuitry (unlike DRAM)  

SRAM stores data using **latching circuits**, and being volatile, it loses data when power is switched off.  

### Types of SRAM
1. Non-volatile SRAM  
2. Pseudostatic RAM  
3. By transistor type  
4. By feature  
5. By function  

A typical SRAM cell consists of **six MOSFETs (6T)** — four transistors form two cross-coupled inverters, and two act as access transistors.  

---

# 🔧 CONVENTIONAL 6T SRAM
<img width="260" height="195" alt="image" src="https://github.com/user-attachments/assets/9c3a988e-ee95-4346-bfa3-e153d9f7520c" />



## ⚙️ Working
A 6T SRAM cell consists of:
- **Two cross-coupled inverters:** M1–M2 (inv1), M3–M4 (inv2)  
- **Two access transistors:** M5 & M6 connected to BL and BLB  

Data is stored as a stable state between Q and Q̅.

### ✔ Write Operation
- WL = 1 (enabled)  
- BL and BLB are driven with input data  
- The cross-coupled inverters switch state and write the new data  

### ✔ Read Operation
- WL = 1  
- BL and BLB are precharged to Vdd  
- Depending on stored value, one bitline discharges  
- Sense amplifier detects the differential voltage  

### ✔ Hold Mode
- WL = 0  
- Access transistors OFF  
- Data at Q and Q̅ remains stable  

### 📌 Important Condition  
The cell must be:
- **Weak enough** to be overwritten during write  
- **Strong enough** to retain data during read  

---

# 🔄 READ / WRITE OPERATION (Detailed)

## 📥 READ Operation
- WL = HIGH  
- Consider stored data Q = 1, Q̅ = 0  
- BL remains HIGH  
- BLB discharges → sense amplifier outputs '1'  

Similarly, for Q = 0, Q̅ = 1:
- BL discharges  
- Sense amplifier outputs '0'  

---

## ✍️ WRITE Operation
Consider Q = 0, Q̅ = 1:
- WL = HIGH  
- BLB = 0 (forcing Q̅ low)  
- Potential difference flips the inverter state  
- New data Q = 1, Q̅ = 0 is written  

If BL and BLB do not create voltage difference → memory retains original value.

---

# 📉 Static Noise Margin (SNM) Analysis

## 📘 Theory
SNM determines **stability** of the SRAM cell.  
It is measured by plotting:

- The **VTC** of one inverter  
- The **inverse VTC** of the second inverter  

The two curves form the characteristic **“Butterfly Curve.”**

### 📷 Fig 2 – Standard SRAM Structure  
<img width="260" height="195" alt="image" src="https://github.com/user-attachments/assets/7cd980e2-7071-449c-8a2c-d94028e4e7d5" />



### 📷 Fig 3 – SNM Butterfly Curve  
<img width="600" height="527" alt="image" src="https://github.com/user-attachments/assets/8f24aefe-821e-429f-8b08-7ec08f07d591" />


### SNM Concept
- SNM is the **largest square** that can fit inside the butterfly lobes  
- Higher SNM → better noise immunity  
- SNM reduces during **read operation** and becomes minimum  

Noise source Vn shifts both VTC curves, reducing margin → risk of incorrect read.

---

# 🧪 Simulation Results

## 📷 Schematic of 6T SRAM  
<img width="1203" height="624" alt="image" src="https://github.com/user-attachments/assets/732ac13d-6e48-4d6a-a996-6eea043ff761" />


---

## 📷 SNM Curve / Butterfly Plot  
<img width="1239" height="710" alt="image" src="https://github.com/user-attachments/assets/51ddde90-b912-41ce-847c-be33fa28d620" />


---

## 📷 SRAM Layout  
<img width="578" height="627" alt="image" src="https://github.com/user-attachments/assets/ea6c1da5-cd8b-481f-93aa-c2bda74bba75" />


---

# 🏁 Conclusion
- The analysis of the **6T SRAM cell** was successfully performed.  
- The **Static Noise Margin (SNM)** was measured using butterfly curves for both read and write conditions.  
- All simulations were completed in **Cadence Virtuoso (90nm CMOS)**.  
- Future improvements can enhance noise immunity and robustness under environmental variations.

---

# 🚀 Future Works
Important supporting circuits for SRAM arrays include:

- Row Decoder  
- Column Multiplexer  
- Sense Amplifier  
- Write Driver  
- Precharge Circuit  

These can be added to extend the SRAM system design.

