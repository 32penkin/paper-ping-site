# site — PaperPing landing, privacy, support, delete-data (M1 draft)

Static HTML for GitHub Pages: https://32penkin.github.io/paper-ping-site/ . Source of truth — `site/` in the private repo `32penkin/paper-ping`; this repo is a published copy.

| Page | en | pl | ru |
|---|---|---|---|
| Landing | `index.html` | — | — |
| Privacy policy | `privacy/` | `privacy/pl/` | `privacy/ru/` |
| Support (FAQ) | `support/` | `support/pl/` | `support/ru/` |
| Delete your data | `delete-data/` | `delete-data/pl/` | `delete-data/ru/` |

- One stylesheet `assets/site.css` (app theme colors, light/dark via `prefers-color-scheme`), system
  fonts, no JavaScript, no cookies, no analytics, no external fonts/scripts/CDN. All links are
  relative, so the site works from any base path (`https://<user>.github.io/<repo>/` or a domain).
- The landing demo (letter → reminder → notification) is plain HTML/CSS with the fictional
  onboarding letter (Linden Court Residents’ Association), no real data.
- `.nojekyll` — serve files as they are. `404.html` — minimal, three languages.

## Placeholders to fill before publishing (all marked with the amber `todo` style)

| Placeholder | Where | Who decides |
|---|---|---|
| `[ADMIN]` — data controller: Yauhen as a private person, or his sole proprietorship (name, address, NIP) | privacy ×3 | Yauhen |
| `[SUPABASE_REGION]` — e.g. EU (Frankfurt) | privacy ×3 | Yauhen (Q1) |
| `[DATE OF PUBLICATION]` | privacy ×3 | on publishing |
| Beta sign-up: `mailto:` stub on the landing → `{BETA_FORM_URL}` | `index.html` | Yauhen (form tool) |
| Store links: "coming soon" pills → App Store / Google Play URLs | `index.html` | after the store records exist |

Check: `grep -rn 'class="todo"' site/` must print nothing before publishing.

## Publishing (when approved)

The main repo `32penkin/paper-ping` is private (D9); GitHub Pages on a private repo needs a paid
plan. As for reverse-steps (`32penkin/reverse-steps-site`): create a public repo
`32penkin/paper-ping-site`, copy this folder to its root, Settings → Pages → Deploy from branch
`main` / root. Site URL then `https://32penkin.github.io/paper-ping-site/` = `https://32penkin.github.io/paper-ping-site` in
`store-listing/`. Links from channels may carry `?src=<channel>`; the site does not read it (no
scripts) — attribution plan in `docs/MARKETING.md` §7.

## Local check

```sh
cd site && python3 -m http.server 8000   # http://localhost:8000/
```

Screenshots were checked in Chromium (Playwright) at 1280 px and 390 px, light and dark, with no
horizontal overflow and no external requests.
