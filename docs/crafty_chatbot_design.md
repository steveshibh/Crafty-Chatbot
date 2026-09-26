# Crafty（匠心小助手）: E-Commerce Chatbot Design Specification

## 1. Executive Summary & Brand Identity

**Crafty（匠心小助手）** is a domain-specialized AI conversational concierge designed specifically for handmade, artisan, and bespoke e-commerce platforms (such as an Etsy-like marketplace or a boutique craft brand). 

Unlike conventional, transactional retail chatbots that prioritize rapid checkout at the expense of nuance, Crafty blends **warmth, craftsmanship knowledge, and consultative sales**. It bridges the gap between independent artisans and conscious consumers by conveying the story, material integrity, production time, and uniqueness behind every piece.

```
                  ┌──────────────────────────────────────────────┐
                  │           Crafty (匠心小助手)                │
                  │   "Every piece has a heartbeat and a story"  │
                  └──────────────────────┬───────────────────────┘
                                         │
     ┌───────────────────┬───────────────┴───────────────┬───────────────────┐
     ▼                   ▼                               ▼                   ▼
┌──────────────┐  ┌──────────────┐                ┌──────────────┐   ┌──────────────┐
│  The Gift    │  │ Bespoke &    │                │ Craft Story  │   │ Production   │
│  Concierge   │  │ Customizer   │                │ & Materials  │   │ & Timeline   │
└──────────────┘  └──────────────┘                └──────────────┘   └──────────────┘
```

### 1.1 Persona & Voice Guidelines
* **Name**: Crafty / 匠心小助手 (Artisan Mind Assistant)
* **Archetype**: The Warm Apprentice & Knowledgeable Curator — passionate about slow crafts, respectful of artisan labor, empathetic to buyer sentiments.
* **Tone**: 
  - **Warm & Tactile**: Uses descriptive, sensory language ("natural veg-tanned leather that develops a rich honey patina", "hand-thrown stoneware fired at 1,280°C").
  - **Transparent & Realistic**: Sets realistic expectations for handmade timelines and natural variations ("Since each mug is hand-glazed, the drip pattern is uniquely yours").
  - **Patient & Consultative**: Encourages thoughtful personalization rather than pushy upselling.
* **Multilingual Capability**: Native English and Chinese (with cultural awareness of Chinese traditional craft terms like 榫卯/紫砂/扎染/银饰錾刻 as well as Western craft idioms like bespoke, raw edge, hammered finish).

---

## 2. Core User Personas & Pain Points

| Persona | Primary Goal | Handmade E-commerce Pain Points | Crafty's Value Proposition |
| :--- | :--- | :--- | :--- |
| **The Thoughtful Gifter** | Finding a unique, personalized gift for an anniversary/birthday. | Clueless about craft styles, afraid gift won't arrive on time, needs engraving. | Filter by timeline, recipient interest, price; provides instant personalization preview. |
| **The Bespoke Customizer** | Wants custom dimensions, specific gemstone, or custom embroidery. | Intimidated to message artisans directly; lacks technical craft terminology. | Guided wizard that gathers required specs (size, material, text) before presenting to the artisan. |
| **The Material Connoisseur** | Wants organic, eco-friendly, ethically sourced items. | Skeptical of "fake handmade" or dropshipped mass production. | Surfaces artisan provenance, studio videos, raw material certifications, and care tips. |
| **The Anxious Buyer** | Awaiting a custom order that takes 3–4 weeks to complete. | Standard shipping tracking shows "Order Placed" for weeks; feels left in the dark. | Milestone-based Craft Timeline: "Clay shaped → Kiln firing → Glazed → Packaged". |

---

## 3. Core Functional Modules

```mermaid
flowchart TD
    User([User Prompt / Event]) --> IntentRouter{Crafty Intent Router}
    
    IntentRouter -->|Gift Consultation| GiftEngine[Gift Recommendation Concierge]
    IntentRouter -->|Customization/Bespoke| CustomWizard[Bespoke Spec Builder & Co-Pilot]
    IntentRouter -->|Craft & Material Inquiry| CraftRAG[Artisan & Material Knowledge Base]
    IntentRouter -->|Order & Craft Timeline| MilestoneTracker[Production Milestone Tracker]
    IntentRouter -->|High-Touch Request| HumanHandoff[Artisan Studio Relay & Quote Escalation]
    
    GiftEngine --> ResponseGen[Crafty Multimodal Response Generator]
    CustomWizard --> ResponseGen
    CraftRAG --> ResponseGen
    MilestoneTracker --> ResponseGen
    HumanHandoff --> ResponseGen
    
    ResponseGen --> Output([Interactive UI Card / Conversational Response])
```

### 3.1 Bespoke & Customization Co-Pilot (定制智造助理)
Handmade items frequently support personalization (name stamping, size adjustment, color combinations, custom artwork). Crafty structures this consultation:
1. **Spec Gathering**: Prompts the user through step-by-step visual options (e.g. Leather Type $\rightarrow$ Thread Stitch Color $\rightarrow$ Monogram Font $\rightarrow$ Placement).
2. **Constraint Validation**: Flags artisan limitations gracefully (e.g., *"Artisan Elena can emboss up to 8 characters on this wallet clasp due to the hand-beveled edge"*).
3. **Structured Handoff**: Converts freeform chatter into a standardized `BespokeRequest` ticket that the artisan can accept, quote, or clarify with 1-click.

