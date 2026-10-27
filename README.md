# DeepFake Face Detector

A lightweight CNN-based web app that classifies a face image as **Real** or **DeepFake**, built with TensorFlow/Keras and Streamlit.

![Home screen](assets/hero.jpg)

## Features
- Lightweight CNN trained to spot manipulation artifacts in face images
- Upload a JPG/PNG and get a Real/Fake verdict with confidence gauge and probability chart
- Secure user authentication with **bcrypt** password hashing and session management
- Role-based Admin panel with protected user management and XSS defense
- Model weights downloaded automatically and cached with `@st.cache_resource` for high performance

## Tech Stack
Python · TensorFlow/Keras · OpenCV · Streamlit · Plotly · SQLite · Bcrypt

## Getting Started

### 1. Clone & Setup Environment
```bash
git clone https://github.com/gedsvd/deepfake-face-detector.git
cd deepfake-face-detector
python -m venv .venv
source .venv/bin/activate       # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### 2. Configure Environment Variables
Copy `.env.example` to `.env` and configure your credentials:
```bash
cp .env.example .env
```
Inside `.env`:
```ini
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=your_strong_admin_password
```

### 3. Run the App
```bash
streamlit run app.py
```
Open [http://localhost:8501](http://localhost:8501). The trained model (`Deep_model.keras`) is fetched automatically on the first prediction.

## Project Structure
```
├── app.py              # Main Streamlit application (UI, auth, inference)
├── assets/             # Media assets (hero.jpg)
├── .env.example        # Template for admin credentials and environment settings
├── .gitignore          # Git exclusion rules (users.db, .env, models)
├── requirements.txt    # Python dependencies
├── LICENSE             # MIT License
└── README.md           # Documentation
```

## Security Best Practices
- **Password Hashing:** Stored user passwords are encrypted using `bcrypt` salted hashes.
- **Admin Authentication:** No credentials hardcoded; loaded via `st.secrets` or `.env`.
- **XSS Sanitization:** All user inputs rendered in HTML are sanitized with `html.escape()`.
- **Database Safety:** Safe context-managed SQLite queries preventing connection leaks.
- **Ignored Artifacts:** Local databases (`users.db`) and secret files (`.env`) are excluded from git.

## GitHub Repository Setup
- **Repository Name:** `deepfake-face-detector`
- **Description:** Lightweight CNN-powered DeepFake Face Classification web application built with TensorFlow/Keras and Streamlit.
- **Topics:** `deepfake-detection`, `cnn`, `streamlit`, `tensorflow`, `computer-vision`

## Limitations
Results are probabilistic and may not generalise to manipulation methods absent from training data. Not intended as sole forensic evidence.

## License
MIT - see [LICENSE](LICENSE).
