# 🚀 AIM-GNSS: ADC & Interference Mitigation for GNSS Resilience  
*A Software-Defined Framework for Evaluating ADC Precision vs. Multi-Antenna Techniques in GNSS Interference Mitigation*

## 📌 Overview
Global Navigation Satellite Systems (**GNSS**) provide critical positioning, navigation, and timing (PNT) data for geomatics applications such as:

✅ **High-precision land surveying & geodesy**  
✅ **Environmental monitoring & disaster management**  
✅ **Precision agriculture & infrastructure planning**  
✅ **Autonomous navigation & transportation**  

### 🚨 Problem Statement
GNSS receivers are increasingly vulnerable to **interference**, including:  

🚨 **Urban RF congestion** → Crowded signals degrade positioning accuracy  
🚨 **Multipath interference** → Signal reflections distort location estimations  
🚨 **Jamming attacks** → Intentional/unintentional RF disruptions block signals  
🚨 **Spoofing threats** → Fake signals manipulate positioning data  

### 🔍 Research Question
> *Can increasing ADC resolution and sampling rate provide comparable resilience to interference as multi-antenna processing?*  

---
## 📊 Theoretical Framework & Key Equations
### **1️⃣ Multi-Antenna Processing & SNR Improvement**
Multi-antenna systems **enhance SNR** through coherent signal processing:

$$
\text{SNR}_{\text{array}} (\text{dB}) = \text{SNR}_{\text{single}} (\text{dB}) + 10\log_{10}(N)
$$
*Equation adapted from:*

> Nossek, J. A., & Ivrlac, M. T. (2008). The why and how of multiantenna systems. *2008 International ITG Workshop on Smart Antennas*, 1-8. https://doi.org/10.1109/WSA.2008.4475529

📌 **Example Gains:**  
- **2 antennas → +3 dB SNR improvement**  
- **8 antennas → +9 dB SNR improvement**  

### **2️⃣ ADC Resolution & SNR Improvement**
Higher ADC bit depth reduces quantization noise:

