# 🌐 Portfolio Creator Agent (Pure AI Agent)

This project implements an autonomous **Pure AI Agent** architecture for generating personalized, modern, and interactive portfolio websites for users.

The agent gathers personal and professional details step-by-step, persists them into `data.json`, and autonomously writes a complete, state-of-the-art portfolio website into `portfolio/` without requiring external template engines or build scripts.

---

## 📂 Project Structure

```text
agent_partfoly/
├── AGENTS.md                          # Primary agent instructions and behavior rules
├── README.md                          # Project documentation
├── data.json                          # Gathered user profile & skills data
│
└── .agents/
    └── skills/
        ├── get-info/
        │   └── SKILL.md               # Skill 1: Gather user info step-by-step and write data.json
        └── build-portfolio/
            └── SKILL.md               # Skill 2: Read data.json and directly build portfolio/ website
```

---

## 🤖 How the Agent Operates

### 1. Introduction & Greeting
When a user initiates the chat, the agent introduces itself:
> *"Hello! I am a portfolio website builder agent. I can create a personalized portfolio website for you. Shall we begin?"*

### 2. Phase 1: Information Gathering (`get-info` skill)
The agent asks questions strictly one by one in 6 steps:
1. **Full Name:** User's name and title.
2. **Location:** City and country.
3. **Picture:** Profile photo URL or file.
4. **Background / Bio:** Summary of career, interests, and ambitions.
5. **Skills:** Core technical proficiencies and their practical applications.
6. **Contacts:** Telegram, GitHub, Email, LinkedIn handles.

Once confirmed by the user, the data is saved into `data.json`.

### 3. Phase 2: Autonomous Generation (`build-portfolio` skill)
Reading `data.json`, the agent writes three files directly into `portfolio/`:
- `portfolio/index.html` (Semantic, SEO-friendly HTML5)
- `portfolio/style.css` (Dark theme, glassmorphism, glowing accents, responsive CSS)
- `portfolio/script.js` (Toast alerts, clipboard copy, scroll spy)

---

## 🚀 Local Preview

Once the website is generated, preview it in your browser:
```bash
python3 -m http.server 8000 --directory portfolio
```
Open `http://localhost:8000` in any web browser.
