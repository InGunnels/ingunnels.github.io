# ingunnels.com landing page

Static HTML for `https://www.ingunnels.com/`. Drop-in replacement for the current GitHub Pages default render.

## Deploy

Copy `index.html` into the root of your `ingunnels/ingunnels.github.io` repo, commit, push. GitHub Pages will serve it immediately at the apex.

```powershell
# From wherever your ingunnels.github.io clone lives:
cd C:\dev\ingunnels.github.io   # or wherever
Copy-Item C:\dev\BabyFocus\docs\website\index.html .
git add index.html
git commit -m "Add landing page"
git push
```

## Design choices

- **Single self-contained HTML file** — no Jekyll layouts, no external CSS, no web fonts, no analytics, no CDN. Matches the no-tracking ethos of the Pindot listing. Loads instantly, works offline, is reviewer-friendly.
- **Inline SVG icon** — concentric amber rings matching the Pindot brand mark. No image asset to download.
- **System font stack** — uses whatever the user's OS provides (SF on Apple, Segoe on Windows, Roboto on Android). Zero font-loading hop.
- **Mobile-first responsive** — breakpoint at 480px tightens padding and icon size.
- **Dark theme with amber accents** — matches Pindot's identity exactly.
- **Honest "personal label" voice** — does not pretend ingunnels is a multi-product company.

## What's on the page

1. **Brand mark + tagline** — `ingunnels — small software, made by hand`
2. **Lede paragraph** — frames it as a personal label, no ads, no data collection.
3. **What we make** — Pindot card with description, privacy link, and a disabled "Play Store soon" link.
4. **The label** — explanation that ingunnels is a play on the name, no company, no team.
5. **Contact** — `info@ingunnels.com`.
6. **Footer** — copyright + privacy + email.

## Things to update later

1. **Play Store link.** When the listing goes live, change the disabled "On the Play Store (soon)" link to the real URL. The `href="#"` placeholder is marked with a `<!-- TODO -->` comment.
2. **Privacy policy styling.** The existing `privacy-policy.md` will render with Jekyll's default light theme, which is jarring next to this dark landing page. Two options:
   - Leave as-is (works, but mismatched). Acceptable for v1.
   - Convert to HTML matching the landing page styling. Worth doing when you have an hour.
3. **Future products.** When you ship a second project under the ingunnels label, duplicate the `.product` block in `index.html`.
4. **Open Graph / Twitter Card metadata.** Skipped for v1 — if you ever want the link to render with a preview card when shared on social/messaging, add `og:title`, `og:description`, `og:image` meta tags. Low priority while the audience is just Play Store reviewers.

## Validation checklist before pushing live

- ☐ Open `index.html` locally in a browser — does it render?
- ☐ Resize the window narrow (or use device emulator) — does the mobile layout work?
- ☐ Click "Privacy policy" — should resolve to `/privacy-policy` and load the existing markdown.
- ☐ Click `info@ingunnels.com` — should open your default mail client.
- ☐ Check both `https://ingunnels.com/` and `https://www.ingunnels.com/` after pushing — both should serve the same content (assuming you set up the four apex A records earlier; if not, only `www` works).
