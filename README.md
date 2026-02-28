# 🧱 Smart Wall Monitoring System

<div align="center">

![Smart Wall Monitoring System](https://img.shields.io/badge/IoT-Structural%20Health%20Monitoring-7C3AED?style=for-the-badge&logo=arduino)
![Hackathon](https://img.shields.io/badge/Quantumard%20Hackathon%202026-Phase%202-F97316?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active%20Build-10B981?style=for-the-badge)
![Cost](https://img.shields.io/badge/Prototype%20Cost-₹%202%2C640-06B6D4?style=for-the-badge)

### *IoT-Powered Structural Health Intelligence — Detect Early. Alert Instantly. Save Lives.*

[🎥 Demo Video](#demo) · [📄 Documentation](#documentation) · [⚡ Quick Start](#quick-start) · [💰 Budget](#financial-budget)

</div>

---

## 📌 Table of Contents

- [About the Project](#about-the-project)
- [Problem Statement](#problem-statement)
- [How It Works](#how-it-works)
- [System Architecture](#system-architecture)
- [Components Used](#components-used)
- [What Makes It Unique](#what-makes-it-unique)
- [Applications](#applications)
- [Financial Budget](#financial-budget)
- [Quick Start](#quick-start)
- [Code Structure](#code-structure)
- [Future Roadmap](#future-roadmap)
- [Team](#team)
- [Submission](#submission)

---

## 🏗️ About the Project

The **Smart Wall Monitoring System** is an IoT-based structural health monitoring solution that **continuously** checks the condition of walls and infrastructure — detecting cracks, moisture intrusion, vibration anomalies, and temperature changes — then transmits this data to the cloud and triggers real-time alerts when safety thresholds are exceeded.

> **No human intervention required. 24/7 autonomous monitoring.**

### 🎯 Core Capabilities

| Feature | Details |
|---------|---------|
| **Sensing** | Crack width, Vibration, Moisture, Temperature |
| **Processing** | Arduino Uno + NodeMCU ESP8266 |
| **Communication** | Wi-Fi (primary) + GSM SIM800L (fallback) |
| **Cloud** | ThingSpeak — real-time dashboard & analytics |
| **Alerts** | Buzzer + SMS + Mobile App notification |
| **Cost** | ₹ 2,640 full prototype |

---

## ⚠️ Problem Statement

Structural deterioration in buildings, bridges, and infrastructure causes thousands of casualties every year. Yet most damage goes **undetected** until catastrophic failure occurs.

```
5,000+     Building collapses per year globally
  40%      Structural failures caused by undetected cracks  
$250B      Annual global infrastructure repair cost
  72hrs    Average time to detect structural damage manually
```

**Current solutions fail because:**
- ❌ Manual inspection is expensive, infrequent, and unreliable
- ❌ Enterprise SHM systems cost ₹5–50 Lakhs — unaffordable for most
- ❌ No early warning means disasters strike without notice
- ❌ Data isn't stored, so no trend analysis or predictive maintenance is possible

---

## ⚙️ How It Works

```
┌─────────────┐    ┌─────────────┐    ┌─────────────────────┐
│   SENSORS   │───▶│     MCU     │───▶│  COMMUNICATION      │
│             │    │             │    │                     │
│ • Crack     │    │ Arduino Uno │    │ Wi-Fi ESP8266        │
│ • Vibration │    │  +          │    │    OR               │
│ • Moisture  │    │ NodeMCU     │    │ GSM SIM800L         │
│ • Temp      │    │             │    │                     │
└─────────────┘    └─────────────┘    └──────────┬──────────┘
                                                  │
                                                  ▼
                                       ┌─────────────────────┐
                                       │   ThingSpeak Cloud  │
                                       │   Dashboard         │
                                       └──────────┬──────────┘
                                                  │
                              ┌───────────────────┴──────────────┐
                              │                                    │
                       ┌──────▼──────┐                   ┌────────▼──────┐
                       │   BUZZER    │                   │  SMS / App   │
                       │   ALARM     │                   │  ALERT       │
                       └─────────────┘                   └──────────────┘
```

### Step-by-Step Process

**Step 1 — Sensor Attachment**
Sensors are mounted on wall surfaces at structurally critical points using adhesive mounts. No drilling required. Deployable in under 30 minutes.

**Step 2 — Continuous Data Capture**
Sensors continuously measure:
- Crack width (flex/strain deformation)
- Vibration amplitude (SW-420)
- Moisture percentage (FC-28)
- Temperature (DHT11)

Readings are collected every **5 seconds**.

**Step 3 — MCU Processing**
Arduino Uno reads analog/digital sensor signals, applies calibration, and converts raw values to engineering units.

**Step 4 — Threshold Logic**
The MCU compares each reading against pre-configured safety thresholds. Any abnormal value triggers the alert sequence immediately.

**Step 5 — Cloud Upload**
NodeMCU ESP8266 transmits data to **ThingSpeak** via Wi-Fi. If Wi-Fi fails, SIM800L GSM module activates as fallback.

**Step 6 — Alert System**
When threshold is exceeded:
- 🔔 Buzzer activates on-site
- 📱 SMS notification sent via GSM
- ☁️ ThingSpeak dashboard flags warning
- 📲 Mobile app notified (via Blynk/IFTTT)

---

## 🔌 System Architecture

```
┌──────────────────────────────────────────────────────┐
│                    SENSOR LAYER                       │
│  [Crack Sensor] [Vibration] [Moisture] [Temperature] │
└─────────────────────────┬────────────────────────────┘
                          │ ADC / GPIO
                          ▼
┌──────────────────────────────────────────────────────┐
│              MICROCONTROLLER LAYER                    │
│         Arduino Uno R3  +  NodeMCU ESP8266           │
│      (Processing)            (Wi-Fi + Cloud)         │
└──────────┬─────────────────────┬────────────────────┘
           │                     │
    ┌──────▼──────┐    ┌─────────▼──────────┐
    │ LCD Display │    │  Communication     │
    │ LED Status  │    │  Wi-Fi / GSM SIM   │
    └─────────────┘    └─────────┬──────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   ThingSpeak Cloud      │
                    │   (Storage + Analytics) │
                    └────────┬────────────────┘
                             │
              ┌──────────────┴──────────────┐
              │                              │
       ┌──────▼──────┐               ┌──────▼──────┐
       │   BUZZER    │               │  SMS / App  │
       │   ALARM     │               │   ALERT     │
       └─────────────┘               └─────────────┘
```

---

## 🔧 Components Used

### Microcontrollers
| Component | Model | Purpose |
|-----------|-------|---------|
| Arduino Uno R3 | ATmega328P | Main processing unit |
| NodeMCU | ESP8266 | Wi-Fi connectivity & cloud upload |

### Sensors
| Sensor | Model | Detects |
|--------|-------|---------|
| Flex / Strain Sensor | 50mm flex strip | Wall crack width & deformation |
| Vibration Sensor | SW-420 module | Structural vibrations & shocks |
| Moisture Sensor | FC-28 with comparator | Water intrusion & dampness |
| Temperature Sensor | DHT11 / LM35 | Thermal expansion stress |

### Communication & Alerts
| Component | Model | Purpose |
|-----------|-------|---------|
| GSM Module | SIM800L + antenna | SMS alerts (fallback comms) |
| Buzzer | 5V Passive Piezo | On-site audio alarm |
| LCD Display | 16x2 with I2C | Local status readout |
| LED Indicators | Red + Green | Visual status signals |

### Cloud Platform
| Platform | Purpose |
|----------|---------|
| ThingSpeak | IoT data storage, visualization & analytics |
| MATLAB (integrated) | Advanced data visualization |
| Blynk / IFTTT | Mobile app notifications |

---

## ✨ What Makes It Unique

| Feature | Why It Matters |
|---------|----------------|
| 🔗 **Multi-Sensor Fusion** | Combines 4 sensor types in one device — no competitor at this price point |
| ☁️ **Real-Time Cloud Sync** | Live data every 5 seconds, accessible globally from any device |
| 💰 **Sub-₹3,000 Cost** | 99.7% cheaper than enterprise SHM systems (₹5–50 Lakhs) |
| 🔧 **Zero-Infra Retrofit** | Adhesive mount — no drilling, rewiring, or civil work needed |
| 🤖 **AI-Ready Architecture** | Threshold logic extensible with ML anomaly detection models |
| 📡 **Dual-Comms Redundancy** | Wi-Fi + GSM fallback ensures alerts reach users even in disasters |

---

## 🌍 Applications

```
🏢 Residential & Commercial    → Apartments, offices, shopping malls
🌉 Bridges & Dams             → Critical infrastructure under dynamic loads  
🏫 Schools & Hospitals        → High-occupancy public safety buildings
🏭 Industrial Structures      → Factories with vibration-generating machinery
🏗️ Construction Sites         → Real-time monitoring during active build phases
🌊 Post-Disaster Assessment   → Quick safety check after earthquakes / floods
```

---

## 💰 Financial Budget

### Bill of Materials

| # | Component | Model | Qty | Unit (₹) | Total (₹) |
|---|-----------|-------|-----|-----------|------------|
| 1 | Arduino Uno R3 | ATmega328P | 1 | 450 | 450 |
| 2 | NodeMCU ESP8266 | 80 MHz Wi-Fi MCU | 1 | 350 | 350 |
| 3 | Flex / Strain Sensor | 50mm strip | 2 | 120 | 240 |
| 4 | Vibration Sensor | SW-420 | 2 | 60 | 120 |
| 5 | Moisture Sensor | FC-28 | 2 | 80 | 160 |
| 6 | Temperature Sensor | DHT11 | 2 | 75 | 150 |
| 7 | GSM Module | SIM800L | 1 | 420 | 420 |
| 8 | Buzzer | 5V Passive | 1 | 30 | 30 |
| 9 | LCD 16x2 + I2C | Blue BL | 1 | 150 | 150 |
| 10 | LED Indicators | R + G pack | 1 | 20 | 20 |
| 11 | Resistors / Caps | Assorted | 1 | 50 | 50 |
| 12 | Breadboard + Wires | 830pt + kit | 1 | 180 | 180 |
| 13 | Power Supply 9V | Adapter + 7805 | 1 | 120 | 120 |
| 14 | PCB / Enclosure | Proto + box | 1 | 250 | 250 |
| 15 | SIM Card + Misc | Data SIM | 1 | 150 | 150 |
| | | | | **TOTAL** | **₹ 2,640** |

> 💡 Prices based on Indian market (2025). May vary ±10% by supplier.

### Cost Comparison
```
Our Prototype       ₹ 2,640       ██ 
Manual Inspection   ₹ 5,000+/visit  ████
Vibrosense SHM      ₹ 5–10 Lakhs    ████████████████████████████████████
SMARTEC SHM         ₹ 20–50 Lakhs   ████████████████████████████████████████████████████████████████████████████

Savings vs Enterprise: 99.7% 🎯
```

---

## 🚀 Quick Start

### Prerequisites
```bash
# Arduino IDE 2.x
# Libraries required:
- DHT sensor library (Adafruit)
- ThingSpeak library
- LiquidCrystal_I2C
- ESP8266WiFi
- TinyGSM (for SIM800L)
```

### Hardware Setup
```
1. Connect sensors to Arduino Uno:
   - Flex Sensor    → A0
   - Vibration      → D2 (interrupt pin)
   - Moisture       → A1
   - DHT11          → D3

2. Connect LCD via I2C:
   - SDA → A4
   - SCL → A5

3. Connect NodeMCU to Arduino via Serial:
   - Arduino TX → NodeMCU RX
   - Arduino RX → NodeMCU TX

4. Connect SIM800L:
   - TX → D7
   - RX → D8
   - Power: 3.7–4.2V (separate supply recommended)
```

### Software Setup

1. **Clone this repository**
```bash
git clone https://github.com/YOUR-USERNAME/smart-wall-monitoring.git
cd smart-wall-monitoring
```

2. **Configure your credentials** in `config.h`:
```cpp
// config.h
#define WIFI_SSID       "Your_WiFi_Name"
#define WIFI_PASSWORD   "Your_WiFi_Password"
#define THINGSPEAK_KEY  "YOUR_THINGSPEAK_API_KEY"
#define ALERT_PHONE     "+91XXXXXXXXXX"

// Safety thresholds (adjust for your wall type)
#define CRACK_THRESHOLD     700    // ADC value (0-1023)
#define VIBRATION_THRESHOLD 300    // ADC value
#define MOISTURE_THRESHOLD  600    // ADC value  
#define TEMP_THRESHOLD      50.0   // Celsius
```

3. **Upload to Arduino**
```
Open src/arduino_main/arduino_main.ino in Arduino IDE
Select board: Arduino Uno
Upload
```

4. **Upload to NodeMCU**
```
Open src/nodemcu_wifi/nodemcu_wifi.ino in Arduino IDE
Select board: NodeMCU 1.0 (ESP-12E Module)
Upload
```

5. **Set up ThingSpeak**
```
1. Create account at thingspeak.com
2. Create new channel with 4 fields:
   - Field 1: Crack Sensor
   - Field 2: Vibration
   - Field 3: Moisture
   - Field 4: Temperature
3. Copy API key to config.h
```

---

## 📁 Code Structure

```
smart-wall-monitoring/
│
├── src/
│   ├── arduino_main/
│   │   └── arduino_main.ino      # Main sensor reading & threshold logic
│   ├── nodemcu_wifi/
│   │   └── nodemcu_wifi.ino      # Wi-Fi + ThingSpeak data upload
│   └── gsm_alerts/
│       └── gsm_alerts.ino        # SMS alert via SIM800L
│
├── config/
│   └── config.h                  # WiFi, API keys, thresholds (rename from config.h.example)
│
├── docs/
│   ├── Smart_Wall_Documentation.pdf
│   ├── circuit_diagram.png
│   └── block_diagram.png
│
├── presentation/
│   └── Smart_Wall_Monitoring_System.pptx
│
├── demo/
│   └── README.md                 # Demo video link + screenshots
│
└── README.md
```

---

## 🗺️ Future Roadmap

```
Phase 1 (NOW)          Phase 2 (6 months)       Phase 3 (1 year)
─────────────          ──────────────────       ────────────────
✅ 4 sensor nodes       🔄 Multi-room mesh        🚀 City-scale deploy
✅ Arduino + NodeMCU    🔄 Custom PCB design       🚀 ML anomaly detect
✅ ThingSpeak cloud     🔄 Native mobile app       🚀 Govt. contracts
✅ SMS + Buzzer         🔄 Cost: ₹15,000/unit      🚀 SaaS subscription
```

**Future Tech Upgrades:**
- 🤖 LSTM neural networks for vibration pattern prediction
- 🏗️ BIM integration for 3D structural visualization
- ☀️ Solar-powered autonomous sensor nodes
- 🚒 Automated emergency dispatch integration
- 🧠 On-device edge AI for reduced cloud latency

---

## 👥 Team

| Role | Name |
|------|------|
| Team Lead & Hardware | [Your Name] |
| Software & Cloud | [Team Member 2] |
| ML / AI Integration | [Team Member 3] |

**Team Name:** Quantumard  
**Institution:** [Your Institution Name]

---

## 📋 Submission

> **⚡ Quantumard National Hackathon 2026 — Phase 2 Build Round**

| Item | Status | Link |
|------|--------|------|
| 🔗 GitHub Repository | ✅ Public | *this repo* |
| 🎥 Demo Video (Drive) | ✅ Public | [View Demo](https://drive.google.com/YOUR-LINK) |
| 🌐 Live Demo | ✅ Active | [Open Demo](https://YOUR-LIVE-DEMO) |
| 📄 PPT (PDF format) | ✅ Uploaded | See `/presentation` folder |
| 🗓️ Deadline | 28 Feb 2026 11:59 PM IST | |

**Submission Portal:** https://forms.gle/jCRqgbpeMVXPgzUT7

---

## 📄 License

This project is developed for the Quantumard National Hackathon 2026.

---

<div align="center">

**Built with ❤️ by Team Quantumard**  
*Detect Early. Alert Instantly. Save Lives.* 🧱🚨

![Made with Arduino](https://img.shields.io/badge/Made%20with-Arduino-00979D?style=flat&logo=arduino)
![IoT](https://img.shields.io/badge/IoT-ThingSpeak-blue?style=flat)
![Cloud](https://img.shields.io/badge/Cloud-Enabled-green?style=flat)

</div>
