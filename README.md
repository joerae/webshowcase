# Joe's AI Showcase

Personal portfolio hub for AI/vibe-coding demo projects. Single static HTML file, deployed automatically to Netlify on push.

**Live site:** `https://joeraeburn.com` ← update this once deployed

---

## Adding a new demo card

1. Copy an existing card block from `index.html` (grab everything from `<a href=...` to the closing `</a>`)
2. Paste it at the end of the `.grid` div, before the closing `</div>`
3. Update: the `href`, the `h2` title, the `<p>` description, the badge, the emoji, the image filename, and the bubbles
4. Add a screenshot to `images/` (see below)
5. Commit and push — Netlify deploys automatically

---

## Adding images

- Take a screenshot of the demo at ~1280×720px (16:9)
- Save as PNG into the `images/` folder
- Name it to match what's in the card's `<img src="images/FILENAME.png">`
- If no image is present, a placeholder with the emoji shows instead — nothing breaks

**Mac screenshot tip:** `Cmd+Shift+4` to drag-select, or use GoFullPage browser extension for a clean full-page capture.

---

## Going live with a "coming soon" card

When a demo is deployed and ready:

1. Change `<div class="card card-static">` → `<a href="YOUR_URL" target="_blank" class="card">`
2. Change the closing `</div>` → `</a>`
3. Change the badge to `<span class="badge badge-live">Live</span>`
4. Add `<span class="card-arrow">→</span>` as the last line inside `.card-body`

---

## Bubble colour guide

| Class | Colour | Use for |
|---|---|---|
| `b-yellow` | Yellow | Gemini, AI tools |
| `b-teal` | Teal | VS Code, backend |
| `b-purple` | Purple | Codex |
| `b-coral` | Coral | API |
| `b-gray` | Gray | Netlify, infrastructure |

---

## Swapping in a photo

In the About section, replace the `<div class="avatar">JR</div>` with:

```html
<img src="images/joe.jpg" style="width:96px;height:96px;border-radius:50%;object-fit:cover">
```

---

## Deploy process

1. Edit `index.html` and/or add files to `images/`
2. Stage + commit in Fork
3. Push to `main`
4. Netlify detects the push and redeploys — usually live in under a minute

No build step. No environment variables. No dependencies.