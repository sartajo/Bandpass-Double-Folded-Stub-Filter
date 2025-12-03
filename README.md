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

## 🛠️ Manufactured Filter

![IMG_4663](https://github.com/user-attachments/assets/0ba3e6ee-7ce4-4e5d-b023-8d0eef17273c)
Figure 9: Manufactured Filter 
<img width="815" height="214" alt="image" src="https://github.com/user-attachments/assets/0e6054d3-9233-4948-a310-2215ef0e7ab3" />

Figure 3: Parameter values of the double-folded stub filter of center frequency 1.9 GHZ

The AWR schematic (Figure 1) shows the double-folded stub bandpass filter designed on FR-4 (εr = 4.4, h = 1.5 mm) using 50 Ω microstrip lines and two open-circuited stubs to shape the passband. The fabricated prototype (Figure 9) was built using copper tape cut to the simulated dimensions and soldered at the junctions, with SMA edge-launch connectors added for VNA measurement. The physical layout closely follows the simulated topology, enabling direct comparison between AWR and measured performance.
 
For the reflection coefficient |S11|, the AWR simulation (Figure 2) predicts two deep return-loss minima around 1.8 GHz and 2.0 GHz with levels below –40 dB, and a –10 dB bandwidth from approximately 1.5 GHz to 2.5GHz.

<img width="549" height="411" alt="image" src="https://github.com/user-attachments/assets/c5e30fdc-5283-4c31-ac52-091899537214" />

Figure 10: Reflection Coefficient dB Mag Plot (VNA)

The VNA measurement of the fabricated filter (Figure 10) shows a very similar response: |S11| falls below –10 dB from about 1.64 GHz to 2.48 GHz, with a minimum of roughly –35 dB near 2.1 GHz. The passband and notch shape agree well with the simulation, but the measured response is slightly shifted up in frequency, and the minimum return loss is a bit smaller in magnitude. These differences are consistent with fabrication tolerances, FR-4 dielectric variation, hand-soldered stub lengths, and the additional parasitics from SMA launch transitions.
 
The simulated and measured S-parameters of the bandpass double folded-stub filter show the same overall behaviour.
In AWR, the filter exhibits a passband centred near 2.0 GHz with S21 ≈ −1 dB and return loss better than about −20 dB, and deep transmission zeros around 1.4 GHz and 2.4 GHz where S21 drops below −50 dB.

The VNA measurement (Figure 10) reproduces this shape: the passband also peaks close to 2.0 GHz, with slightly higher insertion loss (about −2 to −3 dB) and somewhat shallower notches, which can be attributed to connector loss, fabrication tolerances, and additional loss from soldered joints and the FR-4 substrate.

<img width="751" height="563" alt="image" src="https://github.com/user-attachments/assets/1709bb84-fedf-498c-8b85-53734246c37c" />

Figure 11: Transmission Coefficients Linear Mag Plot (VNA)

<img width="766" height="575" alt="image" src="https://github.com/user-attachments/assets/d3ef095f-7abe-410b-8611-36944e17e110" />

Figure 12: Transmission Coefficients Linear Mag Plot (VNA)

The simulated S-parameter response of the double-folded stub bandpass filter agrees well with the VNA measurements. Both the dB-magnitude plots and the linear-magnitude plots show a passband from about 1.5–2.5 GHz with peak transmission around 0.9 (about −1 dB) and a deep transmission notch near the center of the band. Small shifts in the notch frequency and a slightly flatter measured passband are mainly due to fabrication tolerances, substrate loss, and parasitics from the SMA launches and soldered microstrip joints.
 
<img width="968" height="726" alt="image" src="https://github.com/user-attachments/assets/3cf8e95f-20ec-4f6b-9814-3bbce998c914" />

Figure 13: Transmission Coefficients Phase Plot (VNA)

The measured transmission phase ∠S_21 from the VNA closely follows the trend predicted by the AWR simulation. In both plots, the phase is approximately linear across the passband (about 1.5–2.5 GHz), decreasing from around +180^∘near the lower edge to about -180^∘at the upper edge, which indicates an almost constant group delay through the filter in the passband. The locations of the phase wraps (±180° discontinuities) in the VNA data occur at nearly the same frequencies as in simulation, showing that the electrical length of the realized structure matches the design reasonably well. Small deviations and extra ripple in the measured phase are likely due to connector and cable effects, as well as fabrication tolerances that are not fully captured in the ideal EM model.
 
<img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/764ea2a4-4fc1-4f4f-a9d5-1229d940e3c4" /> 

Figure 14: Input at Port 1 S-parameter Linear Mag Plots (VNA)

For the input at port 1, the simulated AWR plot (Figure 11) shows the expected bandpass behaviour:
around 2.0 GHz the filter is well matched with ∣S_11∣≈0.015(about -36dB) and high transmission ∣S_21∣≈0.96. Away from the centre frequency, ∣S_11∣rises toward 1 while ∣S_21∣falls, indicating strong reflection at the input and very little power delivered to the load.

The measured VNA data follows the same trend. ∣S_11∣starts near 0.96 at 1 GHz, drops to a minimum of about 0.05 around 1.8 to 1.9 GHz, and then increases again above 0.7 as the frequency approaches 3 GHz. This confirms that the fabricated filter presents a good input match only in the passband and reflects most of the power outside it. Compared with simulation, the measured minimum ∣S_11∣is higher and slightly shifted in frequency, and the peak ∣S_21∣level is offset. These differences are likely caused by connector and solder parasitics, finite substrate loss, and small errors in the realized stub dimensions and VNA calibration.




