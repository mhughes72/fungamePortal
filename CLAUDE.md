# fungamePortal

Matt's portfolio site for PM job applications — background + four live AI experiments (games built to demonstrate agentic AI fluency: LangGraph, RAG, multi-agent debate, tool-calling). Full recap of decisions below so a future session doesn't have to rediscover them.

## Structure

- `index.html` — the entire site. Single self-contained file (inline CSS/JS), no build step. **This is the single source of truth — edit it directly.** No separate template/fragment file exists anywhere else; don't recreate one.
- `assets/matt-hughes.jpg` — portrait used in the hero.
- `package.json` — `npm start` runs `serve -s . -l $PORT` for both local preview and Railway's deploy.
- `.claude/launch.json` — lets Claude's browser preview tool run the site locally via `npm start`.

## Deployment

- Hosted on **Railway**, deployed straight from this repo. Push to `main` → auto-redeploy.
- Custom domain: **matthughes.ca** (root + `www`), DNS on **Cloudflare**.
  - Cloudflare records: CNAME `@` and CNAME `www`, both **DNS only** (grey cloud, not proxied) — Railway needs to see the real CNAME to verify the domain and issue its Let's Encrypt cert. Proxying breaks that.
  - Gotcha we hit: the custom domains were added in Railway *before* DNS had finished propagating, so Railway's one-time verification failed and got stuck (yellow warning icon, no useful message, edge returned `x-railway-fallback: true` / "Application not found" even though the app was deployed and healthy). Fix was to remove and re-add the domains in Railway once DNS was confirmed resolving — it doesn't auto-retry on its own.
  - Railway Hobby plan includes 2 custom domains, which covers root + www.

## Content decisions worth knowing

- **No real screenshots of the four game experiments.** There was no way to persist the browser tool's screenshots to disk, and live-embedding the actual games via iframe would risk triggering their LLM API calls just from someone viewing the portfolio. Solution: bespoke CSS/SVG "poster" art per project instead, thematically matched to each game's own visual identity.
- Technique/stack chips on each project card were pulled from each game's own in-app "About" panel (real implementation detail, not generic marketing copy).
- LinkedIn (`https://www.linkedin.com/in/matthewhughes/`) is linked; phone number intentionally left off the public page for privacy (email + GitHub + LinkedIn only).
- Hero portrait is a circular crop placed where the hero's existing decorative amber glow already was, with a matching accent-color ring — deliberately placed to look native to the original design, not bolted on.

## If publishing this page as a Claude Artifact preview

The Artifact tool auto-wraps pages in its own `<!DOCTYPE>/<html>/<head>/<body>`, and rejects/duplicates those tags if the source file already has them. Since `index.html` here is a full standalone document (needed for direct Railway hosting), strip the outer `<!DOCTYPE html><html><head>`/`</head><body>`/`</body></html>` wrapper before publishing as an Artifact, and add it back if copying the Artifact-published version back into this repo. Don't maintain a second permanent copy of the content to avoid this — it's a one-off `sed` when actually needed.

## Related repos

The four experiments linked from this page each live in their own repo, all under github.com/mhughes72: `fungame02` (Haunted Mansion), `fungame03` (Philosopher's Bar), `fungame04` (Not Jeopardy), `fungame05` (Republic of Veridia).
