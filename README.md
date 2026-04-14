# Phishing Website Detector

A machine learning-powered web application that detects phishing websites by analyzing URL characteristics and features. This project combines scikit-learn's classification models with a Django web interface to provide an accessible tool for identifying potentially malicious URLs.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Technology Stack](#technology-stack)
- [Installation](#installation)
- [Usage](#usage)
- [Machine Learning Model](#machine-learning-model)
- [Dataset](#dataset)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

Phishing attacks remain one of the most prevalent cybersecurity threats. This project leverages machine learning to automatically classify URLs as either legitimate or phishing-related based on a comprehensive set of URL characteristics. The model is trained on a labeled dataset of URLs and integrated into a user-friendly Django web application.

### Key Capabilities
- **Binary Classification**: Classifies URLs as phishing or legitimate
- **Feature-Based Analysis**: Analyzes 11 distinct URL characteristics
- **Web Interface**: Easy-to-use form for URL analysis
- **Production-Ready**: Deployable to platforms like Heroku

## ✨ Features

- **ML Model**: Scikit-learn based classifier trained on URL features
- **Web Interface**: Django-powered user interface for real-time predictions
- **Feature Extraction**: Analyzes multiple URL characteristics including:
  - Number of dots and dashes
  - URL length and path depth
  - Presence of sensitive words
  - External hyperlinks and resources
  - Form security indicators
  - Domain mismatch frequency
  - HTTPS security implementation
  - Iframe/Frame usage
  
- **Model Persistence**: Pre-trained model saved for quick inference
- **Responsive Design**: Web interface accessible from any browser

## 📁 Project Structure

```
Phishing_Project/
├── ML Project - Phishing/
│   ├── Phishing.csv                 # Dataset with URL features and labels
│   ├── Phishing.ipynb               # Jupyter notebook with ML model development
│   └── mysite/                      # Django web application
│       ├── manage.py                # Django management script
│       ├── requirements.txt         # Python dependencies
│       ├── Procfile                 # Heroku deployment configuration
│       ├── runtime.txt              # Python runtime specification
│       ├── db.sqlite3               # SQLite database
│       ├── mysite/                  # Django project settings
│       │   ├── __init__.py
│       │   ├── settings.py          # Django configuration
│       │   ├── urls.py              # URL routing
│       │   ├── asgi.py              # ASGI configuration
│       │   └── wsgi.py              # WSGI configuration
│       └── polls/                   # Django application
│           ├── models.py
│           ├── views.py             # View handlers for predictions
│           ├── urls.py
│           ├── admin.py
│           ├── apps.py
│           ├── tests.py
│           ├── Phishing.pickle      # Serialized ML model
│           ├── migrations/          # Database migrations
│           └── templates/
│               └── index.html       # Web interface template
```

## 🛠 Technology Stack

### Machine Learning & Data Processing
- **scikit-learn** (0.24.2) - Classification algorithms
- **pandas** (1.3.2) - Data manipulation and analysis
- **numpy** (1.21.2) - Numerical computing
- **scipy** (1.7.1) - Scientific computing

### Web Framework
- **Django** (3.1) - Web application framework
- **gunicorn** (20.1.0) - WSGI HTTP Server

### Supporting Libraries
- **joblib** (1.0.1) - Model serialization
- **pytz** (2021.1) - Timezone handling
- **sqlparse** (0.4.1) - SQL parsing

### Deployment
- **Heroku** - Cloud deployment platform

## 🚀 Installation

### Prerequisites
- Python 3.7 or higher
- pip (Python package manager)
- Virtual environment tool (venv or virtualenv)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/happyananya/Phishing_Project.git
   cd Phishing_Project
   ```

2. **Navigate to the project directory**
   ```bash
   cd "ML Project - Phishing"
   cd mysite
   ```

3. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

5. **Run database migrations**
   ```bash
   python manage.py migrate
   ```

6. **Start the development server**
   ```bash
   python manage.py runserver
   ```

7. **Access the application**
   Open your browser and navigate to `http://127.0.0.1:8000/`

## 💻 Usage

### Web Interface

1. Navigate to the application homepage
2. Enter the required URL features in the form:
   - Website name
   - Number of dots in URL
   - Path level depth
   - Number of dashes
   - Count of sensitive words
   - Percentage of external hyperlinks
   - Percentage of external resource URLs
   - Presence of insecure forms
   - Percentage of null/self-redirect hyperlinks
   - Frequent domain name mismatch
   - Form submission to email
   - Use of iframes or frames

3. Submit the form to receive a prediction
4. View the result indicating whether the URL is classified as phishing or legitimate

### Model Training

To retrain the model with new data:

1. Open `Phishing.ipynb` in Jupyter Notebook
2. Update the dataset path if using different data
3. Modify model parameters as needed
4. Execute all cells to train and save the model
5. The trained model will be saved as `polls/Phishing.pickle`

## 🧠 Machine Learning Model

### Model Details
- **Algorithm**: Scikit-learn classifier (gradient boosting, random forest, or similar)
- **Training Data**: Labeled URL dataset with 11 features
- **Output**: Binary classification (0 = Legitimate, 1 = Phishing)
- **Model Format**: Pickle serialization for easy deployment

### Feature Engineering
The model analyzes 11 critical URL characteristics:

| Feature | Description |
|---------|-------------|
| NumDots | Number of dots in the URL |
| PathLevel | Depth of the URL path |
| NumDash | Number of dashes in the URL |
| NumSensitiveWords | Count of sensitive keywords (e.g., "login", "verify") |
| PctExtHyperlinks | Percentage of external hyperlinks |
| PctExtResourceUrls | Percentage of external resource URLs |
| InsecureForms | Presence of insecure form submissions |
| PctNullSelfRedirectHyperlinks | Percentage of null or self-redirecting hyperlinks |
| FrequentDomainNameMismatch | Frequency of domain name mismatch |
| SubmitInfoToEmail | Forms submitting information to email |
| IframeOrFrame | Presence of iframes or frames |

## 📊 Dataset

The project uses `Phishing.csv` containing:
- **Features**: 11 URL characteristics (numeric)
- **Label**: Binary classification (phishing or legitimate)
- **Format**: CSV with headers

### Data Characteristics
- Comprehensive URL feature extraction
- Balanced or relevant class distribution
- Preprocessed and ready for ML model training

## 🌐 Deployment

### Heroku Deployment

The project is configured for Heroku deployment:

1. **Configuration Files**
   - `Procfile`: Defines application startup command
   - `runtime.txt`: Specifies Python version

2. **Deploy Steps**
   ```bash
   heroku login
   heroku create phishing-websites  # or your app name
   git push heroku main
   heroku run python manage.py migrate
   ```

3. **Access Deployed App**
   - Visit: `https://phishing-websites.herokuapp.com`

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Submit a Pull Request

## 📝 License

This project is open source and available under the MIT License.

## 👤 Author

**Ananya Agarwal**
- GitHub: [@happyananya](https://github.com/happyananya)

## 🔗 References

- [Django Documentation](https://docs.djangoproject.com/)
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [Phishing Detection Research](https://en.wikipedia.org/wiki/Phishing)

## ⚠️ Disclaimer

This tool is intended for educational and research purposes. While it aims to detect phishing websites with reasonable accuracy, it should not be relied upon as the sole security measure. Always practice safe browsing habits and use multiple security tools in conjunction with this application.

