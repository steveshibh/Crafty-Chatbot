# Crafty · 匠心小助手 🏺

> **Artisan E-Commerce Concierge for Handcrafted & Bespoke Goods**  
> *"Every piece has a heartbeat and an artisan's story." / 每一件手作，都有温度与故事。*

Crafty is an AI conversational assistant designed specifically for handmade, artisan, and bespoke e-commerce platforms. Unlike transactional retail bots, Crafty acts as a **Warm Apprentice & Knowledgeable Curator**—educating buyers on craft materials, guiding custom bespoke orders, and setting transparent production milestone expectations.

---

## ✨ Key Features

- **🎁 Smart Gift Concierge**: Recommends personalized handmade gifts while automatically checking artisan lead times against the buyer's deadline.
- **✂️ Bespoke Customizer Co-Pilot**: Interactive configurator for materials (Tuscan veg-tanned leather, stoneware pottery), monograms, and finishes. Automatically generates structured tickets for artisan studios.
- **🪵 Milestone Craft Timeline**: Transparent progress tracking across artisan fabrication stages (e.g. *Raw Timber Selected → 1500-Grit Sanding → Hardwax-Oil Curing → Dispatched*).
- **🏺 "Behind the Craft" Storyteller**: Explains natural variations (wood-fired fly ash glazes, leather patina) and proactive material care tips.
- **🌐 100% Seamless Bilingual Support**: Instant toggling between English and Chinese across all UI components and conversational flows.
- **🎨 Warm Artisan Palette**: Built with a tactile color palette (`#f5f2ed` warm off-white/beige canvas and `#4a4238` dark muted ink-brown typography).

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
