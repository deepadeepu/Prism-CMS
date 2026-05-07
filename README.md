# 🟣 Prism CMS — Content Management Platform

> A fully interactive Content Management System dashboard built as a portfolio project to demonstrate Product Owner skills across editorial workflow design, content lifecycle management, analytics strategy, and UX decision-making.


## 🧭 Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Modules](#modules)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [File Structure](#file-structure)
- [Product Design Decisions](#product-design-decisions)
- [User Personas](#user-personas)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

---

## 📖 About the Project

**Prism CMS** is a single-file, fully interactive content management system dashboard designed to simulate a real enterprise editorial platform. It was built as a **Product Owner portfolio project** to demonstrate:

- Content lifecycle management from draft to publish
- Multi-stage editorial workflow with approval queues
- Analytics-driven content strategy tooling
- Digital asset management (DAM)
- Role-based team collaboration features

The project showcases the product thinking behind a real CMS — not just how it looks, but **why each design decision was made** from a PO perspective.

---

## ✨ Features

| Feature | Description |
|---|---|
| 📊 **Live Dashboard** | Real-time KPI cards, team activity feed, traffic channel breakdown |
| 📝 **Content Library** | Filterable, searchable content table with SEO scores and status pills |
| 🔁 **Editorial Workflow** | Kanban board with 5 pipeline stages and colour-coded urgency |
| ✅ **Approval Queue** | Structured review queue with one-click Approve / Decline actions |
| 📁 **Media Library** | Asset grid with file metadata, type filters, and upload prompt |
| 📈 **Analytics** | Top content performance, channel breakdown, SEO health, audience split |
| ✏️ **Content Editor** | Rich toolbar, publish settings, SEO metadata panel, featured image |
| 🔔 **Toast Notifications** | Action feedback on approve, decline, save, and publish |
| 🧭 **Full Navigation** | Sidebar + tab-based routing between all modules |

---

## 🗂 Modules

### 1 · Dashboard
The command centre. Surfaces the four most important operational KPIs at a glance:

- **Total Content** — volume across all content types
- **Published Today** — daily publishing velocity
- **Pending Review** — queue health indicator
- **Team Members** — active capacity

Also includes a traffic-by-channel bar chart, a truncated review queue, and a full team activity feed.

---

### 2 · Content Library
A filterable, searchable table of all content in the system. Each row shows:

- Content title and word count
- Content type (Article, Guide, Report, Template, Email, Docs)
- Status pill (Published / Draft / In Review / Scheduled)
- Author, view count, SEO score bar, and last-updated timestamp

**Product decision:** SEO score uses a colour-coded progress bar (green > 89, amber > 74, red below) so writers can self-serve quality feedback without opening each item.

---

### 3 · Editorial Workflow
A five-stage Kanban board modelling the full editorial pipeline:

```
Drafting → In Review → Approved → Scheduled → Published
```

Each card shows the content title, author, and an urgency dot:
- 🔴 **High** — time-sensitive; breaking news or campaign deadline
- 🟡 **Medium** — upcoming deadline within 48 hours
- 🟢 **Low** — evergreen; no time pressure

Below the Kanban, an **Approval Queue** surfaces pending items with Approve and Decline actions side-by-side.

---

### 4 · Media Library
A DAM (Digital Asset Management) grid of all uploaded assets. Features:

- Filter by file type (PNG, JPG, PDF, MP4, SVG)
- Sort by recent, name, or size
- Per-asset metadata: filename, file size
- Storage quota display (4.2 GB / 10 GB)

---

### 5 · Analytics
Performance visibility across all content:

- **Page views, unique visitors, avg. time on page, bounce rate** — with month-over-month deltas
- **Top performing content table** — views, average time, CTR, and status
- **Content-by-type bar chart** — relative distribution across types
- **SEO health checklist** — optimised pages, missing metadata, broken links, Core Web Vitals status
- **Audience split** — new vs returning, mobile vs desktop

---

### 6 · Content Editor
A full creation environment for new content:

- Rich text toolbar (Bold, Italic, Headings, Lists, Links, Tables, Code, Quotes)
- Publish settings panel (status, author, content type, category, date)
- SEO metadata panel (meta title, description, focus keyword, tags)
- Live SEO preview showing how the content will appear in search results
- Featured image upload zone

---

## 🛠 Tech Stack

This project is intentionally **zero-dependency** — a deliberate product decision to make it maximally portable.

| Layer | Choice | Reason |
|---|---|---|
| Markup | HTML5 | Semantic, accessible, universal |
| Styling | CSS3 (custom properties) | No build step; themeable via CSS vars |
| Interactivity | Vanilla JavaScript (ES6+) | No framework dependency; instant load |
| Fonts | Google Fonts (DM Sans + Instrument Serif) | CDN-loaded; fallback-safe |
| Distribution | Single `.html` file | Open in any browser; email-safe |

**No React. No Vue. No build pipeline. No npm install.**




## 📁 File Structure

```
prism-cms/
│
├── prism-cms.html          # Complete application — single file
├── README.md               # This file
└── assets/                 # (optional) screenshots for README
    ├── dashboard.png
    ├── workflow.png
    └── analytics.png
```

The entire application — HTML, CSS, and JavaScript — lives in `prism-cms.html`. This is intentional: the project is designed to be shared as a single file, opened on any machine, and run without any setup.

---

## 🧠 Product Design Decisions

These are the kinds of decisions a Product Owner explains in interviews. Each one has a rationale.

### ① Status as a State Machine
Content status (Draft → In Review → Approved → Scheduled → Published) is not just a label — it is a **workflow state**. Transitioning between states:
- Moves the item in the Kanban board
- Triggers the appropriate action for the appropriate person
- Locks or unlocks editing permissions by role

This pattern prevents content from existing in ambiguous states that no-one owns.

---

### ② Urgency Dots Over Full Labels
Review queue items use a small colour dot (red / amber / green) rather than a full text label. This was a deliberate **cognitive load reduction** decision: reviewers can triage a queue of 20 items in seconds without opening each one.

---

### ③ SEO Score Inline in the Content Table
SEO scores are surfaced in the content library table — not buried in a separate SEO tool. The product decision: writers should encounter quality feedback in their daily workflow, not only when they remember to check a separate panel.

---

### ④ Approval Queue as Two-Action Minimum
Each queue item has exactly two actions: **Approve** or **Decline**. No ambiguous "Maybe", no "Send back for more info" without a decision. This forces a clear handoff and prevents content from stalling in an undefined state.

---

### ⑤ Analytics Tied to Content — Not Separate
Analytics are not a standalone reporting tool — they are linked directly to the content that drives them. A top-performing content table shows which items drive traffic, so editors can replicate what works. This connects **output** (publishing) to **outcome** (traffic and engagement).

---

## 👥 User Personas

| Persona | Primary Module | Key Goal |
|---|---|---|
| **Content Writer** | Editor, Content Library | Draft and submit content efficiently |
| **Editor / Reviewer** | Workflow, Approval Queue | Review and approve content quickly |
| **Content Manager** | Dashboard, Analytics | Visibility into team output and performance |
| **SEO Specialist** | Analytics, Content Library | Identify and fix SEO gaps at scale |
| **Product Owner** | All modules | Ensure the system delivers on content strategy OKRs |
| **C-Suite** | Dashboard | High-level publishing and performance KPIs |

---

## 🗺 Roadmap

### ✅ MVP (Current)
- [x] Dashboard with KPI cards and activity feed
- [x] Content library with filter, search, and SEO scores
- [x] Kanban workflow with 5 stages
- [x] Approval queue with Approve / Decline
- [x] Media library with asset grid
- [x] Analytics with top content and SEO health
- [x] Content editor with SEO panel

### 🔜 Phase 2 — Collaboration
- [ ] Inline commenting on content drafts
- [ ] @mention notifications for reviewers
- [ ] Real-time co-editing indicator
- [ ] Version history and diff view

### 🔜 Phase 3 — Integrations
- [ ] REST API for headless content delivery
- [ ] Webhook triggers on status change
- [ ] Google Analytics / GA4 data import
- [ ] Email newsletter integration (Mailchimp, Klaviyo)
- [ ] Social scheduling (Buffer, Hootsuite)

### 🔜 Phase 4 — Intelligence
- [ ] AI-assisted meta description generation
- [ ] Content gap analysis from keyword data
- [ ] Predictive performance scoring before publish
- [ ] Automated content audit and debt flagging

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome.



## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---


## ⭐ If this project helped you

Give it a star on GitHub — it helps other Product Owners find it.

---

<p align="center">Built with product thinking first, code second.</p>
