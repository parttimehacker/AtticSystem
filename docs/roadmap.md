
## 3) Version roadmap (practical, incremental)

# AtticSystem Roadmap

## v0.1 (Foundation) ✅
- Sensor BLE payload stable (temp, humidity, pressure, batt, motion, seq)
- BLE worker reliably decodes payload + writes DB
- Django Live view renders latest reading
- Basic systemd service for ble_worker

## v0.2 (Reliability + Debuggability)
- Deduplicate bursty BLE readings (sequence + timestamp window)
- Structured logging (levels + rotating file) for ble_worker
- Health endpoints / status card: “last seen”, “missing data” detection
- Management command to backfill/repair missing computed fields (dew point)

## v0.3 (Risk Model + Glanceable UI)
- Dew point + “roof deck condensation risk” model
- Live view “Risk Card” + “Motion Card”
- Trend indicators (last 1h / 24h change)
- Export CSV button for readings

## v0.4 (History + Charts)
- History page with selectable time ranges (24h / 7d / 30d)
- Simple charts (temp/hum/dewpoint/battery)
- Outlier handling (sensor reboot, partial payloads)

## v0.5 (Deployment Hardening)
- Apache/mod_wsgi + static file pipeline documented
- Install script or Ansible playbook for Pi setup
- DB migration + retention policy (e.g., keep 1y, summarize older)

## v1.0 (Release)
- Documented hardware builds + wiring
- Stable risk thresholds with config
- “First-run experience” checklist
- Tagged release + changelog

## v1.1+ (Future)
- Multi-sensor support (sensor_id + location name)
- Notifications (email/push optional)
- Wi-Fi settings + remote view on LAN
