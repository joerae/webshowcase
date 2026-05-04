# AGENTS.md — Joe's AI Showcase

## What this project is

A personal portfolio hub listing Joe Raeburn's AI/vibe-coding demo projects. It is a **single static HTML file** (`index.html`) with no framework, no build step, and no package manager. It deploys automatically to Netlify on every push to the GitHub main branch.

The hub is also a product credential — it should look sharp and reflect AI product craft. Design quality matters.

---

## File structure

```
/
├── index.html        ← the entire site lives here
├── images/           ← 16:9 screenshot for each demo card
│   ├── medcheker.png
│   ├── baitclicker.png
│   ├── maths-monsters.png
│   ├── slop-detective.png
│   └── oh-really.png
├── AGENTS.md         ← you are here
└── README.md         ← human-facing guide
```

No `node_modules`, no `dist`, no build output. If you find yourself reaching for npm, stop — this project is intentionally zero-dependency.

---

## Design system

### Colours (CSS variables defined in `:root`)

| Variable | Hex | Used for |
|---|---|---|
| `--yellow` | `#FFE94E` | Primary accent, card titles, arrows |
| `--coral` | `#FF5C3A` | Secondary accent |
| `--teal` | `#00C9A7` | Live badge, status dot |
| `--purple` | `#7B5EF6` | Blob, avatar gradient |
| `--navy` | `#0F0E1A` | Page background |
| `--card-bg` | `#1E1C2E` | Card background |
| `--border` | `rgba(255,255,255,0.08)` | Subtle dividers and card borders |
| `--text` | `#F0EEF8` | Body text |
| `--muted` | `rgba(240,238,248,0.5)` | Secondary text, descriptions |

**Never hardcode hex values in new CSS.** Always use the CSS variables above.

### Typography

- **Headings** (`h1`, `h2`, `h3`, card titles): `Syne`, weight 700–800
- **Body**: `DM Sans`, weight 400–500
- Both loaded from Google Fonts in the `<head>`

### Bubble colour classes

Bubbles are the small pill-shaped tags on each card showing tools and stack layers. Use these classes — do not invent new ones:

| Class | Colour | Use for |
|---|---|---|
| `b-yellow` | Yellow | Gemini, AI tools |
| `b-teal` | Teal | VS Code, backend layers |
| `b-purple` | Purple | Codex |
| `b-coral` | Coral | API layers |
| `b-gray` | Gray/muted | Netlify, infrastructure, neutral tools |

---

## Card anatomy

Each demo is a card. There are two card types:

### Live / clickable card
```html
<a href="https://DEMO-URL" target="_blank" class="card">
  <div class="card-image">
    <img src="images/FILENAME.png" alt="DEMO NAME screenshot" onerror="this.style.display='none'">
    <div class="card-image-placeholder"><span class="ph-icon">EMOJI</span><span>images/FILENAME.png</span></div>
  </div>
  <div class="card-body">
    <div class="card-top">
      <h2>DEMO NAME</h2>
      <span class="badge badge-live">Live</span>
    </div>
    <p>One or two sentence description. Punchy, plain English, no jargon.</p>
    <div class="card-divider"></div>
    <div class="card-meta">
      <div class="meta-row">
        <span class="meta-label">Built with</span>
        <div class="bubbles">
          <span class="bubble b-???">Tool</span>
        </div>
      </div>
      <div class="meta-row">
        <span class="meta-label">Stack</span>
        <div class="bubbles">
          <span class="bubble b-???">Layer</span>
        </div>
      </div>
    </div>
    <span class="card-arrow">→</span>
  </div>
</a>
```

### Coming soon / static card
Same structure but:
- Outer element is `<div>` not `<a>` 
- Add `card-static` class: `<div class="card card-static">`
- Badge is `badge-soon` or `badge-wip`
- No `<span class="card-arrow">` needed

### Promoting a card from "coming soon" to "live"
1. Change `<div class="card card-static">` → `<a href="URL" target="_blank" class="card">`
2. Close with `</a>` not `</div>`
3. Change badge class to `badge-live` and text to `Live`
4. Add `<span class="card-arrow">→</span>` before closing `</div>` of `.card-body`

---

## Image handling

- Images go in `images/` at the root
- Format: PNG, 16:9 aspect ratio, ideally 1280×720px
- The `onerror="this.style.display='none'"` attribute on every `<img>` hides broken images gracefully — the placeholder emoji/text shows instead. **Do not remove this attribute.**

---

## Copy and tone

- Short, punchy descriptions — one or two sentences max per card
- Plain English, no buzzwords, no "leveraging AI to unlock synergies"
- Slight personality is good: "Scroll bait, but make it fun" not "An interactive news gamification platform"
- The about section is first-person and casual

---

## What not to do

- Do not add a build step, bundler, or package.json
- Do not add JavaScript frameworks or import maps
- Do not hardcode colours — use CSS variables
- Do not create new bubble colour classes — use the existing five
- Do not add external CSS or JS dependencies beyond the two Google Fonts already linked
- Do not change the `onerror` pattern on image tags
- Do not alter the CSS variable names in `:root`

---

## Deployment

- Repo is on GitHub (main branch)
- Netlify watches main and auto-deploys on every push
- No build command, publish directory is `/`
- No environment variables required (this is a purely static site — API calls happen in the individual demo projects, not here)