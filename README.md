# 🌐 Multilingual Chatbot

An AI-powered multilingual chatbot designed to make information accessible through natural-language conversations. Built using React, Django REST Framework, and AI-powered language-processing components, the project combines conversational AI, knowledge retrieval, and multilingual interaction in a unified application.

**Repository:** [Multilingual-Chatbot](https://github.com/aadhii-i/Multilingual-Chatbot)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Technology Stack](#-technology-stack)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Installation and Setup](#-installation-and-setup)
- [Environment Configuration](#-environment-configuration)
- [Running the Application](#-running-the-application)
- [API Overview](#-api-overview)
- [Knowledge Base and RAG](#-knowledge-base-and-rag)
- [Testing](#-testing)
- [Security](#-security)
- [Future Improvements](#-future-improvements)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Overview

Multilingual Chatbot is a full-stack conversational application that combines a modern web interface with backend AI and language-processing capabilities.

The application is organized into independent frontend and backend components, making it easier to develop, test, and extend its functionality.

The backend includes chatbot agent logic, language processing, retrieval-augmented generation (RAG), conversation management, authentication, speech processing, eligibility checks, feedback handling, and escalation components.

A structured knowledge base and document-ingestion utilities support information retrieval workflows.

### Project Objectives

- Provide a conversational interface for accessing information.
- Support multilingual text processing.
- Retrieve relevant information from a knowledge base.
- Integrate AI-powered conversational capabilities.
- Support user authentication and conversation-related workflows.
- Maintain a modular architecture for future development.

---

## ✨ Features

### 💬 Conversational AI
- Chatbot agent and conversation-management components.
- AI integration through the Groq ecosystem.
- Retrieval-augmented generation (RAG) components.
- Knowledge retrieval and repository abstractions.

### 🌍 Multilingual Processing
- Language-processing utilities.
- Language-detection components.
- Tests for multilingual interactions.
- Code-switching evaluation.
- Manglish and Tanglish input-processing tests.

### 📚 Knowledge Base
- Document-ingestion utilities.
- Embedding generation using Sentence Transformers.
- Knowledge-base seeding and import scripts.
- Retrieval and embedding evaluation tests.
- Word-document processing support.

### 🔊 Speech Processing
- Speech-related backend components.
- Text-to-speech integration through gTTS.
- Speech API and processing tests.

### 🔐 Authentication and User Management
- Authentication services and views.
- User-management components.
- Administrative authentication components.
- Login and registration interfaces.

### 🧭 Dashboard and User Interaction
- Chat interface.
- Dashboard components.
- Feedback dialog.
- Quick prompts.
- Sidebar and navigation components.
- Campus map interface components.

### ⚙️ Backend Services
- Eligibility-related processing.
- Feedback management.
- Escalation components.
- Conversation-related services.
- Modular API organization.

*Feature availability depends on the current implementation and configuration of each component.*

---

## 🛠️ Technology Stack

### Frontend

| Technology | Purpose |
|---|---|
| React 19 | User interface |
| Vite | Development server and build tooling |
| JavaScript / JSX | Frontend development |
| Tailwind CSS | Styling |
| Lucide React | Icons |
| React Markdown | Markdown rendering |

### Backend

| Technology | Purpose |
|---|---|
| Python | Backend development |
| Django | Web framework |
| Django REST Framework | API development |
| django-cors-headers | Cross-origin request configuration |
| python-decouple | Configuration management |
| Groq | AI model integration |
| Sentence Transformers | Text embeddings |
| langdetect | Language detection |
| gTTS | Text-to-speech |
| Beautiful Soup | HTML parsing |
| python-docx | Word-document processing |
| PyPDF | PDF processing |
| Requests | HTTP requests |

### Data and Storage

- SQLite is configured as the Django database.
- MongoDB-related ingestion utilities support knowledge-base workflows.
- Document-processing and embedding components support retrieval workflows.

---

## 🏗️ System Architecture

```text
                         ┌──────────────────────┐
                         │         User         │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    React Frontend    │
                         │                      │
                         │  Chat Interface      │
                         │  Authentication      │
                         │  Dashboards          │
                         └──────────┬───────────┘
                                    │
                               HTTP / API
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │ Django REST Framework│
                         │                      │
                         │  Chatbot Agent       │
                         │  Language Processing  │
                         │  Conversation Logic  │
                         │  Authentication      │
                         │  Feedback / Escalation│
                         └──────────┬───────────┘
                                    │
                     ┌──────────────┴──────────────┐
                     │                             │
                     ▼                             ▼
          ┌─────────────────────┐       ┌────────────────────┐
          │ Knowledge Retrieval  │       │ AI / Language      │
          │ and RAG Components   │       │ Processing         │
          └──────────┬──────────┘       └────────────────────┘
                     │
                     ▼
          ┌─────────────────────┐
          │ Documents and       │
          │ Embeddings          │
          └─────────────────────┘
```

The diagram represents the major application components. The exact execution flow depends on the implementation of the individual services.

---

## 📁 Project Structure

```text
Multilingual-Chatbot/
│
├── backend/
│   ├── chatbot/
│   │   ├── agent.py
│   │   ├── rag.py
│   │   ├── language.py
│   │   ├── speech.py
│   │   ├── conversation.py
│   │   ├── eligibility.py
│   │   ├── escalation.py
│   │   ├── feedback_service.py
│   │   ├── auth_service.py
│   │   ├── auth_views.py
│   │   ├── admin_auth.py
│   │   ├── admin_views.py
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   └── repositories/
│   │
│   ├── core/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── asgi.py
│   │   └── wsgi.py
│   │
│   ├── ingestion/
│   │   ├── embedding.py
│   │   ├── ingest_docx.py
│   │   └── ingest_to_mongodb.py
│   │
│   ├── scripts/
│   ├── requirements.txt
│   └── manage.py
│
├── frontend/
│   ├── src/
│   │   ├── app/
│   │   ├── components/
│   │   ├── styles/
│   │   ├── App.jsx
│   │   ├── api.js
│   │   └── main.jsx
│   ├── admin.html
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
│
├── knowledge_base/
│   └── iiitk_knowledge_base.docx
│
├── docs/
├── tests/
├── .gitignore
└── README.md
```

---

## 🚀 Installation and Setup

### Prerequisites

Ensure that you have installed:

- Python 3.10 or a compatible version for the project's dependencies.
- Node.js and npm.
- Git.
- Credentials for any external AI services required by your configuration.
- MongoDB access if using the MongoDB-based ingestion workflows.

### 1. Clone the Repository

```bash
git clone https://github.com/aadhii-i/Multilingual-Chatbot.git
cd Multilingual-Chatbot
```

### 2. Set Up the Backend

Navigate to the backend directory:

```bash
cd backend
```

Create a virtual environment:

```bash
python3 -m venv .venv
```

Activate the environment on Linux or macOS:

```bash
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Install the dependencies:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 3. Configure Environment Variables

Create your local environment file from the example:

```bash
cp .env.example .env
```

Open `.env` and configure the required values.

Do not commit your actual `.env` file or expose API credentials.

### 4. Initialize the Database

Run the Django migrations:

```bash
python manage.py migrate
```

Optionally, create a Django administrator account:

```bash
python manage.py createsuperuser
```

### 5. Start the Backend

```bash
python manage.py runserver 8000
```

The backend development server will be available at:

http://127.0.0.1:8000/

Keep the terminal running.

### 6. Set Up the Frontend

Open a second terminal from the project root:

```bash
cd frontend
```

Install the dependencies:

```bash
npm install
```

Start the frontend development server:

```bash
npm run dev
```

Open the application at:

http://localhost:5173/

The Vite development configuration proxies `/api` requests to the backend at `http://127.0.0.1:8000`.

---

## ⚙️ Environment Configuration

The backend provides an `.env.example` file as a starting point for local configuration.

Depending on the enabled functionality, configuration may include:

- Django settings and secret configuration.
- External AI service credentials.
- Database settings.
- Knowledge-base ingestion settings.
- Other service-specific values.

Refer to the actual environment example and backend settings for the exact variable names and required values.

**Never publish API keys, passwords, private tokens, or production credentials.**

---

## 🔌 API Overview

The backend uses Django URL configuration to organize its endpoints.

The main URL configuration includes:

| Route | Purpose |
|---|---|
| `/api/` | Chatbot application API routes |
| `/admin/` | Django administration interface |

The chatbot's individual endpoint definitions are maintained in:

```text
backend/chatbot/urls.py
```

The frontend API integration is maintained in:

```text
frontend/src/api.js
```

Refer to these files for exact endpoint paths, HTTP methods, request formats, authentication requirements, and response structures.

---

## 📚 Knowledge Base and RAG

The repository includes a knowledge-base document and utilities for processing knowledge sources.

### Main Components

| File | Purpose |
|---|---|
| `backend/chatbot/rag.py` | RAG-related components |
| `backend/chatbot/repositories/knowledge_repository.py` | Knowledge repository abstraction |
| `backend/ingestion/embedding.py` | Embedding generation |
| `backend/ingestion/ingest_docx.py` | Word-document ingestion |
| `backend/ingestion/ingest_to_mongodb.py` | MongoDB ingestion workflow |
| `backend/scripts/` | Knowledge-base seeding, import, evaluation, and maintenance |

### General Workflow

1. Prepare the knowledge documents.
2. Process the source documents.
3. Generate or maintain embeddings.
4. Retrieve relevant information for a query.
5. Use the retrieval components as part of the chatbot response workflow.

The exact ingestion procedure depends on the selected storage backend and application configuration.

---

## 🧪 Testing

The repository includes tests for different chatbot components and workflows.

Examples include:

- `backend/test_agent.py`
- `backend/test_all_languages.py`
- `backend/test_code_switching.py`
- `backend/test_context.py`
- `backend/test_eligibility.py`
- `backend/test_embedding.py`
- `backend/test_language_detection.py`
- `backend/test_multilingual_agent.py`
- `backend/test_retrieval.py`
- `backend/test_speech.py`
- `backend/test_translation.py`

Run the Django test suite from the backend directory:

```bash
cd backend
python manage.py test
```

Individual test modules can also be executed using the appropriate test runner.

Ensure that the necessary environment variables and external services are configured before running tests that depend on them.

---

## 🔒 Security

- Store credentials in environment variables.
- Never commit `.env` files containing secrets.
- Exclude virtual environments and generated artifacts from version control.
- Configure allowed frontend origins appropriately before production deployment.
- Apply appropriate authentication and authorization checks to protected endpoints.
- Use production-grade Django settings when deploying publicly.
- Avoid exposing development databases or administrative interfaces unnecessarily.

---

## 🛣️ Future Improvements

Potential areas for further development include:

- Expanded multilingual evaluation and language coverage.
- Improved retrieval relevance and response quality.
- More comprehensive API documentation.
- Additional automated integration tests.
- Better error reporting and observability.
- Production deployment documentation.
- Performance monitoring for AI and retrieval workflows.

These are potential improvements, not claims that every item is currently implemented.

---

## 🤝 Contributing

Contributions that improve functionality, reliability, documentation, testing, or multilingual interaction are welcome.

To contribute:

1. Fork the repository.
2. Create a feature branch.
3. Implement your changes.
4. Test the relevant functionality.
5. Commit your changes with a descriptive message.
6. Open a pull request describing your changes.

Please avoid including credentials, private information, or environment-specific files in commits.

---

## 📄 License

A license has not been specified in this README. Check the repository for an existing license before reusing or redistributing the project.

---

## 👨‍💻 Repository

**GitHub:** [aadhii-i/Multilingual-Chatbot](https://github.com/aadhii-i/Multilingual-Chatbot)

Built with React, Django, Python, and AI-powered language-processing components.
