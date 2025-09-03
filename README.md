
# GAAM+ (Guardian AI for Women's Safety & Emotional Monitoring)

This repository is a ready-to-run GAAM+ with:
- **Backend (FastAPI)**: Threat prediction, SOS, evidence upload, hotspot API.
- **ML training pipeline**: Synthetic or real datasets support (plug in later).
- **Dashboard (Streamlit)**: City heatmap & analytics.
- **Mobile (Flutter)** scaffold: Buttons to trigger SOS, evidence, and a live status panel.

- ### 1) Backend
```bash
cd backend
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
# Optional: train a simple model (uses synthetic demo if you don't add real data)
python models/train/train_threat_model.py
uvicorn app:app --reload --port 8000
```
### 2) Dashboard
```bash
cd dashboard
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
streamlit run app.py
```

### 3) Mobile (Flutter)
Install Flutter SDK. Then:
```bash
cd mobile/flutter/gaam_plus
flutter pub get
flutter run
```
## Replace datasets
- Put audio/voice and accelerometer CSVs under `backend/models/train/data/`.
- Update paths in `backend/models/train/config.json` or use CLI args.
- Re-run `train_threat_model.py`. The model saves to `backend/models/threat_model.pkl`.

## Modules overview
- `backend/app.py`: REST API (predict, sos, evidence, hotspots).
- `backend/models/train/*`: Training pipeline (feature engineering + classifier).
- `dashboard/app.py`: Streamlit heatmap from `data/alerts.csv`.
- `mobile/flutter/gaam_plus`: Minimal UI (SOS, record, status).

## License
MIT (for this scaffold). Respect licenses of any external datasets you add.
