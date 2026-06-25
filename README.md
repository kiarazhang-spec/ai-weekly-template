# ai-weekly-template

> A zero-cost, AI-tool-agnostic template to publish your own weekly newsletter on GitHub Pages.
> 一份 AI 工具中立的极简学术风周报模板，托管在 GitHub Pages，零成本自动归档。

🌐 **Live demo of a working instance → [kiarazhang-spec.github.io/kiara-weekly-ai](https://kiarazhang-spec.github.io/kiara-weekly-ai/)**

> ⚡ **Tool-agnostic by design.** Use ChatGPT, Claude, Gemini, Cursor, WorkBuddy, or any AI assistant you like. The prompt in [`prompts/weekly-prompt.md`](./prompts/weekly-prompt.md) is plain Markdown — copy, paste, generate.

---

## ✨ What you get

- 📰 **A static archive site** (HTML + CSS, no JS framework, no build step)
- 🤖 **GitHub Actions auto-deploy** — push an HTML file → site updates in ~3 minutes
- 🎨 **Stratechery-style minimal academic design** — single accent color, 760px reading width, system fonts
- 🧠 **A ready-to-use AI prompt** that enforces source-tier discipline (no hallucinated links)
- 📋 **AGENTS.md** — so future AI helpers won't mess up your repo

---

## 🚀 Quick start (5 minutes)

### 1. Use as template
Click **"Use this template" → "Create a new repository"** at the top of this GitHub page. (Or just Fork it.)

### 2. Enable GitHub Pages
In your new repo: **Settings → Pages → Source: GitHub Actions**

### 3. Customize
Edit these placeholders in `index.html`:

| Placeholder | Replace with |
|---|---|
| `{{NEWSLETTER_TITLE}}` | Your newsletter name (e.g. "Sarah's Climate Weekly") |
| `{{NEWSLETTER_TAGLINE}}` | One-line tagline shown under the title |
| `{{NEWSLETTER_KICKER}}` | Small uppercase eyebrow text (e.g. "CLIMATE WEEKLY") |
| `{{NEWSLETTER_DESCRIPTION}}` | One-paragraph description shown in the lead box |

(Optional) Re-theme in `assets/style.css`: change `--green: #2D8B3E` in `:root` to your color.

### 4. Write your first issue
Copy `posts/example-issue.html` → `posts/YYYY-MM-DD.html` (use the Monday of the week you're covering).
Replace the placeholder content. Keep the 8-section structure.

### 5. Push
```bash
git add posts/2026-06-29.html
git commit -m "post: weekly 2026-06-29"
git push
```

GitHub Actions will rebuild `manifest.json` and deploy. Your post is live at
`https://<your-username>.github.io/<your-repo>/posts/2026-06-29.html`.

---

## 🤖 Generating issues with AI

The AI does the heavy lifting. You curate, edit, and publish.

1. Open your favorite AI tool (ChatGPT, Claude, Gemini, Cursor, etc.)
2. Paste the full content of [`prompts/weekly-prompt.md`](./prompts/weekly-prompt.md)
3. Tell it the date range (e.g. "本周监测周期：2026-06-22 ~ 2026-06-28")
4. AI returns a full HTML file
5. **Manually verify every link** (the prompt forbids fabricated URLs, but always double-check)
6. Save as `posts/YYYY-MM-DD.html`, commit, push

The prompt is **opinionated** — it bakes in source-tier rules (S = official blogs, A = English mainstream, B = supplementary), an 8-section structure, and word counts. You can adapt it to your domain by editing the source list and themes.

---

## 📐 How it works

```
your-newsletter-repo/
├── index.html                    # Homepage — reads posts/manifest.json
├── posts/
│   ├── YYYY-MM-DD.html           # One file per issue (Monday of the covered week)
│   ├── example-issue.html        # Reference template — delete or keep as a guide
│   └── manifest.json             # Auto-generated index. DO NOT EDIT BY HAND.
├── assets/style.css              # All styles (~300 lines, vanilla CSS)
├── prompts/weekly-prompt.md      # The AI prompt for generating issues
├── .github/workflows/deploy.yml  # Rebuilds manifest, deploys to Pages
├── AGENTS.md                     # Instructions for AI agents editing this repo
├── LICENSE                       # MIT for code; CC BY 4.0 recommended for your content
└── README.md                     # This file
```

The Actions workflow scans `posts/*.html` files matching `YYYY-MM-DD.html`, extracts the `<title>` and first `.lead` block as the summary, and writes `manifest.json`. The homepage `<script>` fetches this manifest and renders the latest issue + full archive list. **No backend, no database, no JS framework.**

---

## 🎨 Customization

### Change theme color
In `assets/style.css :root`, change `--green` (and `--green-soft` to a matching pastel). That's it.

### Change sections
Edit `index.html`'s "About" footer block, and adjust the prompt in `prompts/weekly-prompt.md` to match your domain (e.g. swap AI source list for climate-tech sources).

### Change reading width
In `assets/style.css`, `.page { max-width: 760px; }` — adjust as you like.

### Custom domain
GitHub Settings → Pages → Custom domain. Standard CNAME / A record setup.

---

## 📜 License

- **Code** (HTML scaffolding, CSS, GitHub Actions YAML): [MIT](./LICENSE) — use freely, including commercial.
- **Your own newsletter content** is yours. We recommend [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) (attribution required when republished), but it's your call.

---

## 🙏 Credits

Built and maintained by [@kiarazhang](https://github.com/kiarazhang-spec), based on the design system of [kiara-weekly-ai](https://github.com/kiarazhang-spec/kiara-weekly-ai).

If you publish a newsletter using this template, I'd love to see it — open an Issue and share the link.

---

## ⚠️ Disclaimer

This template provides scaffolding only. **You** are responsible for:
- Verifying every link in your published issues
- Ensuring you have rights to quote / reference sources
- Adding your own disclaimers (the example issue shows a recommended set)
- Compliance with applicable laws in your jurisdiction

Generated content from AI assistants may contain factual errors. **Always fact-check before publishing.**
