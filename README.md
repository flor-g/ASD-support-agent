# AS-support Agent (UCL Prototype)

I want to build a modular, privacy-conscious, and neurodivergent-aware AI assistant designed to support autistic university students in managing emails, tasks, coursework, and mental wellbeing. This repository contains the initial system framework and plans for a prototype focused on the University College London (UCL) environment.

---

## 🧠 Project Purpose

This Agent aims to reduce executive load and emotional stress for autistic students by combining:
- Voice-first AI interaction
- Academic email and coursework integration
- Calendar and task management
- Wellbeing-aware pacing and support
- Autonomy-respecting accommodation tools

---

## 📄 Framework Overview

You can find the full design specification in [framework.md](./framework.md), including:

- 🧩 **System architecture and modular breakdown**
- 🏫 **UCL-specific configuration** (Outlook, Moodle, EC process)
- 🎤 **Voice interaction and overload response logic**
- 🛠️ **MVP development roadmap**
- 🧠 **Neurodivergent interaction design and tone modulation**

---

## 🎯 MVP Development Goals

1. Outlook Email Reader via Microsoft Graph API (OAuth + MFA)
2. Moodle Scraper using Playwright (UCL SSO + Microsoft Authenticator)
3. Voice interaction loop (STT, intent parser, TTS)
4. Google Calendar sync with flexible task handling
5. Accommodation support and one-click EC submission
6. Overload detection and wellbeing support engine
7. Modular low-stim UI with voice-only and customizable modes

---

## 🛠 Tech Stack (Planned)

- **Python** (FastAPI or Flask backend)
- **OpenAI Whisper** (Speech recognition)
- **pyttsx3 or ElevenLabs** (Text-to-speech)
- **Microsoft Graph API** (Outlook)
- **Playwright** (Moodle automation)
- **SQLite / JSON config** (local storage)
- **React / Tauri / Streamlit** (for UI, optional)

---

## 🔐 Accessibility & Privacy Principles

- All data is stored and processed locally unless explicitly authorized
- Voice interaction is gentle, affirming, and fully user-controlled
- UI can be customized or hidden based on sensory or emotional needs

---

## 🤝 Contributing

We welcome collaborators, testers, and contributors—especially neurodivergent students and accessibility advocates. If you're interested in helping shape this project, please open an issue or reach out with suggestions.

---

## 📬 Contact

You can open a GitHub Issue or fork the repository to suggest improvements. 

---
