# Global Tourism AI Platform

A comprehensive analytics platform that combines Power BI dashboards with AI-powered insights, travel planning, gamification, and advanced admin features — focused on visualizing **global holidays and travel data** to help travel agencies, policymakers, tourism boards, and travelers make data-driven decisions.

---

## 1. Project Statement & Outcomes

**Project:** Global Holidays and Travel Data Visualization

This project aims to develop an interactive Power BI dashboard that visualizes travel trends, holiday patterns, and tourism statistics across countries and regions. It includes collecting, preprocessing, and structuring historical and current data on global holidays, tourist arrivals, travel expenditures, and popular destinations to enable effective visualization and analysis.

**Outcomes:**

* A user-friendly Power BI dashboard embedded within a web application that allows users to analyze travel trends over time, monitor seasonal fluctuations, and compare tourism metrics across regions and countries.
* Interactive visualizations and filters to identify peak seasons, regional differences, and outliers.
* A hosted web application (Streamlit/Flask) that embeds the dashboard, enabling seamless interaction for travel professionals and the public.
* Comprehensive testing and documentation that detail data sources, preprocessing steps, dashboard features, and recommendations for future enhancements.

---

## 2. Modules to be Implemented

1. **Data Collection and Preprocessing** — Acquire and clean holidays and tourism datasets.
2. **Data Structuring and Power BI Dashboard Development** — Transform and model data for visualizations.
3. **Exploring and Streamlit Integration** — Host and embed the Power BI dashboard inside a web app.
4. **Testing, Review, and Documentation** — QA, user testing, and final documentation.

---

## 3. Week-wise Plan & High-Level Requirements

**Weeks 1–2: Data Collection & Preprocessing**

* Collect historical and current global holiday data from government tourism websites, UNWTO, and public travel APIs.
* Gather travel metrics: tourist arrivals, expenditures, popular destinations, and seasonal indicators.
* Clean and preprocess: handle missing values, outliers, inconsistent country names, and time-zone/date format issues.
* Ensure datasets are balanced and representative across countries, regions, and time ranges.

**Weeks 3–4: Data Structuring, Transformation & Power BI Dashboard Development**

* Design a data model optimized for Power BI (date tables, country/region hierarchies, normalized measures).
* Transform data: normalization, aggregation, feature engineering (season flags, holiday proximity, occupancy proxies).
* Build visuals: time-series trends, heatmaps, choropleth maps, top-destination tables, seasonality charts, and KPI cards.
* Add interactivity: filters, slicers, bookmarks, drill-through pages, and tooltips.
* Make the dashboard responsive and user-centered with clear legends and accessible color choices.

**Weeks 5–6: Web App & Power BI Integration**

* Develop a web application (Flask/Streamlit) to host the dashboard and supporting UI.
* Embed the Power BI dashboard via secure embed or iframe (for prototypes) inside the web app.
* Implement user authentication and role-based access for dashboards and admin features.
* Support dashboard interactions tracking for analytics and personalized recommendations.

**Weeks 7–8: Testing, Review & Documentation**

* Conduct functional, integration, and user-acceptance testing on the dashboard and web app.
* Review visualizations for clarity and domain relevance; refine with stakeholder feedback.
* Prepare full documentation: data lineage, preprocessing notebooks/scripts, dashboard guide, and API docs.
* Produce a final presentation and a packaged deliverable including exports (PDF/DOCX) and example reports.

---

## 4. Key Features (Technical + Product)

### 🔐 Authentication & User Management

* JWT-based authentication
* Google OAuth integration
* Role-based access control (User, Pro User, Admin, Super Admin)
* Email verification, password reset, and user promotion/block controls

### 📊 Power BI Dashboard Integration

* Embed Power BI dashboards (secure embed / public embed URLs)
* Track and log user interactions (filters, clicks, page changes)
* Capture dashboard screenshots & run OCR with Tesseract for metadata extraction
* Dashboard metadata storage, categories, and favorites

### 🤖 AI-Powered Insights

* **AI Insight Story Mode**: animated slide-by-slide storytelling with text-to-speech narration
* **Auto-Insight Engine**: automatic screenshot capture, OCR extraction, and AI analysis of trends, anomalies, and key metrics
* Exportable insights (PDF, DOCX, Email) with history stored in DB

### 🔍 Visual Comparison & Analysis

* Side-by-side dashboard comparison, visual diffs, and AI comparison summaries
* Time-series comparison, seasonality overlays, and color-coded variations

### 🏅 Gamification & Personal Analytics

* Badge system, activity timeline, and progress tracking to boost user engagement
* Smart recommendations for dashboards based on user behavior and OCR keywords

### 🎒 Smart Travel Itinerary Planner

