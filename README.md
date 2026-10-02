# Crafty · Artisan Studio Direct Messaging Widget 🪵

> **Direct Seller ↔ Buyer Communication Mini-Widget for Handcrafted & Bespoke Goods**  
> *"Every piece has a heartbeat and an artisan's story." / 每一件手作，都有温度与故事。*

Crafty is a lightweight, responsive communication mini-widget designed specifically for artisanal, handmade, and bespoke e-commerce platforms (such as Atelier Form). 

Rather than an automated bot, Crafty acts as a **direct bridge connecting buyers and independent studio makers**: enabling live consultations on custom monograms, material grain variations, official bespoke quotes, and workbench progress proof snapshots before dispatch.

---

## ✨ Key Features

- **💬 Floating Mini-Widget Form Factor**: Discreet floating launcher docked at bottom-right (`💬 Message Maker / 联系匠人`) with unread badge and active maker status. Opens into a tactile 410px popup chat window.
- **🔄 Dual-Role Testing Toolbar**: Built-in `[👤 Buyer Mode]` ⇋ `[🔨 Maker Mode]` toggle allowing reviewers and developers to easily simulate both sides of the conversation in real time.
- **🏷️ Studio Custom Quotes**: Makers can issue official itemized quotes (e.g. *Keepsake Box $58 + Solid Brass Inlay $10*) directly within the thread with an instant `[Accept Quote]` receipt.
- **📸 Workbench Photo Proofs**: Makers can post progress photos directly from the studio workbench (e.g. *1500-grit progressive sanding & OSMO hardwax-oil curing*) for buyer approval prior to shipment.
- **📦 Order & Product Context**: Contextual header pill binds discussions to specific products or orders (e.g. *Regarding: FAS Black Walnut Dovetail Box #AF-8921*).
- **🎨 Atelier Form Design System**: Built with Atelier Form's tactile color palette (`#F7F2E9` bone canvas, `#FFFDF8` porcelain paper, `#A65427` artisan clay, and `"Iowan Old Style"` editorial serif typography).
- **🌐 Seamless Bilingual Support**: Instant toggling between English and Chinese across all UI components, buttons, and conversation threads.

---

## 📁 Repository Structure

```tree
crafty-chatbot/
├── index.html                  # Interactive live demo (Atelier Form product page + Mini-Widget)
├── css/
│   ├── site.css                # Atelier Form design system tokens, typography & layout
│   └── chatbot.css             # Scoped Seller ↔ Buyer messaging widget styles
├── config.js                   # Studio & maker metadata configuration (gitignored)
├── README.md                   # Project overview & guide
├── docs/
│   └── crafty_chatbot_design.md # Product Requirement Document (PRD) & Architecture
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
python3 -m http.server 8080
```

Then visit [http://localhost:8080](http://localhost:8080).

---

## 👥 How to Test the Dual-Role Interaction

1. Open the widget by clicking the bottom-right **💬 Message Maker** launcher or the **Message Maker · 联系匠人** button on the product page.
2. At the top of the chat window, use the role switcher:
   - Click **👤 Buyer (买家)** to send questions about custom engraving, wood grain, or lead times.
   - Click **🔨 Maker (匠人)** to reply as Master Lin, send an official custom quote card, or share workbench photos.
3. Use the quick chips bar for one-click realistic interactions.
