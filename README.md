# AI Terminal

**AI-powered mobile operating system for intelligent automation**

AI Terminal is a mobile-first AI platform that orchestrates multiple AI models through voice and text, enabling intelligent automation for individuals and small teams.

## Core Features

- **Multi-Agent Orchestration** — Specialized AI agents with persistent memory, role-based task delegation, and real-time collaboration across sessions
- **Voice-First Interface** — Real-time voice recognition and natural language interaction, designed for hands-free mobile operation
- **Intelligent Automation** — Automated scheduling, health monitoring, cross-device communication, and smart task dispatching
- **Model Flexibility** — Seamlessly switch between cloud models (Claude, GPT, Gemini, DeepSeek) and local models (Ollama) based on task and cost
- **Team Collaboration** — Built-in team engine for multi-agent orchestration with shared context and cross-team communication
- **Secure by Design** — Device-bound authentication, encrypted channels, tiered permissions (L1-L4), and operator privilege controls

## Technology Stack

| Layer | Technology |
|-------|-----------|
| Mobile App | Flutter / Dart (Android & iOS) |
| Backend | Node.js / WebSocket |
| AI Engine | Python, multi-model orchestration |
| Cloud AI | AWS Bedrock (Claude), OpenRouter, DeepSeek |
| Local AI | Ollama (Qwen, LLaMA) |
| Communication | Feishu (Lark) API, IRCS, MCP |

## Architecture

```
┌─────────────────────────────────────┐
│         AI Terminal Mobile App       │
│        (Flutter / Dart)              │
├─────────────────────────────────────┤
│      WebSocket Relay Server          │
│        (Node.js)                     │
├─────────────────────────────────────┤
│       AI Agent Engine                │
│  ┌─────────┬──────────┬───────────┐ │
│  │ Role    │ Team     │ Shared    │ │
│  │ Cards   │ Engine   │ Context   │ │
│  └─────────┴──────────┴───────────┘ │
├─────────────────────────────────────┤
│    Cloud Models  │  Local Models     │
│  (Bedrock/API)   │  (Ollama)         │
└─────────────────────────────────────┘
```

## Status

Active development. Currently in private beta.

## Contact

For inquiries, please reach out via GitHub Issues.
