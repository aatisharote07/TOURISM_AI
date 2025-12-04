# Global Tourism AI Platform

A comprehensive analytics platform that combines Power BI dashboards with AI-powered insights, travel planning, gamification, and advanced admin features.

## 🌟 Features

### 🔐 Authentication & User Management
- **JWT-based authentication** with secure token management
- **Google OAuth** integration for social login
- **Role-based access control** (User, Pro User, Admin, Super Admin)
- **Email verification** and password reset functionality
- **User blocking/unblocking** by admins
- **User promotion/demotion** system

### 📊 Power BI Dashboard Integration
- **Embed Power BI dashboards** via public embed URLs
- **Track user interactions** (page switches, filters, clicks)
- **Capture screenshots** of dashboards
- **OCR text extraction** using Tesseract
- **Dashboard metadata** storage
- **Category organization** (Tourism, Sales, Finance, General Analytics)
- **Favorite dashboards** system

### 🤖 AI-Powered Features

#### AI Insight Story Mode
- **Animated slide-by-slide insights** with overlays
- **AI-generated explanations** for dashboard data
- **Text-to-speech narration** support
- **Auto-highlight overlays** on key metrics
- **Auto movement animations** for visual appeal
- **Pause/Resume/Exit** controls

#### AI Auto-Insight Engine
- **Automatic screenshot capture**
- **OCR text extraction** from dashboard images
- **AI analysis** identifying:
  - Highest/lowest values
  - Trend directions
  - Outliers and anomalies
- **Export insights** as PDF, DOCX, or Email
- **Insight storage** in database

### 🔍 Visual Trend Comparison
- **Compare two Power BI dashboards** side-by-side
- **Visual diff generation**
- **Combined overlay view**
- **AI comparison summary**
- **Color-coded variations**
- **PDF export** of comparisons

### 🏅 Gamification System
- **Automatic badge awards** based on actions:
  - **Explorer**: Viewed 10+ countries
  - **Analyst**: Compared multiple dashboards
  - **Trend Hunter**: Used time slider
  - **Reviewer**: Submitted 5+ feedbacks
  - **Story Master**: Used Story Mode 3 times
- **Badge popup animations**
- **Badge gallery** view
- **Badge progress tracker**
- **Admin badge control**

### 🎒 Smart Travel Itinerary Planner
- **AI-generated travel plans** based on:
  - Best travel months
  - Budget estimates
  - Weather conditions
  - Crowd density
  - Trip sequence optimization
  - Hotel & flight cost predictions
- **Timeline visualization**
- **Budget summary**
- **Best sequence recommendations**
- **PDF export** and profile integration

### 📜 Personal Analytics Timeline
- **Track all user actions**:
  - Dashboard views
  - Insights generated
  - Countries clicked
  - Badges unlocked
  - Itineraries generated
  - Feedback submitted
- **Beautiful timeline UI** with icons and timestamps
- **Category filtering**
- **PDF export** capability

### 🧩 Feedback Analyzer
- **AI categorization** of feedback:
  - Bug reports
  - Feature requests
  - Improvements
  - Positive feedback
- **Admin panel** with:
  - Pie chart visualization
  - Keyword cloud
  - Top issues list
  - Auto-reply system

### 🔎 Recommendation Engine
- **Smart dashboard recommendations** based on:
  - Title similarity
  - Tag matching
  - OCR keywords
  - User behavior analytics
- **Personalized suggestions** for each user

### 🛠️ Admin Panel
Comprehensive admin dashboard with:

#### Dashboard Overview
- Total users
- Daily active users
- Total dashboards added
- Insights generated
- OCR runs
- AI story usages
- Top dashboards

#### User Management
- Block/unblock users
- Promote/demote users
- Reset passwords
- View user logs
- View user badges

#### Dashboard Management
- Edit categories
- Delete dashboards
- Flag inappropriate content

#### Feedback Management
- View all feedback
- AI categories
- Auto-response replies
- Export feedback

#### System Logs
- OCR logs
- Story mode logs
- Insight generation logs
- Admin action logs

### 📨 Notification System
- **In-app notifications** for:
  - New badges earned
  - New insights available
  - Admin announcements
  - Dashboard updates
- **Email notifications** support
- **Global notifications** by admins

### 🎨 Additional Features
- **Dark/Light Mode** toggle
- **Multi-language Support** (English + Indian languages)
- **Role-based UI** elements
- **Export all insights** as ZIP
- **Activity heatmap** (GitHub-style)
- **QR code share links** for dashboards
- **Offline mode** with caching (PWA support)

