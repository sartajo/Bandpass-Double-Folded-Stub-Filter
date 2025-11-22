# 🛰️ RF Bandpass Filter Design

I designed and simulated a **wideband microstrip bandpass filter** using AWR Microwave Office and later manufactured the design. The goal was to build a compact, FR-4-based filter centered around ~2 GHz using **folded open-stub resonators**.

---

## 🎯 What I Built

I implemented a **double folded-stub bandpass filter** on an FR-4 substrate (εr 4.4, h = 1.5 mm).

The design is fully symmetrical and uses microstrip transmission lines with carefully tuned lengths to hit the desired passband.

- Substrate: **FR-4**, εr = 4.4, tanδ = 0.01
- Transmission line width: **2.793 mm** (for 50 Ω)
- Center frequency: **~1.9–2.0 GHz**
- Overall bandwidth: **~1.0 GHz**

---

## 📡 How the Filter Works

The filter uses **two open-circuited stubs** that act as resonators. When these resonators are tuned to slightly different electrical lengths, their responses overlap and create a **wide, smooth passband**.

I verified the electrical lengths using TXLINE:

- **Stub 1 (40 mm)** → ~**175°** electrical length → behaves like a **λg/2 resonator**
- **Stub 2 (35 mm)** → ~**153°** → slightly detuned from λg/2

This dual-resonance structure is what produces the filter’s **strong return-loss dips** and its **1.5–2.5 GHz** usable passband.

---

## 📈 Key Results

### ✔ Wide passband

|S21| ≈ 0 to −3 dB from **1.5 GHz to 2.5 GHz**

### ✔ Strong return loss

|S11| dips below **−40 dB** in the passband

### ✔ Excellent symmetry

S11 ≈ S22 and S21 ≈ S12, confirming a reciprocal, symmetric design

### ✔ Low loss

Measured insertion loss at 2 GHz: **~0.34 dB**

(~7% power lost due to dielectric + conductor losses on FR-4)

---

## 🛠️ Tools & Skills Used

- **AWR Microwave Office** (schematic design + S-parameter simulation)
- **TXLINE** (impedance, width, and electrical length verification)
- **RF transmission line theory**
- **Filter design (λ/2 resonators, microstrip stubs)**
- **S-parameter interpretation & analysis**
- **FR-4 high-frequency modeling**

---

## 📌 Design Summary

<img width="975" height="599" alt="image" src="https://github.com/user-attachments/assets/611e5937-b814-46af-b083-3c45bd4d4850" />

Figure 1: Circuit Schematic in AWR

<img width="975" height="484" alt="image" src="https://github.com/user-attachments/assets/592b4848-1677-4323-905f-a2b475e87add" />

Figure 2: Reflection Coefficient dB Mag Plot

From the plot of |S11| and |S22| (dB), the filter is well matched when the return loss exceeds 10 dB (|S11|dB, |S22|dB ≤ -10 dB). This occurs from approximately 1.50 GHz to 2.50 GHz. The best match occurs near the center of this range, around 1.85-1.90 GHz, where both |S11| and |S22| reach minimum values of about -40 dB.

<img width="975" height="430" alt="image" src="https://github.com/user-attachments/assets/58009685-31b0-4237-bdc5-77a842c215d7" />

Figure 3: Transmission vs. Reflection Coefficient dB Mag Plot

The |S11| and |S21| dB-magnitude plots show typical bandpass behavior. Inside the passband (approximately 1.7-2.2 GHz), the transmission coefficient |S21| is high (0 to -3 dB), indicating low insertion loss, while the reflection coefficient |S11| is very low (below -20 dB), indicating good matching. Outside this frequency range, |S21| drops sharply to below -20 dB, and |S11| rises toward 0 dB, meaning the input power is reflected. Therefore, this circuit behaves as a bandpass filter.

<img width="975" height="428" alt="image" src="https://github.com/user-attachments/assets/ee546f8b-475e-4799-a631-76276592fdca" />

Figure 4: Transmission Coefficients Linear Mag Plot

From the linear transmission plot, the 3dB passband is defined by the range where ∣S_21∣is approx 0.78. The filter meets this threshold approximately from approx. 1.5 GHz to 2.5 GHz, giving a 3dB bandwidth of about 1.0 GHz. |S21| and |S12| fully overlap, confirming the reciprocal nature of the circuit.

<img width="975" height="484" alt="image" src="https://github.com/user-attachments/assets/1e6b350a-d0b3-4842-8292-51d8c3855a4c" />

Figure 5: Transmission Coefficients Phase Plot

The phase plots of S21 and S12 overlap across the entire frequency range, showing that their phases are identical. Together with the magnitude results from Part C, this confirms that the circuit is reciprocal (S21 = S12). The phase decreases linearly with frequency, consistent with transmission-line delay within the filter.

<img width="975" height="447" alt="image" src="https://github.com/user-attachments/assets/a04b6987-8625-4a16-9d2e-ebe3af1e001d" />

Figure 6: Input at Port 1 S-parameter Linear Mag Plots

|S21| = 0.9626
|S11| = 0.01484
Pref = ∣S11∣^2 = (0.01484)^2
P_"ref" =0.0002202
P_transmitted=|S21|^2=(0.9626)^2
P_"transmitted" =0.9266
P_loss=1-(P_ref+P_transmtted)

P_"loss" =1-(0.0002202+0.9266)
P_"loss" =1-0.9268202=0.07318
∣S11^2=2.20×10-4,∣S21^2=0.9266
Ploss=1-(∣S11|^2 +∣S21^2)=1-(0.00022+0.9266)=0.0732

Approximately 7.3% of the input power is lost due to dielectric loss (tan δ = 0.01), conductor loss, radiation/discontinuity loss, and nonideal microstrip behaviour.

<img width="471" height="274" alt="image" src="https://github.com/user-attachments/assets/38ad7fe7-721a-4ee9-960f-0ae6ed161933" /> Figure 7: 40mm 
<img width="470" height="278" alt="image" src="https://github.com/user-attachments/assets/3ed33af5-c4c6-46e7-a8ed-02fefd747410" /> Figure 8: 35mm

Using TXLINE with the substrate (εr = 4.4, h = 1.5 mm, W = 2.793 mm), the guided wavelength at 2 GHz is approximately λg = 82 mm, and λg/2 = 41 mm. The two folded stubs in the filter have physical lengths L₁ = 40 mm and L₂ = 35 mm. TXLINE outputs electrical lengths of approximately 175° and 153°, respectively. Therefore, the first stub is essentially a half-wavelength (λg/2) resonator, while the second stub is slightly shorter than λg/2. These two staggered resonances combine to produce the wide bandpass response observed in the S-parameter plots.
