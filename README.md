# 🧠 InsightHub

Chat with AI, upload documents (PDFs, audio files), and get intelligent responses based on your content using RAG (Retrieval Augmented Generation).

## ✨ Features

- 🤖 **AI Chat Interface** - Natural conversations powered by OpenAI GPT models
- 📄 **Document Upload** - Support for PDFs, audio files (MP3, WAV, MP4)
- 🎙️ **Audio Transcription** - Automatic transcription of audio files using OpenAI Whisper
- 🔍 **Semantic Search** - ChromaDB vector database for intelligent document retrieval
- 💬 **Conversation History** - Save and resume conversations
- 👤 **User Authentication** - Secure JWT-based authentication
- 🎨 **Modern UI** - Streamlit interface with responsive design

## 🏗️ Architecture

```
┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐
│   Streamlit     │─────▶│   FastAPI       │─────▶│   PostgreSQL    │
│   Frontend      │      │   Backend       │      │   Database      │
└─────────────────┘      └─────────────────┘      └─────────────────┘
                               │
                               ▼
                         ┌─────────────────┐
                         │   ChromaDB      │
                         │   Vector Store  │
                         └─────────────────┘
```

## 🚀 Quick Start

### Prerequisites

- Docker & Docker Compose
- OpenAI API Key
- Tavily API Key
- ChromaDB Cloud account

### 1. Clone the Repository

```bash
git clone https://github.com/nicpack/insighthub.git
cd insighthub
```

### 2. Configure Environment Variables

Create a `.env` file in the project root and fill it using attached `.env.example`.

### 3. Start the Application

```bash
docker-compose up --build
```

The application will be available at:
- **Frontend**: http://localhost:8501
- **Backend API**: http://localhost:8000
- **API Docs**: http://localhost:8000/docs

### 4. Create Your First Account

1. Open http://localhost:8501
2. Use the admin credentials from `.env` to log in
3. Start chatting!

### Project Structure

```
insighthub/
├── insighthub-backend/
│   ├── app/
│   │   ├── api/              # API routes
│   │   ├── core/             # Core functionality (config, db)
│   │   ├── models.py         # Database models
│   │   ├── crud.py           # Database operations
│   │   └── main.py           # FastAPI application
│   ├── Dockerfile
│   ├── pyproject.toml
│   └── entrypoint.sh
│
├── insighthub-frontend/
│   ├── app/
│   │   ├── ui/               # UI components
│   │   ├── utils/            # Helper functions
│   │   └── app.py            # Main Streamlit app
│   ├── Dockerfile
│   └── requirements.txt
│
├── docker-compose.yml
├── .env
└── README.md
```

### Running Locally (Without Docker)

#### Backend

```bash
cd insighthub-backend
uv venv
source .venv/bin/activate  # or `.venv\Scripts\activate` on Windows
uv sync
uv run uvicorn app.main:app --reload
```

#### Frontend

```bash
cd insighthub-frontend
uv venv
source .venv/bin/activate  # or `.venv\Scripts\activate` on Windows
uv sync
uv run streamlit run app/app.py
```

### Database Migrations

Initialize the database:

```bash
cd insighthub-backend
python -m app.core.db
```

## 📚 API Documentation

Once the backend is running, visit:
- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

### Key Endpoints

- `POST /login/access-token` - User authentication
- `GET /conversations/` - List all conversations
- `POST /conversations/` - Create new conversation
- `POST /conversations/{id}/messages` - Send message
- `POST /embeddings/{conversation_id}` - Upload document

## 🔧 Configuration

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `POSTGRES_USER` | PostgreSQL username | - |
| `POSTGRES_PASSWORD` | PostgreSQL password | - |
| `POSTGRES_DB` | Database name | insighthub |
| `OPENAI_API_KEY` | OpenAI API key | - |
| `SECRET_KEY` | JWT secret key | - |
| `ACCESS_TOKEN_EXPIRE_MINUTES` | Token expiration time | 30 |

### Supported File Types

- **Documents**: PDF
- **Audio**: MP3, WAV, MP4


## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [FastAPI](https://fastapi.tiangolo.com/) - Modern web framework
- [Streamlit](https://streamlit.io/) - Interactive web apps
- [OpenAI](https://openai.com/) - GPT models and Whisper
- [ChromaDB](https://www.trychroma.com/) - Vector database
- [LangChain](https://langchain.com/) - LLM framework

## 📧 Contact

Nicolas Stupak - nicostupak@gmail.com

Project Link: [https://github.com/yourusername/insighthub](https://github.com/nicpack/insighthub)

---

Made with ❤️ and 🤖


