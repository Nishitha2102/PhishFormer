# 🎣 PhishFormer - Intelligent Phishing Detection System

> An advanced deep learning-based phishing detection system combining URL analysis and HTML feature extraction using an attention-based deep fusion model.

[![Frontend Status](https://img.shields.io/badge/Frontend-Live%20on%20Netlify-success?style=flat-square)](https://phish66.netlify.app)
[![Backend Status](https://img.shields.io/badge/Backend-Flask%20API-blue?style=flat-square)](https://flask.palletsprojects.com/)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

---

## 🌟 Overview

**PhishFormer** is a sophisticated phishing detection system that leverages machine learning to identify malicious URLs with high accuracy. It combines:

- **URL Feature Analysis**: Extracts 20+ suspicious patterns from URL structure
- **HTML Content Analysis**: Detects 30+ phishing indicators from page HTML
- **Deep Fusion Model**: Uses attention mechanisms to combine both feature sets
- **Real-time Detection**: Instant predictions with confidence scores
- **User-Friendly Interface**: Modern web UI for easy URL scanning

### Key Statistics
- **Accuracy**: >95%
- **Model Type**: Attention-Based Deep Fusion Neural Network
- **Language Composition**: TypeScript (83.9%), Python (13%), CSS (3%), JavaScript (0.1%)
- **Supported Features**: 50+ detection indicators
- **Response Time**: <500ms per prediction

---

## 🚀 Features

### 🔍 **URL Scanner**
- Real-time phishing detection
- Detailed risk assessment (Critical, High, Moderate, Safe)
- Feature breakdown showing suspicious indicators
- Security recommendations

### 🧠 **Intelligent Detection**
- **20+ URL Features**
  - IP address detection
  - Domain anomalies
  - Suspicious TLDs
  - Shortening services
  - Phishing keywords
  - And more...

- **30+ HTML Features**
  - Login form detection
  - External resource analysis
  - JavaScript behavior detection
  - Redirect patterns
  - Brand impersonation indicators
  - And more...

### 📊 **Model Metrics Dashboard**
- View model performance statistics
- Accuracy, Precision, Recall, F1-Score
- ROC-AUC metrics

### 💾 **Model Management**
- Download trained model files
- Get all model artifacts in ZIP format
- Model versioning support

---

## 🏗️ Architecture

### Technology Stack

#### **Backend (Python)**
- **Framework**: Flask + Flask-CORS
- **ML/DL**: TensorFlow, Keras
- **Data Processing**: NumPy, scikit-learn
- **Web Scraping**: BeautifulSoup
- **URL Parsing**: tldextract

#### **Frontend (TypeScript/React)**
- **Framework**: Next.js 14
- **UI Components**: Radix UI
- **Styling**: Tailwind CSS
- **Forms**: React Hook Form
- **Charts**: Recharts
- **HTTP Client**: SWR

#### **Deployment**
- **Frontend**: Netlify
- **Backend**: Railway (or self-hosted)
- **Database**: MongoDB (optional)

### System Architecture

```
┌─────────────────────────────────────────────┐
│         User Web Interface (Netlify)        │
│      TypeScript/React/Next.js Frontend      │
└──────────────────────────────────────────────┘
                      ↓ HTTP/REST API
┌──────────────────────────────────────────────┐
│      Flask API Server (Railway/Local)       │
│  • CORS-enabled for Netlify                  │
│  • Feature extraction endpoints              │
│  • Model prediction service                  │
└──────────────────────────────────────────────┘
                      ↓
┌──────────────────────────────────────────────┐
│     ML/DL Models (TensorFlow/Keras)         │
│  • Attention-Based Deep Fusion Model        │
│  • URL Feature Scalers                       │
│  • HTML Feature Scalers                      │
│  • Metrics & Configurations                  │
└──────────────────────────────────────────────┘
```

---

## 📋 Getting Started

### Prerequisites
- **Python 3.11+** (for backend)
- **Node.js 18+** (for frontend)
- **pip & npm** package managers

### Backend Setup

#### 1. Clone Repository
```bash
git clone https://github.com/Nishitha2102/PhishFormer.git
cd PhishFormer
```

#### 2. Create Python Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

#### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

#### 4. Verify Model Files
Ensure the following files exist in `saved_models/` directory:
```
saved_models/
├── phishing_model.keras  (or .h5 format)
├── scaler_url.pkl
├── scaler_html.pkl
├── feature_config.pkl
└── metrics.pkl
```

#### 5. Start Backend Server
```bash
python app.py
```

The server will start on `http://localhost:5000`

**Expected Output:**
```
================================================================================
🚀 PHISHING DETECTION API SERVER
================================================================================

Server starting on http://localhost:5000

API Endpoints:
  • GET  /                    - API info
  • GET  /health              - Health check
  • GET  /metrics             - Model metrics
  • POST /predict             - Predict URL
  • GET  /api/download-model  - Download model
  • GET  /api/download-all    - Download all files (ZIP)

================================================================================

✅ Ready to accept requests from React frontend!
================================================================================
```

### Frontend Setup

#### 1. Install Dependencies
```bash
npm install
# or
pnpm install
# or
yarn install
```

#### 2. Configuration
Update the API URL in your environment or code:

**Option A: Environment Variable (Recommended)**
```bash
echo "NEXT_PUBLIC_API_URL=http://localhost:5000" > .env.local
```

**Option B: Direct Code Update**
- File: `components/detection/url-scanner.tsx`
- Find the API URL and update as needed

#### 3. Start Development Server
```bash
npm run dev
```

Frontend runs on `http://localhost:3000`

#### 4. Build for Production
```bash
npm run build
npm start
```

---

## 🔌 API Documentation

### Base URL
- **Local Development**: `http://localhost:5000`
- **Production**: See [Deployment Guide](./README_DEPLOYMENT.md)

### Endpoints

#### 1. **GET /** - API Information
```bash
curl http://localhost:5000/
```

**Response:**
```json
{
  "status": "online",
  "message": "Phishing Detection API is running",
  "model": "Attention-Based Deep Fusion Model",
  "model_loaded": true,
  "version": "1.0.3",
  "endpoints": {
    "/predict": "POST - Predict if URL is phishing",
    "/health": "GET - Check API health",
    "/metrics": "GET - Get model performance metrics",
    "/api/download-model": "GET - Download model file",
    "/api/download-all": "GET - Download all model files as ZIP"
  }
}
```

#### 2. **GET /health** - Health Check
```bash
curl http://localhost:5000/health
```

**Response:**
```json
{
  "status": "healthy",
  "model_loaded": true,
  "url_features": 20,
  "html_features": 30,
  "timestamp": "2026-05-09T10:30:45.123456"
}
```

#### 3. **GET /metrics** - Model Performance
```bash
curl http://localhost:5000/metrics
```

**Response:**
```json
{
  "model": "Attention-Based Deep Fusion Model",
  "metrics": {
    "accuracy": 95.42,
    "precision": 94.87,
    "recall": 96.12,
    "f1_score": 95.49,
    "roc_auc": 98.67
  }
}
```

#### 4. **POST /predict** - Predict URL
```bash
curl -X POST http://localhost:5000/predict \
  -H "Content-Type: application/json" \
  -d '{
    "url": "https://suspicious-login-bank.tk",
    "fetch_html": true
  }'
```

**Request Body:**
```json
{
  "url": "https://example.com",
  "fetch_html": true  // Optional: fetch and analyze HTML (default: false)
}
```

**Response (Phishing):**
```json
{
  "url": "https://suspicious-login-bank.tk",
  "prediction": "Phishing",
  "confidence": 0.9234,
  "confidence_percentage": 92.34,
  "phishing_score": 92.34,
  "legitimate_score": 7.66,
  "risk_level": "🔴 CRITICAL",
  "risk_color": "red",
  "is_phishing": true,
  "html_analysis": "fetched",
  "features": {
    "url_features": {
      "length_url": 30,
      "length_hostname": 24,
      "ip": 0,
      "nb_dots": 3,
      "nb_hyphens": 2,
      "shortening_service": 0,
      "suspecious_tld": 1,
      "phish_hints": 1
    },
    "total_url_features": 20,
    "total_html_features": 30,
    "suspicious_html_features": ["login_form", "external_favicon"]
  },
  "recommendations": [
    "⚠️ DO NOT enter any personal information on this website",
    "❌ DO NOT click on any links or download files",
    "📢 Report this URL to your IT security team",
    "🚪 Close the webpage immediately and clear your browser cache"
  ],
  "timestamp": "2026-05-09T10:35:12.456789"
}
```

**Response (Legitimate):**
```json
{
  "url": "https://github.com",
  "prediction": "Legitimate",
  "confidence": 0.0523,
  "confidence_percentage": 5.23,
  "phishing_score": 5.23,
  "legitimate_score": 94.77,
  "risk_level": "🟢 SAFE",
  "risk_color": "green",
  "is_phishing": false,
  "html_analysis": "fetched",
  "features": { /* ... */ },
  "recommendations": [
    "✅ URL appears to be legitimate based on our analysis",
    "🔒 Always verify HTTPS and valid SSL certificates",
    "👀 Double-check the domain spelling before entering sensitive data",
    "⚡ Stay cautious of suspicious redirects or pop-ups"
  ],
  "timestamp": "2026-05-09T10:35:12.456789"
}
```

#### 5. **GET /api/download-model** - Download Model
```bash
curl -O http://localhost:5000/api/download-model
```

Downloads the trained model file (`.keras` or `.h5`)

#### 6. **GET /api/download-all** - Download All Files
```bash
curl -O http://localhost:5000/api/download-all
```

Downloads ZIP containing:
- Model file
- URL feature scaler
- HTML feature scaler
- Feature configuration
- Metrics JSON

---

## 🧬 Feature Extraction

### URL Features (20 total)
1. URL length
2. Hostname length
3. IP address detection
4. Number of dots
5. Number of hyphens
6. Number of @ symbols
7. Number of slashes
8. WWW presence
9. .com presence
10. Digit ratio
11. Punycode detection
12. Prefix-suffix hyphens
13. Shortening service detection
14. TLD in subdomain
15. Abnormal subdomain
16. Number of subdomains
17. Suspicious TLD detection
18. Phishing keyword hints
19. Random domain detection
20. Double slash detection

### HTML Features (30 total)
1. HTTP in path
2. HTTPS in path/query
3. Number of hyperlinks
4. Internal hyperlink ratio
5. External hyperlink ratio
6. Null hyperlink ratio
7. External CSS count
8. Internal redirection ratio
9. External redirection ratio
10. Login form detection
11. External favicon
12. Links in tags
13. Email submission form
14. Server Form Handler (SFH)
15. iFrame detection
16. Popup window detection
17. Safe anchor (href="#")
18. Onmouseover event
19. Right-click disable
20. Empty page title
21. Domain in title
22. Domain with copyright
23. Brand in subdomain
24. Brand in path
25. Domain in brand
26. And more...

---

## 🎯 Model Details

### Architecture
- **Type**: Attention-Based Deep Fusion Neural Network
- **Input**: Concatenated URL + HTML features
- **Hidden Layers**: Multiple dense layers with attention mechanisms
- **Output**: Binary classification (Phishing probability: 0-1)
- **Activation**: ReLU (hidden), Sigmoid (output)

### Training
- **Dataset**: Phishing URL dataset with balanced classes
- **Preprocessing**: Feature scaling (StandardScaler)
- **Validation**: Cross-validation with test set
- **Optimization**: Adam optimizer with categorical crossentropy

### Performance
- **Accuracy**: 95.42%
- **Precision**: 94.87%
- **Recall**: 96.12%
- **F1-Score**: 95.49%
- **ROC-AUC**: 98.67%

---

## 📚 Project Structure

```
PhishFormer/
├── 📄 README.md                      # Main documentation (this file)
├── 📄 README_DEPLOYMENT.md           # Deployment guide
├── 📄 app.py                         # Flask backend server
├── 📄 package.json                   # Frontend dependencies
├── 📄 tsconfig.json                  # TypeScript configuration
├── 📄 next.config.mjs                # Next.js configuration
├── 📄 tailwind.config.ts             # Tailwind CSS config
├── 📄 components.json                # Radix UI components config
│
├── 📁 app/                           # Next.js app directory
│   ├── layout.tsx                    # Root layout
│   ├── page.tsx                      # Home page
│   └── api/                          # API routes (if needed)
│
├── 📁 components/                    # React components
│   ├── detection/
│   │   └── url-scanner.tsx          # Main URL scanner component
│   ├── ui/                          # Reusable UI components
│   └── ...
│
├── 📁 lib/                           # Utility functions
├── 📁 styles/                        # Global styles
├── 📁 public/                        # Static assets
├── 📁 hooks/                         # Custom React hooks
│
├── 📁 saved_models/                  # ML model files
│   ├── phishing_model.keras         # Trained Keras model
│   ├── scaler_url.pkl               # URL features scaler
│   ├── scaler_html.pkl              # HTML features scaler
│   ├── feature_config.pkl           # Feature configuration
│   └── metrics.pkl                  # Model metrics
│
├── 📁 api/                           # API utilities
└── 📄 Procfile                       # Railway deployment config
```

---

## 🚀 Deployment

### Quick Start - Netlify + Railway

**Frontend (Netlify):**
- Status: ✅ Live at https://phish66.netlify.app
- Auto-deployed from GitHub main branch

**Backend (Railway):**
1. Push code to GitHub
2. Connect repository to Railway
3. Railway auto-deploys from `Procfile`
4. Get your Railway domain
5. Update frontend environment variables

See [Deployment Guide](./README_DEPLOYMENT.md) for detailed instructions.

### Environment Variables

**Backend (.env):**
```
FLASK_ENV=production
PORT=5000
ALLOWED_ORIGINS=https://phish66.netlify.app,http://localhost:3000
```

**Frontend (.env.local):**
```
NEXT_PUBLIC_API_URL=https://your-railway-backend.up.railway.app
```

---

## 🧪 Testing

### Backend API Testing

Using `curl`:
```bash
# Health check
curl http://localhost:5000/health

# Test legitimate URL
curl -X POST http://localhost:5000/predict \
  -H "Content-Type: application/json" \
  -d '{"url": "https://github.com", "fetch_html": false}'

# Test suspicious URL
curl -X POST http://localhost:5000/predict \
  -H "Content-Type: application/json" \
  -d '{"url": "https://suspicious-login-bank.tk", "fetch_html": false}'
```

### Frontend Testing
1. Open http://localhost:3000
2. Enter various URLs in the scanner
3. Check predictions and feature breakdowns
4. Verify error handling and UI responsiveness

---

## 🔒 Security Considerations

- ✅ **CORS Protection**: Configured for specific domains
- ✅ **HTTPS Only**: Required for production
- ✅ **Input Validation**: All URLs validated before processing
- ✅ **Rate Limiting**: Consider implementing for production
- ✅ **SSL/TLS**: Enforced on all deployments

### Best Practices
- Never share API keys or credentials
- Always use HTTPS in production
- Regularly update dependencies
- Monitor model performance
- Implement request logging and monitoring

---

## 📊 Performance Optimization

- **Caching**: Model predictions can be cached
- **Async Processing**: Backend handles parallel requests
- **Lazy Loading**: Frontend components load on demand
- **Image Optimization**: Handled by Next.js
- **Database Indexing**: If adding persistence layer

---

## 🐛 Troubleshooting

### Backend Issues

**Model Not Loading**
```
Error: FileNotFoundError: No model file found!
Solution: Ensure saved_models/ directory contains phishing_model.keras
```

**CORS Errors**
```
Error: Access to XMLHttpRequest blocked by CORS policy
Solution: Update ALLOWED_ORIGINS in app.py with your frontend domain
```

**Port Already in Use**
```
Error: Address already in use
Solution: Kill existing process or use different port
python app.py --port 5001
```

### Frontend Issues

**API Connection Error**
```
Error: Failed to fetch from API
Solution: Verify API_URL is correct and backend is running
```

**Build Errors**
```
Solution: Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

---

## 📈 Future Enhancements

- [ ] Batch URL processing
- [ ] Phishing URL database integration
- [ ] Real-time threat intelligence feeds
- [ ] Mobile app (React Native)
- [ ] Browser extension
- [ ] Email scanning integration
- [ ] Advanced analytics dashboard
- [ ] Multi-language support
- [ ] User authentication system
- [ ] Scan history and reporting

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📞 Support & Contact

- **GitHub Issues**: [Report bugs or request features](https://github.com/Nishitha2102/PhishFormer/issues)
- **Email**: [Your contact email]
- **Live Demo**: https://phish66.netlify.app

---

## 📚 Additional Resources

- [Flask Documentation](https://flask.palletsprojects.com/)
- [TensorFlow/Keras Guide](https://www.tensorflow.org/guide)
- [Next.js Documentation](https://nextjs.org/docs)
- [Railway Deployment Docs](https://docs.railway.app/)
- [Netlify Deployment Guide](https://docs.netlify.com/)

---

## 🎓 Research & References

This project implements research on:
- Deep learning for phishing detection
- Feature engineering for URL analysis
- HTML content analysis for security
- Attention mechanisms in neural networks
- Multi-input fusion models

---

<div align="center">

**Made with ❤️ by Nishitha2102**

⭐ If you found this project helpful, please give it a star!

[Live Demo](https://phish66.netlify.app) • [GitHub](https://github.com/Nishitha2102/PhishFormer) • [Report Issue](https://github.com/Nishitha2102/PhishFormer/issues)

</div>
