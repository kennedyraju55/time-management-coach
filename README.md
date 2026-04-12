# ⏱️ Time Management Coach

A comprehensive time management system with productivity scoring, Pomodoro planning, time-block scheduling, deep work analytics, weekly reviews, and AI-powered coaching — your personal productivity consultant running 100% locally.

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Local LLM](https://img.shields.io/badge/Local_LLM-Ollama-000000.svg?style=for-the-badge&logo=ollama&logoColor=white)](https://ollama.com)
[![Privacy-First](https://img.shields.io/badge/100%25-Privacy--First-2ea043.svg?style=for-the-badge&logo=shield&logoColor=white)](#privacy-first)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![FastAPI](https://img.shields.io/badge/FastAPI-REST_API-009688.svg?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Streamlit](https://img.shields.io/badge/Streamlit-Web_UI-FF4B4B.svg?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io)

---

## ✨ Features

- **⏱️ Pomodoro Planning** - Structure your day into focused deep work sessions
- **📊 Productivity Scoring** - Track your productivity with intelligent scoring system
- **📅 Time-Block Scheduling** - AI-optimized daily schedule with time blocks
- **🎯 Focus Analytics** - Deep work metrics and focus streak tracking
- **📈 Weekly Reviews** - AI-powered insights with trends and improvements
- **💡 AI Coaching** - Get personalized productivity recommendations
- **⚡ Category Breakdown** - See exactly how you spend your time
- **🔒 100% Local** - All data stays on your machine
- **🎨 Web UI & API** - Use via web dashboard, CLI, or REST API

---

## 🏗️ Architecture

```
┌──────────────────────┐
│   User Input         │
│ (CLI/Web UI/API)     │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  Time Engine         │
│ - Scheduling        │
│ - Tracking          │
│ - Analytics         │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  Local LLM           │
│  (Ollama/Gemma)      │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  Insights & Reports  │
│  - Coaching         │
│  - Analytics        │
└──────────────────────┘
```

---

## 📋 Project Structure

```
time-management-coach/
├── src/time_coach/
│   ├── __init__.py              # Package initialization
│   ├── core.py                  # Time tracking & analysis
│   ├── scheduler.py             # Pomodoro & time-blocking
│   ├── analytics.py             # Productivity metrics
│   ├── cli.py                   # Click CLI interface
│   ├── api.py                   # FastAPI endpoints
│   └── web_ui.py                # Streamlit dashboard
├── tests/
│   ├── test_core.py             # Unit tests
│   └── __init__.py
├── config.yaml                  # Configuration
├── requirements.txt             # Dependencies
├── docker-compose.yml           # Docker setup
└── README.md                    # This file
```

---

## 🚀 Quick Start

### Prerequisites

- **Python 3.11+**
- **Ollama** (for local LLM)
- **Gemma 4 model** (via Ollama)

### Installation

```bash
# Clone the repository
git clone https://github.com/kennedyraju55/time-management-coach.git
cd time-management-coach

# Create and activate virtual environment
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Pull the AI model
ollama pull gemma4

# Verify installation
python -m time_coach.cli --help
```

### First Run

```bash
# Start Ollama
ollama serve &

# Create your daily schedule
python -m time_coach.cli schedule --hours 8 --template pomodoro

# Or launch web UI
streamlit run src/time_coach/web_ui.py

# Or use REST API
uvicorn src.time_coach.api:app --reload --port 8000
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Runtime** | Python 3.11+ | Core application |
| **CLI** | Click 8.1+ | Command-line interface |
| **Web** | Streamlit 1.28+ | Interactive dashboard |
| **API** | FastAPI | REST endpoints |
| **LLM** | Ollama + Gemma 4 | AI coaching insights |
| **Data** | JSON/YAML | Config & storage |
| **Testing** | pytest | Unit tests |
| **Deployment** | Docker | Container orchestration |

---

## 📖 CLI Reference

```bash
python -m time_coach.cli [COMMAND] [OPTIONS]
```

### Available Commands

| Command | Description | Example |
|---------|-------------|---------|
| schedule | Create optimized daily schedule | --hours 8 --template pomodoro |
| log | Log completed tasks/time | --task "Design UI" --minutes 60 |
| eport | View productivity report | --days 7 |
| nalytics | Deep work metrics | --metric focus_streak |
| coach | Get AI coaching tips | --focus area |
| week-review | Weekly analysis | --include-ai |

---

## 🌐 Web UI

Launch the interactive dashboard:

```bash
streamlit run src/time_coach/web_ui.py
```

Access at **http://localhost:8501**

Features:
- 📅 Visual calendar with time blocks
- 📊 Real-time productivity metrics
- 🎯 Pomodoro timer with tracking
- 💡 AI coaching suggestions
- 📈 Weekly analytics and trends

---

## ⚡ REST API

All features via FastAPI endpoints.

```bash
uvicorn src.time_coach.api:app --reload --port 8000
```

Interactive docs: **http://localhost:8000/docs**

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /health | Health check |
| POST | /schedule/generate | Create schedule |
| POST | /log/task | Log completed task |
| GET | /analytics/score | Productivity score |
| GET | /coach/suggestion | AI suggestion |

---

## 🐳 Docker Deployment

```bash
git clone https://github.com/kennedyraju55/time-management-coach.git
cd time-management-coach

docker compose up

# Access at http://localhost:8501
```

---

## 🧪 Testing

```bash
# Run all tests
pytest tests/ -v

# Run with coverage
pytest tests/ --cov=time_coach --cov-report=term-missing

# Run specific test
pytest tests/test_core.py::test_schedule_generation -v
```

---

## ⚙️ Configuration

Create a config.yaml:

```yaml
llm:
  model: "gemma4"
  temperature: 0.4
  max_tokens: 1500

scheduler:
  default_template: "pomodoro"
  pomodoro_duration: 25
  break_duration: 5

analytics:
  track_focus: true
  daily_goal_hours: 8
  min_deep_work_minutes: 90

categories:
  - "Deep Work"
  - "Meetings"
  - "Admin"
  - "Breaks"
```

---

## 🔒 Privacy-First

100% local processing:
- ✅ No cloud API calls
- ✅ No tracking or telemetry
- ✅ Your schedule stays private
- ✅ Full AI control
- ✅ GDPR/HIPAA compliant

---

## 📚 Python API

```python
from time_coach.core import create_schedule, log_task
from time_coach.analytics import get_productivity_score

# Create optimized schedule
schedule = create_schedule(
    hours=8,
    template="pomodoro",
    min_focus_duration=90
)

# Log completed task
log_task(
    name="Design database schema",
    minutes=120,
    category="Deep Work"
)

# Get productivity insights
score = get_productivity_score(days=7)
print(f"Weekly score: {score}")
```

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: git checkout -b feature/amazing-feature
3. Commit changes: git commit -m 'Add amazing feature'
4. Push to branch: git push origin feature/amazing-feature
5. Open a Pull Request

---

## 📄 License

Licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 👤 Author

**Nrk Raju Guthikonda**
- GitHub: [@kennedyraju55](https://github.com/kennedyraju55)
- Dev.to: [@kennedyraju55](https://dev.to/kennedyraju55)
- LinkedIn: [Nrk Raju Guthikonda](https://linkedin.com/in/nrk-raju-guthikonda)

---

<div align="center">

**Made with ❤️ by kennedyraju55**

[⭐ Star this repo if you found it helpful!](https://github.com/kennedyraju55/time-management-coach)

</div>
