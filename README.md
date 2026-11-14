# Solar-Powered Floating Microplastic Interceptor Dashboard

A modern, industrial IoT telemetry monitoring web application developed for the engineering semester review of the **Solar-Powered Floating Microplastic Interceptor**.

![Dashboard Preview](https://img.shields.io/badge/System-Active_Simulation-0284c7?style=for-the-badge)
![React](https://img.shields.io/badge/React-18.3-61dafb?style=for-the-badge&logo=react)
![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-3.4-38bdf8?style=for-the-badge&logo=tailwind-css)
![Vite](https://img.shields.io/badge/Vite-6.0-646cff?style=for-the-badge&logo=vite)
![Chart.js](https://img.shields.io/badge/Chart.js-4.4-ff6384?style=for-the-badge&logo=chart.js)
![ESP32](https://img.shields.io/badge/ESP32-Hardware_Ready-e7352f?style=for-the-badge&logo=espressif)

---

## 🌊 Project Overview

The **Solar-Powered Floating Microplastic Interceptor** is an autonomous surface-water remediation unit designed for deployment on lakes, urban canals, retention reservoirs, and river estuaries. It captures floating macro-debris, meso-plastics, and microscopic plastic fibers through a multi-stage sequential gradient filtration assembly powered entirely by an off-grid solar photovoltaic array.

This dashboard provides **real-time supervisory control, IoT sensor telemetry monitoring, multi-stage filtration animation, automated alert tracking, and analytical reporting**.

> **Demonstration Mode Notice**: For this semester evaluation, all readings (flow rate, turbidity attenuation, solar power) are generated via an internal stochastic simulation engine clearly watermarked as **"SIMULATION MODE"**. The software architecture is cleanly decoupled with a hardware abstraction layer ready for physical ESP32 and sensor integration.

---

## 🚀 Key Modules & Capabilities

1. **Dashboard Overview**:
   - High-contrast industrial cards displaying System Status, Water Flow Rate ($L/\text{min}$), Initial Intake Turbidity ($\text{NTU}$), Final Outfall Turbidity ($\text{NTU}$), Turbidity Reduction ($\%$), and Solar Generation ($W$).
   - Large cumulative summary metrics: Total filtration cycles, total volume processed, average flow rate, and mean turbidity reduction.
   - Live sparkline charts reflecting continuous stochastic sensor telemetry.

2. **Filtration Process Visualization**:
   - Interactive, animated fluid transit diagram illustrating the full 8-step hydraulic journey:
     $$\text{Contaminated Water Intake} \rightarrow \text{Protective Screen} \rightarrow \text{12V DC Pump} \rightarrow \text{Stage 1 Coarse Mesh} \rightarrow \text{Stage 2 Fine Mesh} \rightarrow \text{Stage 3 Nanofiber} \rightarrow \text{Stage 4 Biochar + Carbon} \rightarrow \text{Clarified Outfall}$$
   - Stage-by-stage engineering cards with micron pore specifications, differential pressures, and particulate capture efficiency.
   - Interactive **START FILTRATION**, **STOP FILTRATION**, and **RESET** controls.

3. **Sensor Monitoring**:
   - **Flow Sensor (Hall-Effect YF-S402)**: Instantaneous flow rate, live rolling chart, min/max/avg statistics, and volumetric integration.
   - **Turbidity Sensor (Analog Optical Light Scatter)**: Real-time dual-line comparison of raw intake vs filtered outfall clarity.
   - **Interactive Perturbation Controls**: Live sliders to simulate sediment influx spikes and altered flow rates during the semester review presentation.
   - **Sensor Connection Diagnostics**: Telemetry link status for ESP32, Flow GPIO, and Turbidity ADC.

4. **Solar Energy Monitoring**:
   - Monocrystalline photovoltaic panel telemetry: Voltage ($18.2\text{V}$), Current ($2.1\text{A}$), Power ($38.2\text{W}$).
   - Power distribution architecture: MPPT Buck-Boost conversion to $12\text{V}$ pump rail and $5\text{V}/3.3\text{V}$ IoT microcontroller rails.
   - Dynamic power balance indicator (Surplus vs Deficit) and diurnal generation trend chart.

5. **Performance Analytics**:
   - Flow rate variance over time.
   - Multi-session comparative bar chart of intake vs outfall turbidity.
   - Auto-generated natural language engineering evaluation summarizing clarity improvements and volumetric throughput.
   - Export buttons for **CSV Data** and **Formatted Engineering Summary Reports**.

6. **Alerts & Notifications**:
   - Rule-based detection monitoring for low flow, filter blockage risks, high intake turbidity, and low solar irradiance.
   - Categorized by severity (Normal $\rightarrow$ Green, Warning $\rightarrow$ Amber, Critical $\rightarrow$ Red).
   - Interactive acknowledgment and log clearing.

7. **Data History**:
   - Full archival table of past and current filtration sessions stored in browser `LocalStorage`.
   - Search by Session ID or notes, status filtering, and multi-column sorting.
   - Granular "View Details" modal for deep inspection of individual session telemetry.

8. **System Settings**:
   - Editable alert detection thresholds (Min Flow, Max Turbidity, Solar Warning).
   - Sampling frequency adjustment ($1.0\text{s}$ to $5.0\text{s}$).
   - Hardware integration configuration (ESP32 IP, REST endpoint, MQTT broker, port, topic).
   - One-click demo data reset to factory state.

9. **About Project**:
   - Comprehensive background documentation, 11 subsystem engineering specification table, and technology stack breakdown.
   - Complete Arduino IDE C++ firmware sketch for ESP32 with one-click copy button.

---

## 🛠️ Technology Stack

- **Framework**: React 18 with Vite
- **Styling**: Tailwind CSS with custom industrial animations and scrollbars
- **Icons**: Lucide React
- **Data Visualization**: Chart.js 4.4 & react-chartjs-2
- **Data Persistence**: HTML5 LocalStorage
- **Export Formats**: RFC 4180 CSV & Plaintext Engineering Reports

---

## ⚡ Quick Start & Run Instructions

### Prerequisites
- Node.js (v18.0 or higher) and npm installed.

### 1. Install Dependencies
```bash
npm install
```

### 2. Start Local Development Server
```bash
npm run dev
```
Open your browser and navigate to:
```
http://localhost:5173
```

### 3. Production Build & Preview
```bash
npm run build
npm run preview
```

---

## 🔌 Future ESP32 Hardware Integration Roadmap

The software architecture is decoupled into a dedicated `sensorService.js` abstraction layer. To connect physical hardware:

1. Flash the provided Arduino sketch (found on the **About Project** page) to an ESP32 board.
2. Wire the **YF-S402 Flow Sensor** to GPIO 18 and the **Analog Turbidity Sensor** to GPIO 34 (ADC1_CH6).
3. Connect the ESP32 to the local Wi-Fi network.
4. In the dashboard's **System Settings** page, toggle mode from `Simulation` to `ESP32 Hardware Mode` and enter your ESP32's IP address.
