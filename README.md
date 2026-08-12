# Spotlight — Website (v5: SEO/AEO/GEO/LLMO release)

Single-page site, no build step required (plain HTML/CSS/JS).

## Files you need — all 9

1. `index.html` — the whole site
2. `assets/logo-mark.png` — small nav icon *(reuse your existing file — not regenerated this round)*
3. `assets/hero-fixture.png` — hero spotlight graphic *(reuse existing)*
4. `assets/logo-full.png` — full logo, used in the footer *(reuse existing)*
5. `assets/favicon.png` — browser tab icon *(reuse existing)*
6. `robots.txt` — crawler rules, placed at the repo root
7. `sitemap.xml` — sitemap, placed at the repo root
8. `llms.txt` — machine-readable summary for LLMs/answer engines, placed at the repo root
9. `README.md` — this file (optional to upload)

**Important:** this round only rebuilt `index.html` + the new root files. The four PNGs under `assets/` are **not included here** — copy them over from your existing GitHub repo (they haven't changed).

## What's new in this release — content is now built to be found, answered, and cited

This release keeps v4's visual direction (dual-tone hero, module/toggle service cards, terminal philosophy block) and adds a full technical layer for four related but distinct goals:

**SEO (traditional search)**
- Real `<title>` and meta description tuned for the actual service categories
- `robots` meta tag, canonical URL, Open Graph + Twitter Card tags for clean link previews
- `robots.txt` (allows all standard crawlers) and `sitemap.xml` at the repo root

**AEO — Answer Engine Optimization** (Google's AI Overviews, Bing Copilot, voice assistants)
- A `FAQPage` JSON-LD block mirrors the on-page FAQ exactly, so answer engines can lift accurate Q&A pairs
- FAQ expanded from 4 to 6 questions, including direct "What is Spotlight?" / "Who is it for?" style questions people actually ask
- New **About** section right after the hero: one self-contained, quotable definition of what Spotlight is and does

**GEO — Generative Engine Optimization** (being cited/summarized correctly by AI chat tools)
- `ProfessionalService` JSON-LD lists each service line as a structured `Offer` with a plain-language description — a generative engine can quote this without guessing
- Copy throughout favors concrete, self-contained sentences over vague marketing language, so a paraphrase stays accurate

**LLMO — LLM-readable content**
- `llms.txt` at the repo root: a plain-markdown summary of the business, services, principles, and contact info, following the emerging `llms.txt` convention some AI crawlers now check for
- `robots.txt` explicitly allows known AI crawlers (GPTBot, ClaudeBot, Google-Extended, PerplexityBot, etc.) alongside standard search bots
- Semantic HTML throughout (`header`, `nav`, `main`, `section`, `footer`), a skip-to-content link, and `aria-label`/`aria-expanded` on interactive controls — all content lives in the raw HTML (nothing is injected only via JS), so crawlers and LLMs see the same thing a visitor does

**One new content section**
- **"Who It's For"** — three concrete client profiles (lean in-house teams, growth-stage brands, multi-brand operators), which also doubles as more citable, specific GEO/AEO content

## Deploy on Vercel via GitHub

1. Upload `index.html`, `robots.txt`, `sitemap.xml`, and `llms.txt` to the repo root, keeping your existing `assets/` folder as-is.
2. On vercel.com → your project → Framework Preset: **Other** → Deploy.
3. Every push to `main` auto-redeploys.
4. Once you have a real domain, replace every `https://www.spotlight.agency/` reference (in `index.html`'s `<head>`, `sitemap.xml`, and `llms.txt`) with your actual URL — canonical tags and structured data need to match the live domain to work correctly.

## Editing
- Copy and section content live directly in `index.html` — search for the section id (`#about`, `#services`, `#how`, `#fitfor`, `#results`, `#faq`, `#contact`).
- If you edit the FAQ text, update the matching `FAQPage` JSON-LD block in `<head>` too — search engines want the visible text and the structured data to match.
- Colors and fonts are CSS variables at the top of the `<style>` block (`:root`) — `--gold` is the marketing accent, `--signal` is the intelligence accent.
- The contact form opens the visitor's email client via `mailto:` — swap in a real form backend (Formspree, a serverless function, etc.) for silent submissions.
- Footer social links (`Instagram`, `LinkedIn`) are placeholders (`href="#"`) — add real URLs when ready, and update the matching `sameAs` array in the Organization JSON-LD.
