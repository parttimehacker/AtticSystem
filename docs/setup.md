## Configuration

### AtticServer Environment Variables

`AtticServer/.env` (optional):

- `DJANGO_SECRET_KEY`
- `DJANGO_DEBUG=1`
- `DATABASE_URL`  
  (Optional; defaults to SQLite if not set)

---

### BLE Worker Configuration

- Sensor manufacturer ID / prefix filtering  
- Duplicate suppression window (to smooth bursty scan results)  
- Poll/scan interval tuning  

---

## Risk Cards (Glanceable UI)

The system converts raw readings into simple risk states:

- **Low**  
  Normal attic conditions  

- **Medium**  
  Watchlist (e.g., dew point spread narrowing, persistent humidity)

- **High**  
  Potential condensation / roof-deck risk  
  (conditions trending toward or exceeding thresholds)

> Thresholds are configurable. See `docs/risk_model.md`.

---

## Deployment (Raspberry Pi)

### Recommended Setup

- Django behind **Apache + mod_wsgi**  
  *(or gunicorn + nginx)*

- BLE worker as a **systemd service**

- SQLite for local-only deployments  
  *(Postgres optional)*

Service units live in:


