# 📘 **AI BasePress – Official Specification (v1.0)**

**Status:** Stable (v1.0)
**Audience:** Developers, AI-assisted builders, WordPress customizers
**License:** MIT
**Language:** **English (official)** — Japanese translation provided separately

---

# 1. Overview

**AI BasePress** is a minimal, fully AI-optimized WordPress starter theme designed for:

* Converting static HTML/CSS sites into WordPress
* Creating lightweight custom themes from scratch
* Building WordPress sites *with* or *through* AI tools (GPT, Claude, Gemini, etc.)
* Avoiding the complexity and bloat of existing multipurpose themes
* Ensuring the entire theme structure is understandable by both humans and AI models

AI BasePress intentionally includes **no plugin dependencies**,
**no heavy styling**, and **no complex logic**.

It is a **clean foundation** — a “true base theme” — built for clarity, extensibility, and AI-drivenness.

---

# 2. Project Goals

### 2.1 Core Goals

* Provide the **cleanest possible WordPress theme structure**
* Ensure **100% comprehension by LLMs**
* Enable developers to quickly model or modify the theme via AI
* Allow pain-free customization without breaking other plugins
* Offer a predictable structure for WordPress migration projects

### 2.2 Non-Goals

* AI BasePress is **not** a design framework
* **Not** a multipurpose theme
* **Not** a theme builder
* **Not** a WooCommerce theme
* **Not** intended to include large scripts, animations, or design systems

---

# 3. Philosophy: “AI-Optimized Minimalism”

AI BasePress follows five principles:

1. **Single Responsibility**
   Each file does exactly one job.

2. **Shallow Structure**
   No deep include chains; AI can read everything in one scan.

3. **Semantic Naming**
   Class and file names clearly express their purpose.

4. **Predictable HTML Layout**
   Identical scaffolding in every template for consistent reasoning.

5. **Non-Intrusive Styling**
   Styling never overrides plugin output; everything is scoped to `.entry-content`.

---

# 4. Directory Structure (v1.0)

```
ai-basepress/
│
├── style.css                     ← Theme header + minimal base styling
├── functions.php                 ← Theme setup + asset loading
│
├── header.php                    ← Document head + header layout
├── footer.php                    ← Footer + wp_footer()
├── sidebar.php                   ← Optional widget sidebar
│
├── index.php                     ← Main loop fallback
├── page.php                      ← Static page template
├── single.php                    ← Single post
├── 404.php                       ← Not-found page
│
├── /assets/
│    ├── /css/
│    │     └── base.css           ← Core typography & layout CSS
│    └── /js/
│          └── main.js            ← Minimal JS (optional)
│
└── /templates/                   ← Future partials (kept minimal for v1.0)
```

---

# 5. Theme Setup (functions.php)

AI BasePress registers only the **essential WordPress supports**:

* `title-tag`
* `post-thumbnails`
* `html5` (gallery, caption, forms, comment-list)
* One menu location (`primary`)
* One widget area (`sidebar-1`)

Assets loaded:

* `style.css`
* `assets/css/base.css`
* `assets/js/main.js` (optional)

No additional frameworks, libraries, or dependencies.

---

# 6. HTML Structure

Every template follows the same global structure:

```html
<body class="site-body">
  <div class="site-wrapper">

    <header class="site-header">
      <!-- Branding / Navigation -->
    </header>

    <div class="site-main-wrapper">
      <main class="site-main">
        <!-- Template-specific content -->
      </main>

      <aside class="site-sidebar" role="complementary">
        <?php get_sidebar(); ?>
      </aside>
    </div>

    <footer class="site-footer">
      <!-- Footer content -->
    </footer>

  </div>
</body>
```

### Key Principles:

* `.site-main` always contains the core content.
* `.entry-content` wraps all WordPress-generated content.
* Plugins output content inside `.entry-content` without conflict.
* No unnecessary wrappers, utility classes, or grid systems.

---

# 7. Template Structure Requirements

### 7.1 `page.php` and `single.php`

