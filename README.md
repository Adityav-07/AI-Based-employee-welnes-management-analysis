# AI-Based Employee Wellness Management Analysis

An AI-powered **Employee Wellness Management System** designed to help employees understand and track their emotional well-being while providing organizations with meaningful, privacy-conscious wellness insights.

The system combines **Natural Language Processing (NLP), sentiment analysis, emotion detection, wellness questionnaires, personalized recommendations, and an AI wellness chatbot** into a single platform.

---

## 📌 Project Overview

Employee well-being can have a significant impact on productivity, engagement, and workplace satisfaction. However, organizations often lack a simple way to understand employee wellness trends.

This project provides an AI-based platform where employees can:

* Record their mood and emotional state
* Write journal entries and receive AI-based analysis
* Upload CSV/TXT files containing employee feedback for NLP analysis
* Complete wellness questionnaires
* Receive personalized wellness recommendations
* Interact with an AI wellness chatbot
* View their mood history and wellness trends
* Export wellness data for further analysis

The system also provides an administrative/HR perspective for analyzing **aggregated employee wellness trends**.

---

## 🎯 Objectives

* Monitor employee emotional well-being using AI and NLP.
* Analyze employee feedback and journal text.
* Detect sentiment and emotional states from text.
* Provide personalized wellness recommendations.
* Identify overall wellness trends through questionnaires and mood history.
* Provide an AI-based conversational wellness assistant.
* Maintain authentication and security for employee data.
* Provide data export and visualization capabilities.

---

## ✨ Key Features

### 👤 Employee Wellness Management

* Employee registration and login
* Email OTP verification
* Password reset using OTP
* Employee profile management
* Profile photo support
* Mood logging
* Mood history
* Wellness questionnaire
* Wellness score and category
* Personalized recommendations

### 🧠 AI & NLP Analysis

The system includes a multilingual NLP pipeline for analyzing employee text.

It supports:

* Language detection
* Text cleaning and normalization
* Emoji processing
* Text fixing
* Translation support
* Sentiment analysis
* Emotion detection
* Confidence scoring
* AI-generated wellness responses

The project uses libraries including **spaCy, Transformers, PyTorch, VADER Sentiment, langdetect, deep-translator, ftfy, emoji, and stopwordsiso**.

### 📂 CSV/TXT Analysis

Employees or administrators can upload **CSV or TXT files** containing textual feedback.

The backend provides an `/analyze` API endpoint for uploaded files and an `/analyze-text` endpoint for direct text analysis.

The system can process the uploaded feedback through the NLP pipeline and display the resulting analysis and recommendations.

### 💬 AI Wellness Chatbot

The platform includes a wellness chatbot that can interact with employees based on their wellness context.

The backend connects the chatbot functionality through the NLP pipeline and provides wellness chat responses.

### 📊 Wellness Analytics

The system provides:

* Mood trends
* Emotion distribution
* Sentiment information
* Questionnaire scores
* Wellness categories
* Employee wellness history
* Team-level wellness insights
* Personalized recommendations
* Visual analytics

### 📄 Reports & Data Export

The application supports:

* PDF report generation
* CSV data export
* Questionnaire history export
* Wellness analysis reports

---

# 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │      Employee        │
                    │   / HR / Admin UI    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │      Streamlit       │
                    │       Frontend       │
                    └──────────┬───────────┘
                               │
                         HTTP / REST API
                               │
                               ▼
                    ┌──────────────────────┐
                    │       FastAPI        │
                    │       Backend        │
                    └───────┬───────┬──────┘
                            │       │
                 ┌──────────┘       └──────────┐
                 ▼                             ▼
       ┌──────────────────┐          ┌──────────────────┐
       │    NLP Pipeline  │          │   Authentication │
       │                  │          │                  │
       │ Sentiment        │          │ JWT              │
       │ Emotion          │          │ Bcrypt           │
       │ Language         │          │ OTP              │
       │ Translation      │          │ Account Lockout  │
       └────────┬─────────┘          └──────────────────┘
                │
                ▼
       ┌──────────────────┐
       │   PostgreSQL DB  │
       │                  │
       │ Users            │
       │ Mood Logs        │
       │ OTP Codes        │
       │ Questionnaires   │
       └──────────────────┘
