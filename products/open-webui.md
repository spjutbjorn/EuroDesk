# Open WebUI

**Category:** AI Interface / LLM Frontend
**Type:** Self-hosted
**Jurisdiction:** EU-hostable (Open Source)
**Website:** [openwebui.com](https://openwebui.com)

## What It Is

Open WebUI is a highly feature-rich, user-friendly frontend for interacting with Large Language Models (LLMs). It acts as a sovereign alternative to the ChatGPT interface, allowing teams to connect to local backends like **EULLM**, **Ollama**, or remote APIs like **Mistral AI**.

## Good Fit For

- Teams wanting a "ChatGPT-like" experience on their own infrastructure
- Organizations needing fine-grained access control over who can use which AI models
- Securely interacting with internal documents via RAG (Retrieval-Augmented Generation)

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run via Docker Compose on your own EU infrastructure |

## Self-Hosted Setup

### Requirements
- Docker and Docker Compose
- A backend for models (e.g., EULLM or Ollama)

### Docker Compose Example

```yaml
version: "3.8"

services:
  open-webui:
    image: ghcr.io/open-webui/open-webui:main
    restart: unless-stopped
    ports:
      - "3000:8080"
    volumes:
      - ./open-webui-data:/app/backend/data
    environment:
      - OLLAMA_BASE_URL=http://your-eullm-server:11434
      - WEBUI_SECRET_KEY=change-me-long-random-string
```

## Key Features

- **Intuitive UI:** Clean and responsive interface similar to commercial AI chats.
- **Model Management:** Easily switch between different models (Mistral, Llama, Qwen).
- **RAG Support:** Upload PDF/text files and chat with your documents locally.
- **RBAC:** Detailed Role-Based Access Control for users and admins.
- **Multi-modal:** Supports image generation and vision-based models.
- **Tools & Plugins:** Extend functionality with custom python-based tools.

## Compliance Notes

- **Data Sovereignty:** When self-hosted on EU infrastructure, all prompts and document data remain within your control.
- **Privacy:** No tracking or telemetry is sent to external servers by default.
- **GDPR:** As you control the server, you are the data controller for all user interactions.

## EuroDesk Verdict

Open WebUI is the essential "wrapper" that turns raw LLM backends into a professional workspace for non-technical office staff.
