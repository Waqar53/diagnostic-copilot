# Diagnostic AI Copilot 🏥

> **AI-powered chest X-ray analysis for diagnostic decision support**

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)](https://pytorch.org)
[![Next.js](https://img.shields.io/badge/Next.js-14-black.svg)](https://nextjs.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

![Diagnostic AI Copilot Demo](docs/demo.png)

## ⚠️ Medical Disclaimer

**This system is for educational and research purposes only.** It is NOT a substitute for professional medical diagnosis or treatment. All AI-generated analyses require review by qualified healthcare professionals.

---

## 🎯 What It Does

Diagnostic AI Copilot analyzes chest X-rays using deep learning and provides:

- **14 Pathology Detection**: Pneumonia, Pneumothorax, Cardiomegaly, Effusion, and more
- **Visual Explainability**: Grad-CAM heatmaps showing exactly where AI focuses
- **Auto-Generated Reports**: Structured radiology report drafts
- **Uncertainty Quantification**: Confidence scores with uncertainty estimates
- **DICOM Support**: Works with medical imaging formats

---

## 🚀 Quick Start

### Prerequisites

- Python 3.11+
- Node.js 18+
- Docker (optional)

### Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the server
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Run development server
npm run dev
```

### With Docker

```bash
# Build and run all services
docker-compose up --build

# Access the app at http://localhost:3000
# API docs at http://localhost:8000/docs
```

---

## 🏗️ Architecture

```
diagnostic-copilot/
├── backend/                 # FastAPI backend
│   ├── app/
│   │   ├── ml/             # ML models (DenseNet121, Grad-CAM)
│   │   ├── routers/        # API endpoints
│   │   ├── schemas/        # Pydantic models
│   │   └── utils/          # Report generation, DICOM
│   └── data/
│       └── models/         # Model weights
│
├── frontend/                # Next.js frontend
│   ├── src/
│   │   ├── app/           # Pages
│   │   ├── components/    # React components
│   │   └── lib/           # API client
│
└── docker-compose.yml       # Container orchestration
```

---

## 🧠 Model Details

### Architecture

- **Base Model**: DenseNet121 pre-trained on ImageNet
- **Fine-tuning**: ChestX-ray14 dataset (112,120 images)
- **Output**: Multi-label classification (14 pathologies)
- **Explainability**: Grad-CAM attention maps

### Detectable Conditions

| Condition | Severity |
|-----------|----------|
| Pneumothorax | 🔴 Severe |
| Mass | 🔴 Severe |
| Pneumonia | 🟡 Moderate |
| Cardiomegaly | 🟡 Moderate |
| Effusion | 🟡 Moderate |
| Edema | 🟡 Moderate |
| Consolidation | 🟡 Moderate |
| Nodule | 🟡 Moderate |
| Atelectasis | 🟢 Mild |
| Infiltration | 🟢 Mild |
| Emphysema | 🟢 Mild |
| Fibrosis | 🟢 Mild |
| Pleural Thickening | 🟢 Mild |
| Hernia | 🟢 Mild |

---

## 📡 API Reference

### Analyze Image

```bash
POST /api/v1/analysis
Content-Type: multipart/form-data

# Parameters
- file: Image file (JPEG, PNG, DICOM)
- patient_age: Optional patient age
- patient_sex: Optional patient sex (M/F)
- clinical_history: Optional clinical notes
- generate_heatmaps: Generate Grad-CAM (default: true)
```

### Get Report

```bash
GET /api/v1/analysis/{analysis_id}/report
```

### Health Check

```bash
GET /health
```

Full API documentation available at `/docs` (Swagger UI).

---

## 🛡️ Safety Features

1. **Medical Disclaimers**: Every output includes clear disclaimers
2. **Uncertainty Quantification**: Monte Carlo Dropout for confidence intervals
3. **Physician Review Required**: Explicit flags for human oversight
4. **Audit Logging**: Track all predictions for compliance
5. **Input Validation**: Check image quality before analysis

---

## 📊 Performance Metrics

| Metric | Value |
|--------|-------|
| Inference Time | ~2-3 seconds (CPU) |
| Model Size | ~30MB |
| Supported Formats | JPEG, PNG, DICOM |

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing`)
5. Open a Pull Request

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgments

- NIH ChestX-ray14 Dataset
- Stanford CheXpert Dataset
- PyTorch and torchvision teams
- FastAPI and Next.js communities

---

**Built with ❤️ for improving healthcare through AI**
# diagnostic-copilot
