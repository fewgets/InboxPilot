

# 📬 InboxPilot - Smart Email Classifier & Cleaner (n8n + Gemini AI)

> **InboxPilot** is an automation workflow built in **n8n** that uses **Google Gemini AI** to classify incoming Gmail messages, automatically delete unwanted promotional emails, and forward important email details to **Discord** for instant notifications.

---

## 📌 Project Summary

InboxPilot connects to Gmail, scans unread messages, and passes them to Google Gemini for classification. Emails are categorized into **otp, security\_alert, career, finance, transactional, personal, promotional, other**.

* If classified as **promotional** → the email is automatically deleted.
* Otherwise → a notification with details (sender, subject, reason) is sent to a **Discord channel**.

This workflow runs every **2 minutes** via a schedule trigger, keeping your inbox clean and important messages visible.

---

## ⚙️ Features

* 📥 **Fetch Unread Emails** from Gmail
* 🧠 **AI-Powered Classification** using Google Gemini
* 🗑 **Auto-Delete Promotional Emails**
* 🔔 **Discord Notifications** for important emails
* ⏳ **Scheduled Execution** every 2 minutes
* ⚡ 100% Automated, runs in the background

---

## 🧰 Tech Stack

| Component         | Tool / Service        |
| ----------------- | --------------------- |
| Automation Engine | [n8n](https://n8n.io) |
| Email Service     | Gmail (OAuth2)        |
| AI Classifier     | Google Gemini (PaLM)  |
| Notifications     | Discord Webhook       |

---

## 🗂 Folder Structure

```bash
InboxPilot/
├── inboxPilot.json     # n8n workflow export
└── README.md           # Documentation
```

---

## 📝 Setup Instructions

### 1) Gmail API (OAuth2)

1. Go to [Google Cloud Console](https://console.cloud.google.com/).
2. Create a project → Enable **Gmail API**.
3. Create **OAuth2 credentials** (Web app).
4. Add redirect URI for n8n:

   ```
   http://localhost:5678/rest/oauth2-credential/callback
   ```

   *(Adjust for your n8n host/port)*
5. In n8n, create **Gmail OAuth2 credential** with your Client ID & Secret.
6. Connect and authorize with your Gmail account.

---

### 2) Google Gemini (AI Model)

1. Get API access for [Google AI Studio](https://aistudio.google.com/).
2. Create an API key.
3. In n8n, add a new credential: **Google Gemini (PaLM)**.
4. The workflow uses `gemini-2.5-flash-lite` model for classification.

---

### 3) Discord Webhook

1. Open your Discord server → Go to channel settings → **Integrations → Webhooks**.
2. Create a webhook and copy the URL.
3. In workflow, update the **HTTP Request** node with your webhook URL.

---

### 4) n8n Workflow Setup

1. Import `inboxPilot.json` into your n8n instance.
2. Configure all credentials: Gmail, Gemini, Discord.
3. Adjust schedule trigger interval if needed (default: every 2 minutes).
4. Activate the workflow.

---

## 🚀 How It Works

1. **Trigger:** Runs every 2 minutes.
2. **Fetch Emails:** Gets the latest unread Gmail message.
3. **AI Classification:** Gemini assigns category (otp, finance, promotional, etc.).
4. **Logic Check:**

   * If `promotional` → Email is deleted.
   * Otherwise → Email details are formatted.
5. **Notification:** Sends details to Discord webhook.

---

## 📩 Contact

👤 **Usama Shahid**
📧 Email: [dev.usamashahid@gmail.com](mailto:dev.usamashahid@gmail.com)

🔗 LinkedIn: [linkedin.com/in/-usamashahid](https://linkedin.com/in/-usamashahid)

🐙 GitHub: [github.com/fewgets](https://github.com/fewgets)


---

## 📜 License

This project is for personal productivity and research use. Feel free to fork and adapt, but please credit the author 🙏
