NAVGHOST [MAIN] REPO LINK - https://github.com/DSGAMING98/SIH26168-IDR 

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=7AA2F7&center=true&vCenter=true&width=800&height=50&lines=%F0%9F%9B%B0%EF%B8%8F+NavGhost+v2.3.3;AI-ML+Assisted+Dead+Reckoning+for+Seamless+Navigation;When+GNSS+disappears%2C+navigation+shouldn't+have+to." alt="Typing SVG" />

<img src="https://img.shields.io/badge/SIH-2026-7AA2F7?style=for-the-badge" />
&nbsp;
<img src="https://img.shields.io/badge/Problem%20Statement-SIH26168-7AA2F7?style=for-the-badge" />
&nbsp;
<img src="https://img.shields.io/badge/Organization-ISRO-7AA2F7?style=for-the-badge" />
&nbsp;
<img src="https://img.shields.io/badge/Platform-Android-7AA2F7?style=for-the-badge&logo=android&logoColor=white" />

NavGhost is a smartphone-first intelligent dead reckoning system built for navigation scenarios where GNSS/GPS becomes unavailable or unreliable.

*Don't stop navigating just because GNSS stopped talking.*

---

### 🚀 What is NavGhost?

Normal smartphone navigation depends heavily on continuous GNSS availability. But real environments are messy:

| | |
|---|---|
| 🚇 | Tunnels |
| 🅿️ | Underground parking |
| 🏙️ | Urban canyons |
| 🌲 | Dense or obstructed areas |
| 📡 | Temporary GNSS degradation or loss |

When GNSS disappears, a conventional navigation system may stop updating, freeze, or wait for a new fix. **NavGhost takes a different approach** — it combines the phone's GNSS, accelerometer, gyroscope and orientation data with sensor fusion and AI-assisted motion estimation to keep producing a navigation estimate during GNSS outages.

---

### 🧠 Architecture

```
        GNSS
          │
          ▼
┌──────────────────┐
│   SENSOR FUSION   │
│  GNSS + IMU +     │
│  Orientation      │
└────────┬──────────┘
         │
         ▼
   ┌─────────────┐
   │     EKF     │
   │ State +     │
   │ Bias Est.   │
   └──────┬──────┘
          │
          ▼
   ┌─────────────┐
   │     GRU     │
   │ Velocity    │
   │ Correction  │
   └──────┬──────┘
          │
          ▼
 ┌───────────────────┐
 │  NAVIGATION STATE  │
 │  Position          │
 │  Speed             │
 │  Heading           │
 │  Uncertainty       │
 └────────────────────┘
```

During GNSS loss, the system continues estimating motion using onboard sensors and tracks increasing uncertainty until GNSS becomes available again.

---

### ✨ What's Inside v2.3.3

<table>
<tr>
<td width="50%" valign="top">

**🗺️ Live Navigation**
- Real-time position tracking
- Speed and heading
- Distance covered
- Position uncertainty
- 2D / 3D map view
- Chase/navigation camera
- Route directions & destination search
- Voice navigation

</td>
<td width="50%" valign="top">

**📡 GNSS Loss Handling**
- Normal Navigation → GNSS Loss
- Dead Reckoning → Uncertainty Tracking
- GNSS Returns → Fix Validation
- Smooth Reacquisition → Normal Navigation

*Designed to avoid simply resetting state when GNSS returns.*

</td>
</tr>
<tr>
<td width="50%" valign="top">

**🧭 Startup Calibration**
- Guided initial sensor alignment
- Accounts for phone orientation ↔ vehicle motion
- No fixed-mount assumption

</td>
<td width="50%" valign="top">

**🧠 AI-Assisted Motion Estimation**
- **EKF** — position, speed, yaw, accel/gyro bias
- **GRU** — lightweight velocity residual/correction

</td>
</tr>
</table>

---

### 📈 Uncertainty Awareness

Dead reckoning is not treated as perfect positioning. As GNSS becomes unavailable, NavGhost tracks the growing uncertainty of its navigation estimate — distinguishing **where** the vehicle is estimated to be from **how confident** the system is about that estimate.

---

### 🧪 Built-in Evaluation Tools