Both follow this format:

```html
<article id="post-<?php the_ID(); ?>" <?php post_class('entry'); ?>>
  <header class="entry-header">
    <h1 class="entry-title"><?php the_title(); ?></h1>
  </header>

  <div class="entry-content">
    <?php the_content(); ?>
  </div>
</article>
```

### Important:

* `.entry-content` acts as the “plugin safety zone”
* All block editor output, shortcodes, and plugin HTML render inside it
* Styling is scoped so plugins are not overridden

---

# 8. CSS Guidelines

### 8.1 Base Styling Philosophy

* Keep `style.css` minimal (theme meta + very small defaults)
* All real styling in `assets/css/base.css`
* Never override plugin styles globally
* Scope all element design to `.entry-content`:

Examples:

```css
.entry-content h2 { ... }
.entry-content p { ... }
.entry-content table { ... }
.entry-content blockquote { ... }
```

### 8.2 Naming Conventions (BEM-inspired)

Layout blocks:

* `.site-header`
* `.site-main`
* `.site-footer`

Content blocks:

* `.entry`
* `.entry__title`
* `.entry__content`

Reusable helpers:

* `.section`
* `.section--narrow`
* `.section--inverted`

---

# 9. JavaScript Guidelines

### 9.1 Principles

* JavaScript is optional
* JS file included but minimal
* No frameworks (React, Vue, Alpine, jQuery etc.)
* Only tiny behaviors allowed (e.g., mobile menu toggle)

---

# 10. Plugin Policy (Critical Specification)

AI BasePress v1.0 declares:

### ❌ No plugin dependencies

### ❌ No plugin-specific CSS

### ❌ No plugin-specific JS

### ❌ No WooCommerce support in core theme

### ✔ Generic markup designed to work with most plugins

### ✔ `.entry-content` allows plugins to render cleanly

### ✔ Plugin compatibility packs may be provided separately

### ✔ WooCommerce Edition will be a separate theme

---

# 11. AI-Optimization Requirements

AI BasePress is designed to be **fully interpretable by LLMs**.

### Requirements:

1. File responsibilities documented at the top of each file
2. No deep include chains
3. High-level structural consistency across templates
4. Clear naming conventions
5. Minimal magic / abstraction
6. Comments explain *why*, not *what*
7. CSS selectors written for human + AI readability
8. No auto-generated or minified code

---

# 12. Internationalization (i18n)

* All theme strings must use `__()` or `_e()`
* Text domain: `ai-basepress`
* Include `languages/ai-basepress.pot` in future releases

---

# 13. Versioning & Releases

Semantic versioning:

```
v1.x.x → Stable core (no breaking structure changes)
v2.x.x → Major additions (partial templates, new layouts)
v0.x.x → Experimental features
```

Initial release: **v1.0.0**

---

# 14. Roadmap

### v1.0.0

* Core minimal theme
* AI-optimized structure
* Base typography + layout
* One menu / one sidebar

### v1.1.x

* Additional templates (`search.php`, `archive.php`)
* More detailed example prompts

### v2.0.0 – Plugin Compatibility Packs

* **PluginPack Lite** (Contact Form 7, ACF, forms, etc.)
* **WooEdition** (separate WooCommerce version)

### v3.0.0 – Optional Enhancements

* Prebuilt layout blocks (header variations, hero sections)
* Pattern library (AI-ready HTML snippets)

---

# 15. Target Users

* Developers who build custom WordPress sites
* Freelancers doing migration from HTML
* Agencies maintaining multiple small WordPress sites
* AI users who want a theme that AI can modify safely
* Anyone who wants full control without bloat

---

# 16. Limitations

AI BasePress intentionally does **not** include:

* Theme options panel
* Customizer sections
* Global styling UI
* Gutenberg block patterns
* WooCommerce templates
* jQuery / JS frameworks
* CSS frameworks
* Design systems

---

# 17. License

**MIT License**

This allows full commercial usage, modification, forking, and redistribution.

---


