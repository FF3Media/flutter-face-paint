# Flutter Face Paint — Project Notes for Claude

## Workflow Preferences

- **Terminal first, always.** Use the Bash tool for everything possible: API calls, git, curl, file operations, DNS changes, checks. Only use browser automation when there is literally no other way (e.g. completing an OAuth browser flow).

## Project Overview

Static HTML website for Maryam Fitzgerald's face painting business in Kanata/Ottawa, Ontario.

- **Live URL:** https://flutterfacepaint.com
- **GitHub repo:** https://github.com/FF3Media/flutter-face-paint
- **GitHub Pages:** enabled on `main` branch, root `/`
- **DNS:** Managed on GoDaddy (account: FF3Media)

## Tech Stack

- Pure HTML/CSS/JS — zero frameworks, zero build step
- Shared stylesheet: `style.css`
- Form submissions: Formsubmit.co → `ff@ff3meda.com`
- Fonts: Playfair Display + DM Sans (Google Fonts)

## Deploy Process

```bash
cd "/Users/frank/Claude/Flutter Face Paint"
git add <files>
git commit -m "message"
git push
```

GitHub Pages auto-deploys on push to `main`. No build step needed.

## GoDaddy DNS (flutterfacepaint.com)

Use the GoDaddy API directly — do not use their browser UI.

```bash
curl -X PATCH "https://api.godaddy.com/v1/domains/flutterfacepaint.com/records" \
  -H "Authorization: sso-key <KEY>:<SECRET>" \
  -H "Content-Type: application/json" \
  -d '[...]'
```

Current A records point to GitHub Pages IPs:
- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

CNAME: `www` → `ff3media.github.io`

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Homepage |
| `about.html` | About Maryam |
| `gallery.html` | Filterable photo gallery + lightbox |
| `services.html` | Services overview |
| `birthday-parties.html` | Birthday parties landing page |
| `corporate-events.html` | Corporate events landing page |
| `reviews.html` | Testimonials |
| `faq.html` | FAQ with FAQPage JSON-LD schema |
| `book.html` | 2-step booking form (Formsubmit) |
| `style.css` | Shared stylesheet — all brand tokens here |
| `sitemap.xml` | XML sitemap |
| `robots.txt` | Search engine directives |
| `CNAME` | Custom domain for GitHub Pages |