## 🚀 Installation

### Prerequisites
- Python 3.8+
- PostgreSQL (or SQLite for development)
- Tesseract OCR installed
- Node.js (for frontend assets, optional)

### Setup

1. **Clone the repository**
```bash
cd "Global Tourism"
```

2. **Create virtual environment**
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Install Tesseract OCR**
- **Windows**: Download from [GitHub](https://github.com/UB-Mannheim/tesseract/wiki)
- **Linux**: `sudo apt-get install tesseract-ocr`
- **Mac**: `brew install tesseract`

5. **Configure environment variables**
Create a `.env` file:
```env
SECRET_KEY=your-secret-key-here
DATABASE_URL=postgresql://user:password@localhost/global_tourism
OPENAI_API_KEY=your-openai-api-key
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password
TESSERACT_CMD=C:\Program Files\Tesseract-OCR\tesseract.exe  # Windows only
```

6. **Initialize database**
```bash
flask --app wsgi db init
flask --app wsgi db migrate -m "Initial migration"
flask --app wsgi db upgrade
```

7. **Create admin user**
```bash
flask --app wsgi create-admin
```

8. **Run the application**
```bash
flask --app wsgi run
# Or for production:
gunicorn wsgi:app
```

## 📁 Project Structure

```
Global Tourism/
├── app/
│   ├── __init__.py          # Flask app factory
│   ├── models.py            # Database models
│   ├── forms.py             # WTForms definitions
│   ├── utils.py             # Utility functions
│   ├── blueprints/
│   │   ├── main/            # Main routes
│   │   ├── dashboards/      # Dashboard routes
│   │   ├── insights/        # Insights routes
│   │   ├── compare/         # Comparison routes
│   │   ├── users/           # Auth routes
│   │   ├── api/             # API endpoints
│   │   ├── admin/           # Admin panel
│   │   ├── chatbot/         # AI chatbot
│   │   └── features/        # Feature pages
│   ├── services/
│   │   ├── ai_service.py           # AI insights & categorization
│   │   ├── ocr_service.py          # OCR text extraction
│   │   ├── gamification_service.py  # Badge system
│   │   ├── itinerary_service.py     # Travel planning
│   │   ├── recommendation_service.py # Dashboard recommendations
│   │   ├── analytics_service.py     # Analytics
│   │   └── data_service.py          # Data processing
│   ├── static/
│   │   ├── css/            # Stylesheets
│   │   ├── js/             # JavaScript files
│   │   └── images/        # Images
│   └── templates/         # Jinja2 templates
├── config.py              # Configuration
├── requirements.txt       # Python dependencies
├── wsgi.py               # WSGI entry point
└── README.md             # This file
```

## 🔧 Configuration

### Database
The application supports both SQLite (development) and PostgreSQL (production). Set `DATABASE_URL` in your environment.

### AI Services
- **OpenAI API**: Required for AI insights and feedback categorization
- **Tesseract OCR**: Required for text extraction from screenshots

### Email
Configure SMTP settings for email verification and notifications.

## 📝 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user
- `POST /api/auth/google` - Google OAuth

### Dashboards
- `GET /api/dashboards` - List all dashboards
- `POST /api/dashboards` - Create new dashboard
- `POST /api/dashboards/<id>/interaction` - Track interaction
- `POST /api/dashboards/<id>/generate-insight` - Generate AI insight
- `GET /api/dashboards/<id>/story-mode` - Get story mode slides

### User Features
- `GET /api/recommendations` - Get dashboard recommendations
- `GET /api/badges` - Get user badges
- `GET /api/timeline` - Get activity timeline

## 🧪 Testing

```bash
# Run tests (when implemented)
pytest

# Check code coverage
pytest --cov=app
```

## 🚢 Deployment

### Production Checklist
- [ ] Set `SECRET_KEY` to a secure random value
- [ ] Use PostgreSQL database
- [ ] Configure SMTP for emails
- [ ] Set up OpenAI API key
- [ ] Configure Google OAuth credentials
- [ ] Enable HTTPS
- [ ] Set up proper logging
- [ ] Configure backup strategy

### Deployment Platforms
- **Render**: Use `gunicorn wsgi:app` as start command
- **Railway**: Automatic detection
- **Heroku**: Use Procfile
- **DigitalOcean**: Use App Platform

## 📄 License

This project is provided as-is for internal use.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📞 Support

For issues and questions, please contact the development team.

---

**Built with Flask, SQLAlchemy, OpenAI, and Tesseract OCR**
