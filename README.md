# Real-Time Conversational AI Platform

A scalable, real-time platform featuring a React frontend and FastAPI backend. Users can log in, choose to chat with an AI agent (powered by Gemini and LangGraph), or join a multi-user chat room.

## 🚀 Features

- **Real-time Messaging**: Low-latency bidirectional communication using WebSockets.
- **AI Agent Integration**: Conversational AI powered by Google Gemini and orchestrators like LangGraph.
- **Multi-User Chat**: Public chat rooms for real-time collaboration.
- **Persistent History**: All interactions are stored in PostgreSQL with JSON metadata.
- **Containerized**: Fully Dockerized for consistent development and deployment.
- **Authentication**: User secure login and session management.

## 🛠 Tech Stack

- **Frontend**: React (Vite), TailwindCSS (recommended)
- **Backend**: FastAPI (Python), WebSockets
- **Database**: PostgreSQL (SQLAlchemy, Alembic)
- **AI/LLM**: Google Gemini API, LangGraph
- **Infrastructure**: Docker, Docker Compose

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- [Docker & Docker Compose](https://www.docker.com/)
- [Node.js (v18+)](https://nodejs.org/)
- [Python (v3.10+)](https://www.python.org/)
- [PostgreSQL](https://www.postgresql.org/) (Only needed if running locally without Docker)

---

## 🐳 Running with Docker (Recommended)

The easiest way to run the full stack (Frontend, Backend, and Database) is via Docker Compose.

1.  **Clone the repository** (if you haven't already):

    ```bash
    git clone <repository-url>
    cd realtime-conversational-ai-platform
    ```

2.  **Configure Environment Variables**:
    Create a `.env` file in the root directory:

    ```bash
    cp .env.example .env
    ```

    _Ensure you add your Google Gemini API Key and DB credentials in `.env`._

3.  **Start the services**:

    ```bash
    docker-compose up --build -d
    ```

    - **Frontend**: http://localhost:5173
    - **Backend API**: http://localhost:8000
    - **API Docs**: http://localhost:8000/docs
    - **PostgreSQL**: localhost:5432

4.  **Stop services**:
    ```bash
    docker-compose down
    ```

---

## 💻 Local Development Setup

If you prefer to run services individually for development:

### 1. Database Setup

Make sure you have a PostgreSQL instance running locally. Create a database named `conversational_ai_db`.

### 2. Backend (FastAPI)

1.  Navigate to the backend folder:
    ```bash
    cd backend
    ```
2.  Create and activate a virtual environment:
    ```bash
    python -m venv .venv
    # Windows
    .\.venv\Scripts\activate
    # Mac/Linux
    source .venv/bin/activate
    ```
3.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    # OR if using poetry
    poetry install
    ```
4.  Set up environment variables (`backend/.env`):
    ```env
    DATABASE_URL=postgresql://user:password@localhost/conversational_ai_db
    GEMINI_API_KEY=your_api_key
    SECRET_KEY=your_secret_key
    ```
5.  Run database migrations (if setup):
    ```bash
    alembic upgrade head
    ```
6.  Start the server:
    ```bash
    uvicorn app.main:app --reload
    ```

### 3. Frontend (React)

1.  Navigate to the frontend folder:
    ```bash
    cd frontend/react-app
    ```
2.  Install dependencies:
    ```bash
    npm install
    ```
3.  Start the development server:
    ```bash
    npm run dev
    ```
    Access the app at `http://localhost:5173`.

---

## 📂 Project Structure

```
├── backend/                # FastAPI application
│   ├── app/
│   │   ├── api_endpoints/  # Routes & WebSockets
│   │   ├── models/         # Database models
│   │   ├── services/       # Business logic & AI agents
│   │   └── main.py         # Entry point
│   ├── tests/
│   └── Dockerfile
├── frontend/               # React application
│   └── react-app/
│       ├── src/
│       └── Dockerfile
├── docker-compose.yml      # Orchestration
└── README.md
```
