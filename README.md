# Self-Powered Smart Knee Sleeve for Gait and Joint Angle Monitoring

An end-to-end, wearable Biomedical Engineering project integrating a **Triboelectric Nanogenerator (TENG)**, high-impedance signal conditioning circuitry, ESP32 BLE telemetry, and Python biomechanical data analytics. 

This repository serves as the practical implementation and documentation for a self-powered joint tracking sleeve designed for continuous telerehabilitation and kinematic gait analysis.

---

## 📌 Project Overview

Traditional wearable sensors for joint monitoring often require constant battery power and rigid form factors. This project utilizes the **triboelectric effect** (contact electrification and electrostatic induction) to generate self-powered electrical signals directly from knee joint motion.

- **Sensor Layer:** Flexible PTFE-Nylon contact-separation TENG patch integrated into a neoprene knee sleeve.
- **Hardware Layer:** Ultra-high input impedance JFET buffer circuit with active analog low-pass filtering.
- **Embedded Layer:** ESP32 ADC acquisition ($100\text{ Hz}$) streaming via Bluetooth Low Energy (BLE).
- **Analytics Layer:** Digital bandpass filtering, peak detection, and gait frequency analysis using Python (`SciPy`/`NumPy`).

---

## 🛠️ Repository Structure

```text
├── hardware/
│   ├── schematics/          # Circuit diagrams & op-amp buffer designs
│   └── bom.md               # Bill of Materials and Sri Lanka local sourcing guide
├── firmware/
│   └── teng_ble_firmware/   # ESP32 C++ Arduino IDE code for ADC sampling & BLE
├── analytics/
│   └── signal_processing.py # Python script for peak detection & gait cycle analysis
├── docs/
│   └── project_manual.pdf   # Complete step-by-step build & theory manual
└── README.md
```

---

## ⚡ Hardware Architecture & Circuitry

TENG sensors generate high open-circuit voltages ($V_{oc} > 10\text{ V}$) but extremely low load currents ($I < 1\,\mu\text{A}$). Direct connection to a microcontroller ADC will collapse the output voltage. 

### Circuit Flow
`[TENG Patch]` $\rightarrow$ `[10 MΩ Bias + Zener Clamp]` $\rightarrow$ `[TL072 JFET Op-Amp Buffer]` $\rightarrow$ `[Active Low-Pass Filter (fc = 15Hz)]` $\rightarrow$ `[ESP32 ADC Pin]`

* **Input Stage:** 10 M$\Omega$ input resistor for bias current path paired with dual 3.3V anti-parallel Zener diodes for over-voltage protection.
* **Buffer & Filtering:** JFET-input TL072 voltage follower for impedance matching coupled with a 2nd-order active low-pass filter to reject $50\text{ Hz}$ power-line interference.

---

## 📋 Bill of Materials (BOM)

| Component | Description | Function |
| :--- | :--- | :--- |
| **Friction Layers** | PTFE (Teflon Tape) + Nylon Fabric | Triboelectric contact pairs (electron donor/acceptor) |
| **Electrodes** | Conductive Copper Foil / Fabric Tape | Top and bottom flexible charge collectors |
| **Substrate** | Neoprene Compression Knee Sleeve | Wearable joint mounting base |
| **Op-Amp** | TL072 / AD8605 JFET-Input IC | High-impedance unity-gain voltage buffer |
| **Microcontroller** | ESP32 NodeMCU | Wireless BLE node & 12-bit ADC acquisition |
| **Validation Sensor** | MPU6050 6-DOF IMU | Ground-truth kinematic joint angle reference |

---

## 🚀 Getting Started

### 1. Embedded Setup (ESP32)
1. Open `firmware/teng_ble_firmware/teng_ble_firmware.ino` in Arduino IDE.
2. Select your ESP32 board and upload the code.
3. Open the Serial Plotter at 115200 baud to monitor live voltage output.

### 2. Analytics Setup (Python)
1. Clone the repository and install dependencies:
   ```bash
   git clone https://github.com/Abdul-Rahman-bme/Self-Powered-Smart-Knee-Sleeve-for-Gait-and-Joint-Angle-Monitoring.git
   cd smart-knee-sleeve-teng
   pip install numpy matplotlib scipy
   ```
2. Run the signal processing pipeline:
   ```bash
   python analytics/signal_processing.py
   ```

---

## 🔬 Target Applications & Portfolio Focus

* Continuous Home Telerehabilitation Monitoring
* Battery-Free Biomechanical Wearables & E-Textiles
* Gait Cycle & Joint Flexion Frequency Tracking

Author : Abdul Rahman Mohamed
University of Moratuwa
