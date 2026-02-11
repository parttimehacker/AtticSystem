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
```
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
```

---

## Architecture

See the diagram in [`docs/architecture.md`](docs/architecture.md) (Mermaid).

Key data flow:
1. Sensor advertises BLE payload every N minutes
2. BLE worker scans, parses payload, writes to SQLite/Postgres
3. Django serves Live/History UI with risk cards + summaries
4. Monitor device optionally displays live + history locally via BLE (or future: via Wi-Fi to server)

---

## Getting Started (Local Dev)

### AtticServer (Django + BLE worker)
```bash
cd AtticServer
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```


## Version roadmap (practical, incremental)


---

## Contributing

Pull requests are welcome. Please:

- Keep commits small and descriptive  
- Prefer deterministic parsing of BLE payloads  
- Add tests for payload decoding and risk classification  

---

## License

Choose a license appropriate for your project (MIT is a common default).

