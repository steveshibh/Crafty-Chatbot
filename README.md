# Crafty · 匠心小助手 🏺

> **Artisan E-Commerce Concierge for Handcrafted & Bespoke Goods**  
> *"Every piece has a heartbeat and an artisan's story." / 每一件手作，都有温度与故事。*

Crafty is an AI conversational assistant designed specifically for handmade, artisan, and bespoke e-commerce platforms. Unlike transactional retail bots, Crafty acts as a **Warm Apprentice & Knowledgeable Curator**—educating buyers on craft materials, guiding custom bespoke orders, and setting transparent production milestone expectations.

---

## ✨ Key Features

- **🤖 Powered by Google Gemini API**: Built-in support for live Gemini models (`gemini-1.5-flash`, `gemini-2.0-flash`, `gemini-1.5-pro`) with Crafty's domain system prompt and multi-turn context memory.
- **🎁 Smart Gift Concierge**: Recommends personalized handmade gifts while automatically checking artisan lead times against the buyer's deadline.
- **✂️ Bespoke Customizer Co-Pilot**: Interactive configurator for materials (Tuscan veg-tanned leather, stoneware pottery), monograms, and finishes. Automatically generates structured tickets for artisan studios.
- **🪵 Milestone Craft Timeline**: Transparent progress tracking across artisan fabrication stages (e.g. *Raw Timber Selected → 1500-Grit Sanding → Hardwax-Oil Curing → Dispatched*).
- **🏺 "Behind the Craft" Storyteller**: Explains natural variations (wood-fired fly ash glazes, leather patina) and proactive material care tips.
- **🌐 100% Seamless Bilingual Support**: Instant toggling between English and Chinese across all UI components and conversational flows.
- **🎨 Warm Artisan Palette**: Built with a tactile color palette (`#f5f2ed` warm off-white/beige canvas and `#4a4238` dark muted ink-brown typography).

---

## 🤖 Connecting the Google Gemini API

Crafty supports real-time conversational intelligence powered by Google Gemini:

1. Obtain a free Gemini API key from [Google AI Studio](https://aistudio.google.com/app/apikey).
2. Open `index.html` (or your GitHub Pages site) in your browser.
3. Click the **⚙️ Gemini 设置 (Settings)** button in the top navigation bar.
4. Paste your API Key and choose your preferred model (e.g., `gemini-1.5-flash`).
5. Click **保存并启用 (Save & Activate)**.

> **Security Note**: Your API key is stored strictly in your browser's private `localStorage` and is never committed to GitHub or sent to any third-party server. When no key is entered, Crafty falls back gracefully to the built-in scenario demo mode.

---

## 📁 Repository Structure

```tree
crafty-chatbot/
├── index.html                  # Interactive live demo (GitHub Pages ready)
├── README.md                   # Project overview & guide
├── docs/
│   └── crafty_chatbot_design.md # Full Product Requirement Document (PRD) & Architecture
└── .gitignore
```

---

## 🚀 Quick Start (Local Preview)

Simply open `index.html` in your web browser:

```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Windows
start index.html
```

Or run a lightweight HTTP server:

```bash
npx serve .
# or
python3 -m http.server 8080
```

---

## 🌐 Deploy to GitHub Pages (Free 1-Click Hosting)

1. Push this repository to GitHub.
2. In your GitHub repository, navigate to **Settings** > **Pages**.
3. Under **Branch**, select `main` (root `/`) and click **Save**.
4. In about a minute, your interactive Crafty prototype will be live at:
   `https://<your-username>.github.io/<repo-name>/`

---

## 📄 Documentation

For full system architecture, entity schemas, tool definitions, and conversation design, check [`docs/crafty_chatbot_design.md`](docs/crafty_chatbot_design.md).

