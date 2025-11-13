# ⭐ **AI BasePress**

*A minimal, AI-friendly WordPress starter theme*
**By NicheWorks**

---

## 🚀 Overview

**AI BasePress** is a super-minimal, clean WordPress starter theme designed specifically for:

* Developers who want a **fully predictable, transparent theme structure**
* People who rely on **AI tools (ChatGPT, Claude, etc.)** to extend or customize themes
* Agencies/freelancers looking for a **lightweight base** for client projects

Unlike existing starters (Underscores, Sage, Blockbase, etc.), AI BasePress is intentionally:

* **Small** (only the essential theme files)
* **Flat** (no complicated folder nesting)
* **Unopinionated** about styling or build tools
* **100% readable by AI**, so the model can modify or extend it safely

This makes it ideal for **rapid prototyping**, **theme porting**, and **AI-assisted development**.

---

## 🎯 Goals

1. **Absolute minimalism**
   Only the core WordPress template hierarchy — nothing more.

2. **AI-friendly structure**
   Every file is small, readable, and consistently formatted.

3. **Human-friendly customization**
   Easy to understand, easy to extend.

4. **Zero dependencies**
   No frameworks, no compilers, no tooling required.

5. **Stable base for future growth**
   Optional “plugin-ready edition” may be released later.

---

## 📦 What’s included

AI BasePress contains:

```
ai-basepress/
├─ style.css          ← Theme header + minimal reset
├─ functions.php      ← Clean registration hooks only
├─ index.php          ← Fallback template
├─ header.php
├─ footer.php
├─ sidebar.php
├─ single.php         ← Single post
├─ page.php           ← Page
├─ archive.php        ← Blog/category archive
├─ 404.php
└─ /assets
     ├─ css/          ← Empty (for your custom CSS)
     └─ js/           ← Empty (for your custom JS)
```

No extra CSS frameworks.
No React/Blade/Timber.
No block-theme complexity.
No bloat.

Just **WordPress core + minimum templates required to start building**.

---

## 🧠 Why “AI-Friendly”?

AI BasePress is designed so that AI tools can:

* Understand **every file** without confusion
* Modify templates safely
* Inject layouts or components without breaking theme logic
* Read and rewrite code consistently
* Generate new features reliably

This theme is used as the base in workflows such as:

> “ChatGPT, add a custom post type named `portfolio` and create the archive + single templates.”

> “Rewrite this theme to match this Figma design.”

Because the structure is fixed and simple, AI's success rate becomes dramatically higher.

---

## 🛠️ How to use

### 1. Download the theme

Clone or download this repository:

```
/wp-content/themes/ai-basepress
```

### 2. Activate it in WordPress

WordPress Dashboard → Appearance → Themes → Activate

### 3. Start customizing

Use your editor — or your AI assistant — to:

* Add components
* Create page templates
* Add UI styling
* Integrate plugins
* Build client layouts

AI BasePress guarantees that the AI sees a **predictable, stable environment** every time.

---

## 🔌 Plugin Support (Concept)

The base version intentionally includes **zero plugin-specific code**.

Why?

* Plugins differ wildly
* Many users don’t need all integrations
* Plugin support belongs in **addon versions**, not core

Planned optional editions:

| Edition                                | Purpose                                |
| -------------------------------------- | -------------------------------------- |
| **AI BasePress – Plugin-Ready**        | Pre-styled templates for major plugins |
| **AI BasePress – WooCommerce Edition** | WooCommerce-optimized                  |
| **AI BasePress – Block Theme Edition** | Block-theme compliant version          |

These may be released later depending on demand.

---

## 📘 Documentation

Full documentation (English & Japanese) is available in:

* `/docs/spec-en.md` – Full English specification
* `/docs/spec-ja.md` – Japanese version (for JP users)

---

## 👤 Author

**NicheWorks**
A collection of lightweight, AI-powered utility tools and practical web development resources.

More tools and projects coming soon.

---

## 📝 License

MIT License.

---

## 🤝 Contributions

PRs and issues are welcome.

When submitting code, please:

* Keep files small
* Follow the existing structure
* Avoid adding frameworks or build tools (core edition must stay minimal)

---

## 🌍 Why This Theme Exists

Existing starter themes are powerful but often too large or opinionated.
AI BasePress exists to provide:

* A **stable base** for AI-assisted workflows
* A **clean skeleton** for rapid WordPress development
* A **reliable porting foundation** for future custom themes

If you use AI for WordPress development — this theme is built for you.

---
