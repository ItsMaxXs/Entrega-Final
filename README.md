# HEMS · Heat stress monitoring dashboard

A Streamlit web app that evaluates heat stress for workers, using live temperature and humidity readings from IoT sensors published to a ThingSpeak channel. Built as a team project at Delta Lab, Costa Rica Institute of Technology (TEC), 2025.

## What it does

- **Task evaluation:** the user describes the job (metabolic rate, clothing insulation, exposure) and the app computes standard thermal comfort and heat stress indices:
  - Heat index with recommended prevention measures by risk level
  - Fanger's PMV and PPD (thermal comfort)
  - WBGT (wet bulb globe temperature) with acclimatized and non acclimatized limit curves
  - Required sweat rate and heat strain index, with the maximum safe exposure time
- **Live monitoring:** reads the latest sensor feed from the ThingSpeak REST API and shows current values and history charts.
- **Simple user accounts** to keep each evaluation separate.

## Tech

Python, Streamlit, pandas, NumPy, Altair, Matplotlib, ThingSpeak REST API.

## Project structure

| File | Purpose |
|---|---|
| `app.py` | Streamlit interface, login and both tabs |
| `funcionesfang.py` | Heat stress and thermal comfort calculations |
| `decodification_ThingSpeak.py` | Reads and decodes the sensor feed |
| `data_input2.py` | Data entry helpers |
| `data/` | Reference tables (metabolism, clothing insulation, correction factors) |

## Run it locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

The app creates `users.json` on first run when someone registers.

## Notes

This was an academic prototype. For a production version I would move the ThingSpeak key to an environment variable and replace the simple SHA-256 password hashing with a salted algorithm such as bcrypt.