* AI-generated itineraries using best months, budgets, weather, and crowd density
* Trip sequence optimization and cost predictions

### 🧩 Feedback & Recommendation Engine

* AI categorization of feedback (bugs, feature requests, improvements, positive)
* Admin feedback dashboard with keyword clouds and auto-reply suggestions

---

## 5. Technical Stack & Architecture

* **Backend:** Flask, SQLAlchemy
* **Frontend / Hosting:** Streamlit (for prototyping) or Flask + frontend assets, optional React for richer UI
* **Database:** PostgreSQL (production), SQLite (development)
* **BI:** Microsoft Power BI (dashboards & embed)
* **AI / NLP:** OpenAI API (insights, summarization), custom AI service layer
* **OCR:** Tesseract OCR for extracting text from dashboards/screenshots
* **Deployment:** Gunicorn + Nginx (production); supports Render, Railway, Heroku, DigitalOcean

---

## 6. Installation & Setup

### Prerequisites

* Python 3.8+
* PostgreSQL (or SQLite for development)
* Node.js (optional, for frontend builds)
* Tesseract OCR installed
* OpenAI API key (optional for AI features)

### Quick Setup

```bash
# Clone repository
cd "Global Tourism"

# Create virtual environment
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

#### Tesseract

* **Windows**: Download installer (e.g., UB Mannheim builds)
* **Linux**: `sudo apt-get install tesseract-ocr`
* **Mac**: `brew install tesseract`

#### Environment variables (`.env`)

```env
SECRET_KEY=your-secret-key
DATABASE_URL=postgresql://user:password@localhost/global_tourism
OPENAI_API_KEY=your-openai-api-key
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password
TESSERACT_CMD=C:\Program Files\Tesseract-OCR\tesseract.exe # Windows only
```

#### Database initialization

```bash
flask --app wsgi db init
flask --app wsgi db migrate -m "Initial migration"
flask --app wsgi db upgrade
```

#### Create admin

```bash
flask --app wsgi create-admin
```

#### Run (development)

```bash
flask --app wsgi run
# or
streamlit run app/streamlit_app.py
```

#### Production

```bash
gunicorn wsgi:app
```

---

## 7. Project Structure

```
Global Tourism/
├── app/
│   ├── __init__.py          # Flask app factory
│   ├── models.py            # Database models
│   ├── forms.py             # WTForms definitions
│   ├── utils.py             # Utility functions
│   ├── blueprints/          # Route modules (main, dashboards, insights, compare, users, api, admin, chatbot, features)
│   ├── services/            # AI, OCR, gamification, itinerary, recommendation, analytics, data processing
│   ├── static/              # CSS, JS, images
│   └── templates/           # Jinja2 templates
├── config.py
├── requirements.txt
├── wsgi.py
└── README.md
```

---

## 8. API Endpoints (High-level)

**Authentication**

* `POST /api/auth/register` — Register new user
* `POST /api/auth/login` — Login user
* `POST /api/auth/logout` — Logout user
* `POST /api/auth/google` — Google OAuth

**Dashboards**

* `GET /api/dashboards` — List dashboards
* `POST /api/dashboards` — Create dashboard
* `POST /api/dashboards/<id>/interaction` — Track interaction
* `POST /api/dashboards/<id>/generate-insight` — Generate AI insight
* `GET /api/dashboards/<id>/story-mode` — Story mode slides

**User / Features**

* `GET /api/recommendations`
* `GET /api/badges`
* `GET /api/timeline`

---

## 9. Testing

```bash
# Run tests
pytest

# Coverage
pytest --cov=app
```

Include unit tests for data preprocessing, API endpoints, and end-to-end test for the dashboard embed flow.

---

## 10. Deployment Checklist

* [ ] Set a secure `SECRET_KEY`
* [ ] Use PostgreSQL in production
* [ ] Configure SMTP for emails
* [ ] Set OpenAI and Google OAuth credentials
* [ ] Enable HTTPS and proper CORS rules
* [ ] Configure logging and monitoring
* [ ] Backups and DB maintenance plan

**Deployment platforms:** Render, Railway, Heroku, DigitalOcean (with Gunicorn & Nginx)

---

## 11. Documentation & Deliverables

* Data collection & preprocessing notebooks (Jupyter)
* Data dictionary & schema
* Power BI pbix file and published embed link
* Web app source and deployment guide
* Final report: insights, limitations, and next steps

---

## 12. Contributing

1. Fork the repo
2. Create a feature branch
3. Run tests and linting
4. Submit a pull request with clear description and linked issue

---

## 13. License

This project is provided as-is for internal and educational use.

---

## 14. Contact & Support

For issues or questions, contact the development team or open an issue in the repository.

---

*Built with Flask, SQLAlchemy, Power BI, OpenAI, and Tesseract OCR.*
