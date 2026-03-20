# ✈️ AeroScan — Aerial Aircraft Detection & Classification

![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat-square)
![YOLO](https://img.shields.io/badge/YOLO-v26-purple?style=flat-square)
![Streamlit](https://img.shields.io/badge/UI-Streamlit-red?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

An end-to-end computer vision pipeline that detects and classifies aircraft in aerial and satellite imagery. Built with YOLO26 for detection and EfficientNet-B0 for fine-grained aircraft type classification.

---

## 🎯 What It Does

Upload any aerial or satellite image of an airport and AeroScan will:
- Detect all aircraft in the image using YOLO26
- Classify each aircraft by type (Boeing 737, Airbus A320, Fighter Jet, etc.)
- Draw bounding boxes with labels and confidence scores
- Display a live detection log with coordinates

---

## 🖥️ Demo

| Input | Output |
|---|---|
| Satellite image of airport | Annotated image with bounding boxes + aircraft type labels |

> **Tip:** Screenshot Google Maps in satellite mode over JFK, Heathrow, or Mumbai Airport for best results.

---

## 🗂️ Project Structure

```
aircraft-detector/
├── train.py              # Train YOLO26 detector
├── classify.py           # EfficientNet classifier
├── pipeline.py           # Chain detector + classifier
├── streamlit_app.py      # Web UI
├── requirements.txt      # Dependencies
└── data/
    ├── data.yaml         # Dataset config
    ├── train/
    │   ├── images/
    │   └── labels/
    ├── valid/
    │   ├── images/
    │   └── labels/
    └── test/
        ├── images/
        └── labels/
```

---

## ⚙️ Installation

### Prerequisites
- Python 3.11+
- Windows / Linux / macOS

### Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/aircraft-detector.git
cd aircraft-detector

# Install dependencies
pip install -r requirements.txt
```

### requirements.txt

```
ultralytics
streamlit
torchvision
timm
pillow
gradio
```

---

## 📦 Dataset

This project uses the **Aerial Airport dataset** from Roboflow.

1. Go to [roboflow.com/roboflow-100/aerial-airport](https://roboflow.com/roboflow-100/aerial-airport)
2. Download in **YOLOv8 format**
3. Extract into the `data/` folder

---

## 🚀 Usage

### Step 1 — Train the detector

```bash
python train.py
```

> Trains YOLO26n on the aerial airport dataset. Expected time: 2–4 hours on CPU, ~30 mins on GPU. Model saved to `runs/detect/aircraft_cpu/weights/best.pt`.

### Step 2 — Launch the web app

```bash
python -m streamlit run streamlit_app.py
```

Opens at `http://localhost:8501` in your browser.

### Optional — Run inference from command line

```bash
python pipeline.py test.jpg
# Saves annotated output to output.jpg
```

---

## 🧠 Model Details

| Component | Model | Purpose |
|---|---|---|
| Detector | YOLO26n | Locate aircraft in aerial images |
| Classifier | EfficientNet-B0 | Identify aircraft type from cropped detections |
| Dataset | Aerial Airport (Roboflow) | Training data for detector |
| Classification labels | FGVC-Aircraft families | 10 aircraft type categories |

### Aircraft types supported

- Boeing 737 / 747 / 777
- Airbus A320 / A380
- Cessna
- Fighter Jet
- Cargo Plane
- Helicopter
- Unknown

---

## 📊 Performance

| Metric | Value |
|---|---|
| Detection mAP@50 | ~0.85+ (after 20 epochs) |
| Single image inference (CPU) | 3–8 seconds |
| Single image inference (GPU) | < 1 second |
| App startup time | ~10 seconds |

---

## 🌍 Real-World Applications

- **Defense & Intelligence** — Monitor airbases via satellite, detect fleet movements
- **Airport Operations** — Automate ground traffic monitoring and gate occupancy
- **Aviation Security** — Detect unauthorized aircraft at restricted airfields
- **Flight Research** — Study air traffic density over radar-less regions
- **Damage Assessment** — Rapidly assess aircraft damage after disasters
- **Fleet Management** — Track airline fleets across multiple airports

---

## 🖥️ Hardware Requirements

| Setup | Recommended |
|---|---|
| Minimum | 8GB RAM, any modern CPU |
| Training (CPU) | 8GB+ RAM, expect 2–4 hour training time |
| Training (GPU) | NVIDIA GPU with 4GB+ VRAM (CUDA) |
| Inference | Works on any laptop CPU |

---

## ☁️ Deploy to Streamlit Cloud (Free)

1. Push this repo to GitHub
2. Go to [share.streamlit.io](https://share.streamlit.io)
3. Sign in with GitHub → **New app**
4. Select your repo, set main file to `streamlit_app.py`
5. Click **Deploy**

You'll get a free public URL to share in your portfolio.

---

## 🛠️ Troubleshooting

| Error | Fix |
|---|---|
| `yolo26n.pt not found` | Run `pip install --upgrade ultralytics` |
| `No module named 'gradio'` | Run `pip install gradio` |
| `data.yaml not found` | Ensure dataset is extracted inside `data/` |
| No detections on image | Use a clearer aerial image — try a Google Maps airport screenshot |
| Still on Python 3.8 | Run `py -3.11 -m streamlit run streamlit_app.py` explicitly |

---

## 📁 Tech Stack

- [Ultralytics YOLO26](https://github.com/ultralytics/ultralytics) — Object detection
- [PyTorch + EfficientNet](https://pytorch.org/) — Image classification
- [Streamlit](https://streamlit.io/) — Web interface
- [Pillow](https://pillow.readthedocs.io/) — Image processing

---

## 👤 Author

Built as a portfolio project for aerospace ML internship applications.

---

## 📄 License

MIT License — free to use, modify, and distribute.