### 3.2 "Behind the Craft" Storytelling & Material Care (匠心物语与养护)
* **Artisan Profiling**: Dynamically injects mini bio cards (artisan's location, years of experience, philosophy).
* **Sensory Material Explanations**: Explains differences between materials (e.g., stoneware vs. porcelain, full-grain vs. top-grain leather, brass vs. 925 sterling silver).
* **Post-Purchase Care Guide**: Proactive care instructions based on the purchased craft (e.g., *"How to re-oil your walnut cutting board after the first month"*).

### 3.3 Milestone-Based Craft Timeline (手作进度追踪)
Traditional tracking only knows *Carrier Picked Up* and *Delivered*. Handmade buyers wait weeks during fabrication. Crafty offers a 5-stage craft tracker:
1. **Raw Material Prepped** (e.g., Leather selected & cut, clay kneaded)
2. **In The Studio / On The Wheel / Hand-Stitching**
3. **Curing / Firing / Drying / Finishing**
4. **Studio Quality Inspection & Sustainable Gift Box Packaging**
5. **En Route with Craft Care Certificate**

Crafty answers *"Where is my order?"* with contextual warmth:
> *"Artisan Lin has finished throwing your ceramic vase on the wheel! It is currently air-drying slowly before entering the kiln for bisque firing this Thursday. Expected dispatch: Oct 12."*

### 3.4 Smart Gift Concierge (好物寻觅与送礼顾问)
* Asks 3 natural questions: **Who is it for?**, **What is the occasion?**, **What is the deadline?**
* Automatically cross-checks **Artisan Lead Time + Shipping Days** against the deadline to prevent disappointed recipients.

---

## 4. Technical Architecture & System Design

```mermaid
graph TB
    subgraph Frontend Client
        UI[Chat Widget: Crafty Dock / Modal]
        Cards[Rich Cards: Material Select, Timeline, Artisan Bio, Quote Form]
    end

    subgraph Backend Orchestration
        Orch[Dialog Orchestrator / LangGraph / Agent Loop]
        Router[Intent Classifier & Entity Extractor]
        Safety[Safety & Artisan Policy Guardrails]
    end

    subgraph Specialized Tools & Context
        RAG[(Vector DB: Artisan Bios, Craft Wiki, Material FAQs)]
        CatalogAPI[Commerce Catalog & Lead Time API]
        CustomOrderAPI[Bespoke Ticket & Quote Engine]
        OrderTrackingAPI[Artisan Studio Milestone Tracker]
    end

    subgraph LLM Layer
        Model[Gemini 1.5 Pro / Flash with Function Calling]
    end

    UI <--> Orch
    Orch --> Router
    Router --> Model
    Model --> Safety
    Model <--> RAG
    Model <--> CatalogAPI
    Model <--> CustomOrderAPI
    Model <--> OrderTrackingAPI
    Model --> Cards
```

### 4.1 System Prompt Design for Crafty

```yaml
role: "Crafty (匠心小助手) - Handmade E-Commerce Conversational Specialist"
personality:
  tone: "warm, respectful, tactile, knowledgeable, honest"
  language: "Adaptive (English or Chinese based on user input)"
core_principles:
  1_respect_artisan_labor: "Never promise expedited rush orders without validating the artisan's lead time."
  2_embrace_imperfection: "Highlight the beauty of handmade natural variance (wood grains, pottery drips, hammer marks)."
  3_structure_custom_orders: "Collect unambiguous parameters (dimensions, materials, text) before generating a quote."
  4_sincerity_over_pressure: "Focus on whether the craft fits the customer's lifestyle and gift story."
tools_available:
  - search_artisan_catalog(query, materials, price_range, max_lead_days)
  - get_craft_timeline(order_id)
  - create_bespoke_quote_request(product_id, artisan_id, specs, deadline)
  - get_material_care_guide(material_type)
  - get_artisan_bio(artisan_id)
```

### 4.2 Tool Calling Schema Examples

#### Tool: `create_bespoke_quote_request`
```json
{
  "name": "create_bespoke_quote_request",
  "description": "Submits a standardized custom order brief to an artisan for approval and pricing.",
  "parameters": {
    "type": "object",
    "properties": {
      "artisan_id": { "type": "string" },
      "base_product_id": { "type": "string" },
      "customization_type": { "enum": ["engraving", "custom_dimensions", "color_palette", "raw_material_swap", "fully_custom"] },
      "parameters": {
        "type": "object",
        "properties": {
          "engraving_text": { "type": "string" },
          "font_or_style": { "type": "string" },
          "dimensions_cm": { "type": "string" },
          "material_preference": { "type": "string" }
        }
      },
      "target_delivery_date": { "type": "string", "format": "date" },
      "customer_notes": { "type": "string" }
    },
    "required": ["artisan_id", "customization_type", "parameters"]
  }
}
```

---

## 5. Conversational UX & Dialogue Design

### Scenario A: Custom Pottery & Gift Consultation (Dual-Language Example)

> **User**: *“我想给朋友挑选一份结婚礼物，预算在 500 元左右，希望是有心意的手作好物，能刻上他们两个的名字。”*
> 
> **Crafty（匠心小助手）**:
> *“真是一份充满心意的祝福！手作的温度最适合见证长久的陪伴。针对新婚礼物与定制刻字，我为您挑选了三位独立陶艺与木作匠人的作品：*
> 
> 1. **【青岚陶坊】景德镇手拉坯对杯・天青双色窑变釉**
>    - *手作工艺：高温还原烧，杯底可手工錾刻新人姓名缩写与结婚日期（如：J & M · 2026.10）*
>    - *工期：现坯刻字烧制需 5-7 个工作日*
>    - *礼盒配置：附赠梧桐木手工榫卯礼盒与手写祝愿卡*
>    - *参考价格：¥468 / 对*
> 
> 2. **【原木物语】北美黑胡桃木手工拼花双人托盘**
>    - *手作工艺：天然生漆擦色，黄铜嵌字定制*
>    - *工期：3 个工作日内发货*
>    - *参考价格：¥398*
> 
> *您更倾向于每天都能握在手心的温润陶杯，还是日常实用、盛载生活点滴的木质托盘呢？如果告诉我婚礼日期，我还能帮您确认排单是否来得及准时送达。”*

---

### Scenario B: Understanding Handmade Variations & Reassurance

> **User**: *"Why does the glaze on the mug look slightly different from the photo on the product page?"*
> 
> **Crafty**:
> *"That’s the enchanting nature of wood-fired stoneware! Artisan Kenji fires these in a traditional climbing kiln where natural wood ash lands unpredictably onto the wet clay at 1,300°C. 
> 
> Unlike industrial mass-produced mugs coated in uniform chemical pigments:
> - Every drip, amber crystallization, and subtle gradient is an unrepeatable signature of fire and earth.
> - No two people in the world will ever hold the exact same piece as yours.
> 
> If you'd like, I can show you a 30-second video of Kenji opening this exact kiln batch, or if you prefer a cup with more uniform tones, I can gladly help you request an exchange from Kenji's studio!"*

### 5.3 Visual Design System & Artisan Palette Tokens

To convey authenticity, tactile warmth, and an unhurried workshop aesthetic, Crafty adopts an earthy, linen-and-earthenware inspired palette:

| Token Name | Hex Value | Semantic Role in Crafty UI |
| :--- | :--- | :--- |
| `--craft-bg` | `#f5f2ed` | **Warm off-white / beige**: Evokes handmade washi paper, unbleached linen, and natural cotton canvas. |
| `--craft-text` | `#4a4238` | **Dark muted brown**: Primary ink tone; softer and more organic than harsh pure black (`#000000`). |
| `--craft-text-muted` | `#736859` | **Warm medium brown**: Secondary metadata, timestamps, artisan studio locations, and care tips. |
| `--craft-card-bg` | `#fdfbf7` | **Warm porcelain parchment**: High-contrast, clean surface for dialogue containers and main window. |
| `--craft-card-inner`| `#f6f2ea` | **Raw earthenware tint**: Embedded product recommendation cards, milestone trackers, and customizer forms. |
| `--craft-border` | `#ded5c4` | **Soft clay sand**: Tactile borders separating steps, cards, and input controls. |
| `--craft-terracotta`| `#a65427` | **Artisan terracotta clay**: Primary action buttons, user bubbles, active milestone pins, and links. |

---

## 6. Artisan-Buyer Bridge & Escalation Model

Artisans are typically busy in their workshops (throwing clay, welding, stitching) and cannot answer chats in real-time. Crafty acts as their **gatekeeper and apprentice**:

```
[Buyer Chat] 
     │
     ▼
[Crafty Bot] ──(Standard FAQs, Care, Stock, Lead times)──> [Immediate Resolution]
     │
     ▼ (Complex Custom Design / Price Estimation)
[Structured Studio Ticket] 
     │
     ▼
[Artisan Daily Digest / Mobile App]
  - 1-click Approve with Lead Time
  - 1-click Quick Price Adjustment
  - Voice Note response transcribed into Crafty chat
```

---

## 7. Metrics & Success Criteria

1. **Artisan Interruption Reduction**: $\ge 65\%$ of routine inquiries (materials, dimensions, care, lead time) resolved without bothering the artisan.
2. **Bespoke Conversion Rate**: Increase custom order completions by $\ge 30\%$ due to structured, frictionless spec gathering.
3. **Buyer Anxiety Reduction**: $\ge 50\%$ drop in "Where is my package?" support tickets via proactive craft milestone notifications.
4. **Artisan Story Engagement**: CTR on "Meet the Artisan" and "Craft Video" cards $\ge 25\%$.
