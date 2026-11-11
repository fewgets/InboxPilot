<!-- InboxPilot · README by Usama Shahid (fewgets) -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,55:0F3D3E,100:36FFC7&height=230&section=header&text=InboxPilot&fontSize=60&fontColor=FFFFFF&fontAlignY=36&desc=AI%20email%20triage%20on%20autopilot%20with%20n8n%20and%20Gemini&descSize=17&descAlignY=58&animation=fadeIn" width="100%" alt="InboxPilot"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=700&color=36FFC7&center=true&vCenter=true&width=720&height=60&lines=Classifies+Every+Email+with+AI;Deletes+Promotions+Automatically;Pings+Discord+for+What+Matters" alt="Typing SVG"/>

<p>
  <img src="https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n"/>
  <img src="https://img.shields.io/badge/Gemini-8E75B2?style=for-the-badge&logo=googlegemini&logoColor=white" alt="Gemini"/>
  <img src="https://img.shields.io/badge/Gmail%20API-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail API"/>
  <img src="https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord"/>
</p>

</div>

---
## 📌 Overview

**InboxPilot** is an **n8n** automation that keeps your Gmail inbox clean on its own. Every
2 minutes it reads new unread emails and asks **Google Gemini** to classify each one:

- 🗑️ **Promotional?** It's **deleted automatically**.
- 🔔 **Anything important?** A short summary (sender, subject, category, reason) is sent to your **Discord** channel.

No more digging through spam to find the OTP, the job reply or the bank alert you actually needed.

---

## ✨ Features

| | Feature |
|:-:|---|
| 📥 | Fetches unread emails from Gmail (OAuth2) |
| 🧠 | AI classification with **Gemini 2.5 Flash-Lite** |
| 🏷️ | 8 categories: `otp`, `security_alert`, `career`, `finance`, `transactional`, `personal`, `promotional`, `other` |
| 🗑️ | Promotional emails deleted automatically |
| 🔔 | Important emails pushed to Discord instantly |
| ⏱️ | Runs every 2 minutes in the background, fully hands-off |

---

## 🔄 Workflow

```mermaid
flowchart LR
    T[⏱️ Schedule<br/>every 2 min] --> G[📥 Gmail<br/>unread emails]
    G --> AI[🧠 Gemini<br/>classify]
    AI --> C{Promotional?}
    C -->|Yes| D[🗑️ Delete email]
    C -->|No| F[📝 Format details]
    F --> DC[🔔 Discord webhook]
```

---

## ⚙️ Setup

### 1. Gmail API (OAuth2)
1. In [Google Cloud Console](https://console.cloud.google.com/), create a project and enable the **Gmail API**.
2. Create **OAuth2 credentials** (web application) with this redirect URI:
   `http://localhost:5678/rest/oauth2-credential/callback` (adjust for your n8n host).
3. In n8n, add a **Gmail OAuth2** credential and authorise your account.

### 2. Google Gemini
1. Create an API key in [Google AI Studio](https://aistudio.google.com/).
2. In n8n, add a **Google Gemini (PaLM)** credential.

### 3. Discord
1. In your server: **Channel Settings → Integrations → Webhooks → New Webhook**.
2. Paste the webhook URL into the workflow's **HTTP Request** node.

### 4. Import and activate
1. In n8n: **Workflows → Import** → `inboxPilot.json`.
2. Connect the three credentials, adjust the schedule if you like, and **activate**.

---

## 🧰 Tech Stack

| Component | Tool |
|---|---|
| Automation | [n8n](https://n8n.io) |
| Email | Gmail API (OAuth2) |
| AI | Google Gemini 2.5 Flash-Lite |
| Notifications | Discord webhooks |

```text
InboxPilot/
├── inboxPilot.json   # n8n workflow export
└── README.md
```

---

## 🤝 Let's Work Together

<div align="center">

**Have an idea, a freelance project, or want to collaborate on something in AI?**
I'm always open to collaborations, freelance work and full-time opportunities.

<a href="mailto:shaikhusama541@gmail.com?subject=Collaboration%20-%20InboxPilot">
  <img src="https://img.shields.io/badge/Email-shaikhusama541%40gmail.com-36FFC7?style=for-the-badge&logo=gmail&logoColor=white&labelColor=0D1117" alt="Email"/>
</a>
<a href="https://www.linkedin.com/in/-usamashahid/">
  <img src="https://img.shields.io/badge/LinkedIn-Usama%20Shahid-36FFC7?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=0D1117" alt="LinkedIn"/>
</a>
<a href="https://github.com/fewgets">
  <img src="https://img.shields.io/badge/GitHub-fewgets-36FFC7?style=for-the-badge&logo=github&logoColor=white&labelColor=0D1117" alt="GitHub"/>
</a>

<br/><br/>

⭐ **If you like this project, please give it a star. It really helps!** ⭐

<br/>

<h3>"Your inbox should work for you, not the other way round."</h3>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:36FFC7,55:0F3D3E,100:0D1117&height=150&section=footer&animation=twinkling" width="100%" alt="footer"/>

</div>