| Tool | Purpose |
|---|---|
| ⚡ **Quick Judge Demo** | Controlled replay environment — deterministic replay, GNSS state transitions, synthetic tunnel trigger, start/pause/reset |
| 📊 **Public Benchmark** | Compares navigation estimates against a reference scenario (evaluation, not a universal accuracy guarantee) |
| 🔬 **System Diagnostics** | Sensor sampling, GNSS availability/age, satellite info, TTFF, engine processing time, rendering performance, battery/thermal, runtime health |
| 🧪 **Field Test** | Guided workflow for real-vehicle testing with local session recording |

---

### 📍 Navigation Beyond the Map

- 📌 **Nearby Places** — fuel, parking, hospitals, EV charging, repair, pharmacies, police, restaurants, ATMs
- 🗂️ **Trip History** — distance, duration, average speed, session date/time, completion state
- 📈 **Local Insights** — trip performance, GNSS/IDR timeline, GNSS-loss events, IDR support distance/time, average uncertainty
- 🖥️ **Background Navigation** — continues as a foreground/background service
- 💾 **Local Session Recording** — exportable for debugging, research, reproducibility

---

### 🧩 Technology Stack

| Layer | Technology |
|---|---|
| Mobile | Kotlin + Android |
| Navigation | GNSS + IMU Sensor Fusion |
| Estimation | Extended Kalman Filter |
| ML Correction | GRU |
| ML Pipeline | Python + PyTorch |
| Data Processing | NumPy + Pandas |
| Maps | Google Maps / MapLibre |
| Map Data | OpenStreetMap where applicable |
| Communication | WebSocket |
| Backend/API tooling | FastAPI |
| Local Data | SQLite / local storage |
| Development | Android Studio / VS Code |
| Version Control | Git + GitHub |

<img src="https://skillicons.dev/icons?i=kotlin,androidstudio,python,pytorch,fastapi,sqlite,git,github,vscode&theme=dark" />

---

### 🔐 Privacy & Data Handling

NavGhost is designed around **local-first navigation and analytics**. The core dead-reckoning calculation runs on the phone — no cloud service required. Local session data can be recorded and exported when needed for testing or analysis. Optional laptop telemetry is available through the Command Center workflow, while navigation itself remains on-device.

---

### 📱 Installation

**Requirements:** Android 8.0 (API 26+) · GNSS/GPS · Accelerometer · Gyroscope · Location permission

```
01  Install APK
02  Grant permissions
03  Keep the phone securely mounted
04  Wait for GNSS
05  Complete calibration
06  Start navigation
07  Explore Live Navigation
08  Try Quick Judge Demo
09  Check System Diagnostics
10  Explore Insights & Trip History
```

> ⚠️ For field testing, mount the phone securely and keep attention on the road. Do not interact with the application while driving.

---

### 🛣️ Roadmap

```
SMARTPHONE → FIELD VALIDATION → NAVIGATION / FLEET PILOTS
    → EDGE DEAD-RECKONING ENGINE → EXTERNAL IMU / MOBILITY INTEGRATION
    → LARGER NAVIGATION SYSTEMS
```

Potential extensions: fleet & logistics, mobility platforms, GNSS-challenged environments, research vehicles, edge navigation systems.

---

### ⚠️ Important Notes

NavGhost v2.3.3 is a **research / prototype build**, not a certified navigation or safety-critical system. Performance can vary with smartphone hardware, sensor quality, phone placement, vehicle dynamics, road conditions, GNSS environment, calibration quality, and duration of GNSS outage. Current validation is based on available datasets and test scenarios — results should be read as experimental evaluation, not a universal guarantee.

---

### 📦 Release Assets

```
📦 Assets
├── NavGhost-v2.3.3.apk
├── NavGhost-v2.3.3-release-notes.pdf   [if available]
└── checksums.txt                        [optional]
```

<img src="https://img.shields.io/badge/Version-v2.3.3-7AA2F7?style=for-the-badge" />
&nbsp;
<img src="https://img.shields.io/badge/Release-SIH%202026%20Prototype-7AA2F7?style=for-the-badge" />

---

**🛰️ NAVGHOST v2.3.3**

*AI-ML Assisted Intelligent Dead Reckoning*

GNSS + IMU • EKF • GRU • Edge AI • Android

Built for SIH 2026 • SIH26168 • ISRO