```

---

# 🛠️ Technology Stack

## Programming Language

* **Python 3.11**

## Frontend

* **Streamlit**
* HTML/CSS customization
* Matplotlib
* Seaborn

The application UI is implemented using Streamlit.

## Backend

* **FastAPI**
* **Uvicorn**
* REST API
* Pydantic
* Python Requests

The project uses FastAPI for backend API endpoints and Uvicorn as the application server.

## Database

* **PostgreSQL**
* `psycopg2-binary`

The database layer uses PostgreSQL and creates/manages tables for users, OTP codes, mood logs, questionnaire responses, and related wellness information.

## Artificial Intelligence / NLP

* **Hugging Face Transformers**
* **PyTorch**
* **spaCy**
* **VADER Sentiment**
* **LangDetect**
* **Deep Translator**
* **FTFY**
* **Emoji**
* **StopwordsISO**

## Machine Learning / Data Processing

* **Pandas**
* **Scikit-learn**
* **Matplotlib**
* **Seaborn**

## Authentication & Security

* **JWT / PyJWT**
* **Bcrypt**
* OTP-based email verification
* Account lockout after repeated failed login attempts
* Text sanitization using **Bleach**
* Environment-variable based secret management

The authentication layer uses JWT tokens, Bcrypt password hashing, OTP functionality, and login-attempt controls.

## Email

* Gmail SMTP
* Python `smtplib`
* Gmail App Password

Email is used for sending verification and password-reset OTPs.

## Reporting

* **ReportLab**
* PDF report generation
* CSV export

## Deployment

* **Docker**
* Docker Compose
* Python 3.11 Docker images
* Streamlit container
* FastAPI container

The project contains separate Docker configurations for the frontend and backend and a Docker Compose configuration connecting both services.

## CI/CD

* **GitHub Actions**
* Python compilation checks
* Dependency installation
* Docker image builds

The CI workflow runs syntax checks and builds both frontend and backend Docker images.

---

# 🔐 Authentication & Security

The system implements multiple security mechanisms:

* Password hashing using Bcrypt
* JWT-based authentication
* Token expiration
* Email OTP verification
* Password reset through OTP
* Failed-login tracking
* Temporary account lockout
* Input sanitization
* Environment variables for sensitive credentials
* Database connection through protected credentials

Sensitive values such as database credentials, JWT secrets, SMTP credentials, and API tokens are loaded through environment variables rather than being hard-coded.

---

# 🗄️ Database

The project uses **PostgreSQL**.

Major database components include:

### Users

Stores:

* User ID
* Username
* Email
* Password hash
* Verification status
* Role
* Failed login attempts
* Account lockout information
* Profile photo

### OTP Codes

Stores:

* Email
* OTP code
* Purpose
* Expiration time
* Used status

### Mood Logs

Stores:

* Employee
* Mood date
* Sentiment
* Emotion
* Compound score
* Confidence
* Journal text
* Source
* Timestamp

### Questionnaire Responses

Stores:

* Employee
* Answers
* Total score
* Maximum score
* Wellness category
* Preference for talking/support
* Submission time

The application automatically creates and updates these database structures through its database initialization logic.

---

# 📋 Wellness Questionnaire

The system contains a structured wellness questionnaire covering areas such as:

* Current mood
* Overall mood
* Stress
* Main factors affecting mood
* Energy level
* Sleep quality
* Preferred support
* Desire to talk
* Frequency of negative emotions
* Confidence in managing emotions
* Immediate support needs
* Personalized recommendation preferences

Responses are scored and categorized into:

```text
Thriving
Doing Well
Needs Attention
At Risk
```

The application then generates recommendations based on the employee's wellness category and selected support preferences.

---

# 📈 Analytics

The system can analyze:

* Individual mood patterns
* Emotion distribution
* Sentiment trends
* Questionnaire results
* Wellness categories
* Common factors affecting employee mood
* Preferred support types
* Overall team wellness patterns

The recommendation engine can also generate team-level insights from mood and questionnaire data.

---



# ⚙️ Main Dependencies

```text
streamlit
fastapi
uvicorn
python-multipart
requests
psycopg2-binary
PyJWT
bcrypt
python-dotenv
email-validator
langdetect
ftfy
emoji
deep-translator
vaderSentiment
spacy
pandas
matplotlib
seaborn
transformers
accelerate
torch
stopwordsiso
reportlab
bleach
```

The project's `requirements.txt` contains the primary runtime dependencies used by the application.

---

#  Running the Project

## 1. Clone the repository

```bash
git clone <your-repository-url>
cd AI-Based-Employee-Wellness-Management-Analysis
```

## 2. Install Python dependencies

```bash
pip install -r requirements.txt
```

## 3. Configure environment variables

Create a `.env` file containing your PostgreSQL, JWT, SMTP, and other required configuration values.

Example:

```env
DB_HOST=your-postgres-host
DB_PORT=5432
DB_NAME=your-database-name
DB_USER=your-database-user
DB_PASSWORD=your-database-password

