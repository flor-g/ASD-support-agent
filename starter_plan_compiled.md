# Starter Plan for AS-Support Agent Development

## Phase 0: Setup & Initialization

### 0.1 Project Environment

- [ ] Create a Python virtual environment:
  ```bash
  python -m venv venv
  source venv/bin/activate  # or .\venv\Scripts\activate on Windows
  ```
- [ ] Install required libraries:
  ```bash
  pip install openai flask requests python-dotenv pyttsx3 playwright
  playwright install
  ```
- [ ] Create a `.env` file to securely store API keys and Microsoft credentials
- [ ] Initialize a Git repository and connect it to your GitHub project

### 0.2 Directory Structure

```
neurosupport/
├── main.py
├── config/
│   └── universities/ucl.json
├── modules/
│   ├── email.py
│   ├── moodle.py
│   ├── voice.py
│   ├── calendar.py
│   ├── accommodation.py
├── ui/
│   └── streamlit_app.py (or flask_ui.py)
├── data/
│   └── user_profile.json
├── framework.md
├── README.md
└── .env
```

---

## Phase 1: UCL Email Integration (Outlook + Microsoft Auth)

### Goal

Enable reading and summarizing emails from UCL Outlook inbox.

### Tasks
- [ ] Register an app in the Azure portal to access Microsoft Graph API
- [ ] Set permissions: `Mail.Read`, `Mail.Send`, `offline_access`
- [ ] Create OAuth2 authentication flow with token refresh handling
- [ ] Implement function to fetch unread Outlook emails using Graph API
- [ ] Parse and summarize emails (e.g., from professors, course notices)
- [ ] Optionally use pyttsx3 to read summaries aloud
- [ ] Log and test responses in command line or temporary UI

---

## Phase 2: Voice Interaction Layer

### Goal
Enable basic voice queries like “What emails do I have?” or “What’s due this week?”

### Tasks
- [ ] Install and configure Whisper (or use OpenAI API) for speech-to-text
- [ ] Set up `pyttsx3` or ElevenLabs for text-to-speech
- [ ] Build simple `voice.py` loop to listen, interpret, and respond
- [ ] Design a basic rule-based intent parser
- [ ] Route parsed voice commands to appropriate module (e.g., email, calendar)

---

## Phase 3: Moodle Assignment Scraper (UCL SSO)

### Goal

Automatically log in to UCL Moodle and extract assignments.

### Tasks
- [ ] Use Playwright for browser automation and UCL SSO + Microsoft Authenticator login
- [ ] Extract upcoming assignments from Moodle dashboard (titles, due dates, links)
- [ ] Parse assignment info into structured JSON format
- [ ] Store in local database or forward to task/calendar module

---

## Phase 4: Calendar & Task Integration

### Goal

Convert assignments and appointments into a manageable task list.

### Tasks
- [ ] Sync with Google Calendar API or build local calendar store
- [ ] Implement functions to add/update calendar events from tasks
- [ ] Enable scheduling via voice commands (e.g., “Study tomorrow 3PM”)
- [ ] Handle task rescheduling when overwhelmed

---

## Phase 5: Accommodation Helper

### Goal

Automatically draft and send accommodation or extension requests.

### Tasks
- [ ] Build template system using UCL config (email professor, EC form)
- [ ] Allow user to invoke helper by voice (e.g., “I need an extension for…”)
- [ ] Auto-fill and send emails via Microsoft Graph API
- [ ] Support one-click or one-command full submission

---

## Phase 6: Overload & Neuro-Aware Features

### Goal

Detect signs of executive fatigue or distress and adjust accordingly.

### Tasks
- [ ] Define user symptom profile and preference file (e.g., `user_profile.json`)
- [ ] Build tone modulation engine to adjust responses and pacing
- [ ] Detect overload triggers from task deferral or voice cues
- [ ] Respond with affirmations and initiate wellbeing support flow
- [ ] Enable voice-triggered EC/help email and low-stim mode toggle

---

## Phase 7: Testing & Iteration

### Tasks
- [ ] Create test cases simulating normal, overloaded, and shutdown states
- [ ] Test module interactions and fallback behavior
- [ ] Validate voice-only mode and accessibility flows
- [ ] Add new university configuration to test extensibility

---

## Optional Later

- UI theme picker (voice-only, visual, low-stim)
- Mood check-ins and emotional journaling
- Peer support integration or alerts
- Offline-first capability