$$
\text{SNR}_{\text{ADC}} (\text{dB}) = 6.02N + 1.76
$$
*Equation adapted from:*
> W. R. Bennett, *"Spectra of quantized signals,"* in *The Bell System Technical Journal*, vol. 27, no. 3, pp. 446-472, July 1948, doi: [10.1002/j.1538-7305.1948.tb01340.x](https://doi.org/10.1002/j.1538-7305.1948.tb01340.x).



📌 **Example Gains:**  
- **10-bit ADC → +12 dB SNR improvement**  
- **16-bit ADC → +30 dB SNR improvement**  

### **3️⃣ Sampling Rate & SNR Improvement**
Higher **sampling rate (\(f_s\))** reduces aliasing and spreads quantization noise:

$$
\text{SNR}_{\text{OS}} (\text{dB}) = 10 \log_{10}(\text{OSR})
$$

where:

$$
OSR = \frac{f_s}{2f_{\text{signal}}}
$$

*Equation adapted from:*
> S. R. Norsworthy, R. Schreier, and G. C. Temes, *"Delta-Sigma Data Converters: Theory, Design, and Simulation,"* IEEE Press, 1997. [Online]. Available: [IEEE Xplore](https://ieeexplore.ieee.org/document/10161979/).

📌 **Example Gains:**  
- **4 MSPS → +3 dB SNR improvement**  
- **16 MSPS → +9 dB SNR improvement**  

---

## 🎯 Research Hypothesis
| Hypothesis | Expected Outcome |
|------------|----------------|
| **H1**: Higher ADC resolution **reduces quantization noise**, improving GNSS **tracking & SNR stability**. | **SNR improves logarithmically** with ADC bit depth, leading to **better signal acquisition & tracking**. |
| **H2**: Higher sampling rates **enhance resilience to jamming** by improving spectral resolution. | **Higher sampling rates enable better interference detection & rejection**. |
| **H3**: Multi-antenna processing **improves SNR through spatial filtering**, allowing better interference rejection. | **Beamforming techniques (MUSIC, ESPRIT) improve signal selectivity, mitigating jamming & multipath effects.** |
| **H4**: **A hybrid approach (ADC + multi-antenna) optimizes both cost and resilience**. | **Best trade-off between cost, complexity, and interference mitigation.** |

---

## 🛠️ Experimental Approach
AIM-GNSS develops a **modular software-defined GNSS receiver simulation framework** to:  

✅ **Model & analyze ADC precision (bit depth, sampling rate) on GNSS resilience**  
✅ **Implement and evaluate multi-antenna processing (MUSIC, ESPRIT, beamforming)**  
✅ **Compare ADC improvements vs. multi-antenna interference rejection**  
✅ **Simulate jamming & spoofing scenarios to measure performance trade-offs**  

### 📌 Experimental Breakdown
| Step | Objective | Key Metrics |
|------|----------|------------|
| **1️⃣ ADC Resolution & Sampling Rate** | Model ADC bit depths (8, 10, 12, 16-bit) and sampling rates (2, 4, 8, 16 MSPS). | SNR, signal acquisition time, tracking accuracy. |
| **2️⃣ Multi-Antenna Processing** | Implement MUSIC, ESPRIT, and beamforming techniques. | Direction-of-arrival (DoA) accuracy, interference suppression gain. |
| **3️⃣ Jamming & Spoofing Simulation** | Introduce interference scenarios (narrowband jamming, broadband noise, spoofing). | Loss of GNSS lock, tracking recovery time. |
| **4️⃣ ADC vs. Multi-Antenna Benchmarking** | Compare ADC-based improvements with multi-antenna techniques. | Performance trade-off analysis (SNR, tracking, cost-benefit). |

---
### 📌 Experimental Breakdown
| Step | Objective | Key Metrics |
|------|----------|------------|
| **1️⃣ ADC Resolution & Sampling Rate** | Model ADC bit depths (8, 10, 12, 16-bit) and sampling rates (2, 4, 8, 16 MSPS). | SNR, signal acquisition time, tracking accuracy. |
| **2️⃣ Multi-Antenna Processing** | Implement MUSIC, ESPRIT, and beamforming techniques. | Direction-of-arrival (DoA) accuracy, interference suppression gain. |
| **3️⃣ Jamming & Spoofing Simulation** | Introduce interference scenarios (narrowband jamming, broadband noise, spoofing). | Loss of GNSS lock, tracking recovery time. |
| **4️⃣ ADC vs. Multi-Antenna Benchmarking** | Compare ADC-based improvements with multi-antenna techniques. | Performance trade-off analysis (SNR, tracking, cost-benefit). |

---

## 📂 Repository Structure
AIM-GNSS follows a **modular, version-controlled** structure:

```plaintext
AIM-GNSS/
│── notebooks/                  
│   ├── 01_adc_vs_multi_antenna.ipynb    # ADC vs. multi-antenna trade-off study
│   ├── 02_gnss_signal_processing.ipynb  # Simulating GNSS signals with interference
│   ├── 03_interference_mitigation.ipynb # Evaluating jamming/spoofing resilience
│   ├── 04_algorithm_comparison.ipynb    # MUSIC, ESPRIT, STAP analysis
│   ├── 05_final_benchmark.ipynb         # Consolidated performance comparison
│── src/                         
│   ├── __init__.py                     
│   ├── config.py                         # Experiment configuration settings
│   ├── gnss_receiver.py                  # Parametric GNSS receiver model
│   ├── adc_simulator.py                   # ADC resolution & sampling rate modeling
│   ├── multi_antenna_processing.py        # MUSIC, ESPRIT, Beamforming
│   ├── interference_model.py              # Jamming & spoofing simulation
│   ├── gnss_metrics.py                   # Compute SNR, acquisition accuracy
│   ├── plot_results.py                    # Visualization functions
│── requirements.txt                       
│── environment_setup.sh                   
│── .gitignore                             
│── README.md          
```
---
## Getting Started
### 1️⃣**Installation**
**1️⃣Clone the repository:**
```bash
git clone https://github.com/coustam/AIM-GNSS.git
cd AIM-GNSS