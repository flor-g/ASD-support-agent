# AS-Support Agent: Framework Document (UCL Configuration)

## 1. Purpose

This agent is an assistive AI system designed for autistic college students to help manage academic workload, communications, and mental wellbeing. It combines natural voice interaction with email, calendar, coursework, and accommodation support, while maintaining flexibility to adapt to different universities.

---

## 2. Core Design Principles

- **Cognitive Accessibility**: Minimalist interface, single-task focus
- **Voice-First Interaction**: Natural conversation via STT/TTS
- **Modularity**: Independent modules for email, calendar, coursework, etc.
- **Adaptability**: Configurable for different universities
- **Privacy & Consent**: All data stored locally unless explicitly authorized
- **Neurodivergent-Sensitive Design**: Respect for hypersensitivity, pathological demand avoidance (PDA), executive dysfunction, and emotional regulation needs

---

## 3. Functional Modules

### A. Voice Interaction Layer

- Speech-to-Text (STT): OpenAI Whisper / local alternative
- Intent Parser: GPT-4 function-calling or custom intent router
- Text-to-Speech (TTS): pyttsx3 / ElevenLabs

### B. Email Assistant

- Outlook 365 via Microsoft Graph API
- OAuth2 login with Microsoft Authenticator (MFA)
- Reads, summarizes, and suggests replies to academic emails

### C. Calendar and Task Manager

- Syncs with Google Calendar or iCal
- Handles voice-driven scheduling
- Reschedules and prioritizes tasks based on wellbeing input

### D. Coursework Connector (UCL Moodle)

- Automates login via Playwright with Microsoft Authenticator
- Scrapes Moodle dashboard for assignments and announcements
- Adds tasks to calendar and tracker

### E. Accommodation Support

- Per-university configuration for accommodation routing
- For UCL:
  - Direct professor email template
  - Extenuating Circumstances (EC) form portal
- System adapts based on course-specific overrides

### F. Overload Detection & Wellbeing Monitor

- Triggers from speech, task deferrals, or check-ins
- Activates "Low-Stim Mode"
- Offers to send accommodation requests
- Re-plans weekly workload
- Provides quick access to university wellbeing services
  - For UCL: prompts to contact Student Support and Wellbeing (SSW)
  - Offers draft emails or opens relevant booking/request portals
  - Enables one-click completion of all related actions (e.g., send email, submit EC form, log calendar update)
  - Responds to phrases like "I need help" or "I’m not okay" with grounding responses and support options
- Entire support flow can be triggered and completed via voice instruction (e.g., "Tell SSW I need help and submit an EC")
- User interface is minimalist by default with optional low-stimulation design
- UI includes customizable modules and one-tap support trigger for wellbeing access
  ### G. Neurodivergent Interaction & Safety Layer
- **Tone Modulation Engine**: Adjusts voice/text output based on emotional state
- **Low-Stim UI Mode**: Minimizes cognitive load via quiet audio and visual design
- **Pathological Demand Avoidance Support**: Avoids imperatives, always offers choices
- **Executive Dysfunction Handling**: Supports microtasking and action scaffolding
- **Personalized Symptom Profiles**: Stores preferences like sensory sensitivity, pacing, and avoidance cues
- **Emotion-Aware Suggestions**: Provides affirming, autonomy-respecting phrasing during overwhelm

---

## 4. University Configuration: UCL Example

```json
{
  "university_name": "UCL",
  "email_system": "outlook",
  "email_auth": {
    "method": "oauth2",
    "provider": "microsoft",
    "token_endpoint": "https://login.microsoftonline.com/common/oauth2/v2.0/token",
    "scopes": ["https://graph.microsoft.com/Mail.Read", "Mail.Send", "offline_access"]
  },
  "coursework_platform": {
    "type": "moodle",
    "url": "https://moodle.ucl.ac.uk",
    "login_method": "ucl_sso_with_mfa"
  },
  "accommodation_routes": [
    {
      "method": "email_professor",
      "template": "Dear [Professor], I’m currently experiencing difficulty managing my workload and would like to request a short extension for the assignment due on [date]..."
    },
    {
      "method": "ucl_ec_portal",
      "form_url": "https://www.ucl.ac.uk/students/disability-support/extenuating-circumstances",
      "requires_login": true
    }
  ]
}
```

---

## 5. System Architecture

```
User (Voice/Text)
  ↓
[Voice Module: STT → Intent Parser → TTS]
  ↓
[Core Agent Logic]
  ↓        ↓         ↓         ↓        ↓         ↓
Tasks   Calendar   Email   Coursework  Wellbeing  NeuroTone
                                ↓
                       [University Config Loader]
```

---

## 6. Extensibility

- All institution-specific logic is abstracted into `/config/universities/{school}.json`
- Modular API connectors for Gmail, Outlook, Canvas, Moodle
- Add new universities by creating a config file and tweaking the login/portal logic
- UI supports user-customizable module layout (e.g., toggle visibility of Email, Tasks, Accommodations)
- UI themes support low-stim, dark/light, or voice-only modes
- All task flows—including accommodation requests, portal actions, and follow-ups—are automatable via voice command---

## 7. MVP Development Roadmap

1. Outlook Email Reader via Microsoft Graph
2. Moodle Assignment Scraper via Playwright
3. Voice Interface (Whisper + pyttsx3)
4. Task & Calendar Sync (Google Calendar)
5. Accommodation Helper + EC Draft Tool
6. Overload Trigger + Replanning Module
7. Neuro-Aware Tone Modulation + UI Pacing

---

## 8. Summary

This framework supports the development of a flexible, respectful, and empowering assistant for autistic students. The UCL configuration serves as a prototype, and the system architecture ensures that future expansion to other institutions is seamless. The neuro-aware communication layer ensures that all interactions respect cognitive overload thresholds, demand avoidance triggers, and emotional safety.

