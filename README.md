# 🧠 Emotion AI

> A full-stack multimodal system that detects human emotions from facial expressions, voice signals, and text — and responds with context-aware, emotionally intelligent conversations.

-----

## 🌟 What It Does

Emotion AI combines three independent emotion detection pipelines into a unified system:

|Modality|Method                               |Output                                |
|--------|-------------------------------------|--------------------------------------|
|👁️ Face  |OpenCV + CNN                         |Emotion label from live/uploaded image|
|🎙️ Voice |Speech feature extraction            |Emotion from audio input              |
|💬 Text  |HuggingFace Transformers (DistilBERT)|Sentiment + emotion from typed input  |

All three feed into a **conversational response layer** that adapts its tone and suggestions based on the detected emotional state.

-----

## 🚀 Getting Started

### Prerequisites

- Python 3.11+
- Node.js 18+

### Backend Setup

```bash
cd backend
python -m venv .venv-py311
source .venv-py311/bin/activate      # Windows: .venv-py311\Scripts\activate
pip install -r requirements.txt
python main.py
```

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

The app will be running at `http://localhost:3000`

### Training (Optional)

To retrain models from scratch:

```bash
cd training
python generate_dataset.py       # Prepare data
python finetune_emotion.py       # Fine-tune text model (DistilBERT)
python train_face.py             # Train facial emotion model
python train_voice.py            # Train voice emotion model
```

> ⚠️ Model weights (`.pt`, `.safetensors`) are not committed to this repo due to file size. Run the training scripts to generate them locally, or download pre-trained checkpoints (see below).

-----

## 🏗️ Architecture

```
emotion-ai/
├── backend/
│   ├── main.py               # Flask app entry point
│   ├── auth.py               # JWT authentication
│   ├── predict_text.py       # Text emotion inference
│   ├── face_model_loader.py  # Facial model loader
│   └── utils/                # Shared utilities
│
├── frontend/
│   └── src/
│       ├── components/       # Reusable UI components
│       ├── pages/            # App pages (Home, Dashboard, Chat)
│       ├── context/          # React context (auth, emotion state)
│       └── styles/           # CSS modules
│
└── training/
    ├── data/                 # Training datasets (CSV)
    ├── generate_dataset.py
    ├── finetune_emotion.py   # HuggingFace fine-tuning
    ├── train_face.py
    └── train_voice.py
```

-----

## 🛠️ Tech Stack

**Frontend:** React, JavaScript, CSS Modules

**Backend:** Python, Flask, JWT Auth

**ML/AI:**

- `transformers` (HuggingFace) — DistilBERT for text emotion
- `OpenCV` + CNN — facial expression recognition
- `librosa` / `speechbrain` — voice feature extraction
- `PyTorch` / `TensorFlow` — model training

-----

Key Features

- **Multimodal fusion** — combines face, voice, and text signals
- **Emotion-aware chat** — responses adapt based on detected emotional state
- **User authentication** — JWT-based login and session management
- **Emotion history tracking** — stores and visualizes past emotion data per user
- **Modular training pipelines** — each modality can be retrained independently

Notes

- This project is intended for **exploratory and supportive use cases**, not clinical diagnosis.
- Model artifacts are generated locally and excluded from version control via `.gitignore`.
- The system is designed to be **privacy-conscious** — no audio or video is stored by default.

Author

**Madhulika Sri** — [github.com/madhulikasri0317](https://github.com/madhulikasri0317)
