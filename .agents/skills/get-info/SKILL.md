---
name: get-info
description: >-
  Use this skill to gather user personal and professional details step-by-step (Full Name, Location, Picture, Bio, Skills, Contacts) and persist them into data.json for portfolio creation.
---

# Get Info Skill (`get-info`)

This skill guides the agent to collect all required personal and professional information from the user in a strict step-by-step manner and save the structured data into `data.json`.

---

## 1. Core Rules
1. **Strict Step-by-Step Flow:**
   - Do NOT ask multiple questions in a single turn.
   - Ask exactly one question at a time and wait for the user's response.
2. **Encouraging & Professional Tone:**
   - Acknowledge each response positively before moving to the next question (e.g., *"Awesome! Let's move on to the next step..."*).
3. **Graceful Fallbacks:**
   - If the user does not have a photo or a particular social link, offer placeholders or let them skip.

---

## 2. Information Gathering Steps

### Step 1: Full Name
- **Prompt:** User's full name (and title/role if desired).
- **Example:** *"Step 1: What is your full name? (e.g., John Doe)."*

### Step 2: Location
- **Prompt:** City and country where they are based.
- **Example:** *"Step 2: Where are you located? (e.g., Samarkand, Uzbekistan or London, UK)."*

### Step 3: Profile Picture
- **Prompt:** URL or local file path to their profile picture.
- **Note:** If the user skips or has no picture, leave it completely empty (`"avatar": ""`). Do NOT insert third-party stock photos or random images.
- **Example:** *"Step 3: Please provide a URL or file path for your profile photo. (If you don't have one or prefer not to show a photo, reply with 'Skip' and we will leave it empty)."*

### Step 4: Background / Bio
- **Prompt:** Brief summary of who they are, what they do, their key focus and ambitions (in the spirit of an agent.me profile bio).
- **Example:** *"Step 4: Please share a brief bio or background story. What are your core areas of expertise, what drives you, and what are you working on?"*

### Step 5: Skills & Descriptions
- **Prompt:** Key technologies, programming languages, or tools they specialize in, along with how they apply them in practice.
- **Example:** *"Step 5: What are your key technical skills? For each skill, feel free to include a short description of how you use it (e.g., TypeScript - frontend & React apps; Python - backend APIs & AI; Docker - containerization)."*

### Step 6: Contacts
- **Prompt:** Contact channels and social media profiles:
  - Telegram (e.g., `@username` or `https://t.me/username`)
  - GitHub (e.g., `https://github.com/username`)
  - Email (e.g., `user@example.com`)
  - LinkedIn (e.g., `https://linkedin.com/in/username`)
- **Example:** *"Step 6 (final step): Please share your contact links (Telegram, GitHub, Email, LinkedIn)."*

---

## 3. Review, Confirmation & Saving to `data.json`

After all 6 steps are answered:
1. Present a neat summary list of all collected details to the user.
2. Ask the user to confirm if the details look accurate.
3. Upon confirmation, save the structured JSON into `data.json` at the root directory following this schema:

```json
{
  "personal": {
    "fullName": "John Doe",
    "title": "Full-Stack Developer & AI Engineer",
    "location": "Samarkand, Uzbekistan",
    "avatar": "https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=600&q=80",
    "bio": "Passionate software engineer building modern web applications and AI-driven systems."
  },
  "skills": [
    {
      "name": "JavaScript / TypeScript",
      "level": "Advanced",
      "description": "Crafting interactive user experiences with React and Next.js"
    },
    {
      "name": "Python",
      "level": "Advanced",
      "description": "Building performant backend APIs, FastAPI, and AI integration pipelines"
    },
    {
      "name": "UI/UX Design & CSS",
      "level": "Experienced",
      "description": "Responsive layouts, micro-animations, and modern glassmorphism aesthetics"
    }
  ],
  "contacts": {
    "telegram": "https://t.me/johndoe",
    "github": "https://github.com/johndoe",
    "email": "john.doe@example.com",
    "linkedin": "https://linkedin.com/in/johndoe"
  },
  "metadata": {
    "createdAt": "2026-10-08T22:00:00Z",
    "status": "ready_for_generation"
  }
}
```

4. Once `data.json` is successfully written, transition immediately to the `build-portfolio` skill to generate the website!
