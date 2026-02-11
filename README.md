# AtticSystem (AtticMonitor + AtticSensor + AtticServer)

Battery-friendly attic/roof monitoring system for wood-frame homes:
- **AtticSensor**: low-power sensor node(s) broadcasting BLE manufacturer payloads (temp, humidity, pressure, battery, motion)
- **AtticMonitor**: M5Stack Core2 (ESP32) display + touch UI showing live status, risk cards, history, and settings
- **AtticServer**: Django app + BLE ingestion worker for logging, dashboards, and historical views

> Goals: **reliable**, **low-maintenance**, **battery-aware**, and **glanceable** for a small household.

---

## Highlights

- **BLE broadcast ingestion** (no pairing required)
- **Dew point** computation + condensation risk presentation
- **Motion detection** as a “significant event”
- **Battery percent** mapping + icon display
- **Local-first** operation option (Pi host), with internet optional

---

## Repository Layout
AtticSystem/
├── AtticSensor/ # Embedded sensor firmware (Feather / Nano / etc)
├── AtticMonitor/ # M5Stack Core2 (ESP32) display firmware
├── AtticServer/ # Django web app + ingestion worker
│ ├── atticguard/ # Django project/app modules
│ ├── ble_worker/ # BLE scan + parse + write DB
│ ├── systemd/ # Service units for Pi deployments
│ └── requirements.txt
├── docs/ # Diagrams, screenshots, design notes
└── .github/workflows/ # CI workflows

