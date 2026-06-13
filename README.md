# 🤖 Automated Social Media Content Scheduling with n8n + AI

> A fully automated personal branding & client acquisition workflow built with n8n, GPT-4o, DALL·E 3, and Telegram — runs twice a week with zero manual trigger.

---

## 📌 What This Workflow Does

This n8n workflow autonomously:

1. **Researches** trending automation topics from the web (Tavily API)
2. **Generates** platform-optimized posts for LinkedIn, Twitter/X, Instagram & Facebook using GPT-4o
3. **Creates** a matching visual using DALL·E 3
4. **Sends a preview** to your Telegram for review
5. **Waits** for your approval before posting anything
6. **Publishes** to all platforms simultaneously via Buffer
7. **Logs** everything to Google Sheets for tracking

---

## 🧠 Content Strategy

| Type | Weight | Purpose |
|------|--------|---------|
| Educational | 40% | Teach automation in simple terms |
| Inspirational | 30% | Real-world results & time saved |
| Case Study / Portfolio | 20% | Show workflows you've built — attracts clients |
| Soft CTA | 10% | Gently invite people to work with you |

---

## 🗓️ Schedule

| Day | Time | Platforms |
|-----|------|-----------|
| Monday | 9:00 AM BST | LinkedIn + Twitter/X |
| Thursday | 9:00 AM BST | Instagram + Facebook |

Timezone: `Asia/Dhaka (UTC+6)`

---

## 🛠️ Tech Stack

- **[n8n](https://n8n.io)** — Workflow automation engine (self-hosted via Docker)
- **[OpenAI GPT-4o](https://openai.com)** — Content generation
- **[DALL·E 3](https://openai.com)** — AI image generation
- **[Tavily API](https://tavily.com)** — Real-time web research
- **[Telegram Bot API](https://core.telegram.org/bots)** — Human-in-the-loop approval
- **[Buffer API](https://buffer.com)** — Multi-platform social publishing
- **[Google Sheets API](https://sheets.google.com)** — Content logging

---

## 📋 Prerequisites

- Docker installed on your machine
- n8n running locally (`docker run -d --restart unless-stopped --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n`)
- API keys for the services listed below

---

## 🔑 Required Environment Variables

Add these to your n8n instance under **Settings → Environment Variables**:

```env
OPENAI_API_KEY=your_openai_key
TAVILY_API_KEY=your_tavily_key
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
TELEGRAM_CHAT_ID=your_chat_id
BUFFER_LINKEDIN_ID=your_buffer_profile_id
BUFFER_TWITTER_ID=your_buffer_profile_id
BUFFER_INSTAGRAM_ID=your_buffer_profile_id
BUFFER_FACEBOOK_ID=your_buffer_profile_id
GOOGLE_SHEET_ID=your_google_sheet_id
```

---

## 🚀 Setup & Installation

### 1. Clone this repository
```bash
git clone https://github.com/YOUR_USERNAME/n8n-social-automation.git
cd n8n-social-automation
```

### 2. Start n8n with Docker
```bash
docker run -d \
  --restart unless-stopped \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

### 3. Open n8n
Go to `http://localhost:5678` in your browser.

### 4. Import the workflow
- Go to **Workflows → Import from File**
- Select `workflow.json` from this repo
- Click **Import**

### 5. Set up credentials in n8n
- Go to **Settings → Credentials**
- Add credentials for: OpenAI, Telegram, Google Sheets, HTTP Header Auth (Buffer)

### 6. Create a Telegram Bot
1. Open Telegram → search `@BotFather`
2. Send `/newbot` and follow the steps
3. Copy your **Bot Token**
4. Get your **Chat ID** via:
```
https://api.telegram.org/bot<YOUR_TOKEN>/getUpdates
```

### 7. Set up Google Sheet
Create a new sheet with these columns:
```
Date | Topic | Content Type | Target Audience | LinkedIn Post |
Twitter Post | Instagram Post | Facebook Post | Image URL |
Platform Post IDs | Status | Notes
```

### 8. Activate the workflow
Toggle the workflow to **Active** in n8n.

---

## 📁 Project Structure

```
n8n-social-automation/
├── workflow.json          # n8n workflow — import this directly
├── README.md              # This file
├── prompt.md              # Full AI system prompt used in the workflow
└── docs/
    └── workflow-diagram.md  # Node-by-node flow explanation
```

---

## 🔄 Workflow Diagram

```
[Schedule Trigger — Mon & Thu 9AM]
           ↓
[Tavily — Research Trending Topics]
           ↓
[GPT-4o — Generate All 4 Platform Posts + Image Prompt]
           ↓
[DALL·E 3 — Generate Visual]
           ↓
[Telegram — Send Full Preview to You]
           ↓
[Wait Node — Pause until your reply]
           ↓
      [IF: "approve"?]
      ↙           ↘
[Publish x4]   [Notify Rejected]
      ↓
[Google Sheets — Log Result]
      ↓
[Telegram — Confirm ✅]
```

---

## 💡 Approval Commands (via Telegram)

| Command | Action |
|---------|--------|
| `approve` | Publishes all posts immediately |
| `edit: [your changes]` | Sends changes back to AI for revision |
| `reject` | Cancels the post, notifies you |

---

## 📊 Google Sheet Log Columns

| Column | Description |
|--------|-------------|
| Date | Post date |
| Topic | Researched topic |
| Content Type | educational / inspirational / case_study / soft_cta |
| Target Audience | developers / business owners / all |
| LinkedIn Post | Generated content |
| Twitter Post | Generated thread |
| Instagram Post | Caption + hashtags |
| Facebook Post | Generated content |
| Image URL | DALL·E generated image |
| Status | published / failed / rejected |

---

## 🎯 Who This Is Built For

This workflow is designed for **Full-Stack Developers** who want to:
- Build a personal brand around automation
- Attract clients who need automation solutions
- Stay consistent on social media without spending hours on content
- Showcase real-world n8n/automation expertise

---

## 🤝 Want This Built for Your Business?

If you're a business owner, agency, or solopreneur who wants a custom automation workflow like this — feel free to reach out!

📩 **monir.shazib@gmail.com**
🌐 **https://nexthiv.com**
💼 **www.linkedin.com/in/md-moniruzzaman-b5709a24a**

---

## 📄 License

MIT License — free to use, modify, and share.

---

⭐ **If this helped you, give it a star on GitHub!**