JWT_SECRET=your-secret-key

SMTP_EMAIL=your-email@gmail.com
SMTP_APP_PASSWORD=your-gmail-app-password

BACKEND_URL=http://localhost:8000
```

**Never commit the real `.env` file to GitHub.**

---

# ▶️ Run the Backend

```bash
uvicorn backend:app --host 0.0.0.0 --port 8000
```

Backend:

```text
http://localhost:8000
```

Health check:

```text
http://localhost:8000/health
```

---

# ▶️ Run the Frontend

```bash
streamlit run app.py
```

Frontend:

```text
http://localhost:8501
```

---

# 🐳 Docker Deployment

The project includes Docker support for running the frontend and backend as separate services.

```bash
docker compose up --build
```

The resulting services are:

```text
Frontend → Streamlit → Port 8501
Backend  → FastAPI   → Port 8000
```

The frontend communicates with the backend through the Docker network.

---

# 🔄 CI Pipeline

GitHub Actions is configured to:

1. Set up Python 3.11
2. Install dependencies
3. Compile Python modules
4. Build the backend Docker image
5. Build the frontend Docker image

This helps identify syntax and Docker build issues before deployment.

---

# 📸 Screenshots

Screenshots of the application's main modules are available in the `Screenshots` folder.

Recommended screenshots include:

* Login / Registration
* Employee Dashboard
* Mood Analysis
* Wellness Questionnaire
* AI Chatbot
* CSV/TXT Upload
* Analytics Dashboard
* Wellness Recommendations
* Database Schema

---

# 🔒 Privacy & Responsible Use

This project is intended as an **employee wellness support and analytics system**, not as a medical diagnostic system.

AI-generated sentiment, emotion, and wellness results should be treated as supportive indicators rather than clinical diagnoses.

Employee wellness information should be handled responsibly, with appropriate access controls, privacy policies, and organizational consent.

---

# 🔮 Future Enhancements

Possible future improvements include:

* Advanced employee wellness dashboards
* More sophisticated emotion classification
* Real-time wellness trend monitoring
* Improved multilingual NLP models
* More advanced recommendation models
* Anonymous organization-level analytics
* Cloud deployment
* Improved role-based administration
* Additional wellness metrics
* Integration with organizational HR systems

---

# 👨‍💻 Project

**AI-Based Employee Wellness Management Analysis**

Developed as an AI/NLP-based employee wellness management and analytics project.

### Core Technologies

**Python • Streamlit • FastAPI • PostgreSQL • NLP • Transformers • PyTorch • spaCy • VADER • JWT • Bcrypt • Docker • GitHub Actions**

---

## ⭐ Project Highlights

> **AI-powered employee wellness platform combining NLP-based emotional analysis, wellness questionnaires, personalized recommendations, conversational support, analytics, secure authentication, and PostgreSQL data management in a single application.**
