# Matt Hughes — AI Lab Portfolio

A single-page portfolio site: background, and four live AI experiments (game-shaped proofs of concept in agentic AI — LangGraph state machines, RAG memory, multi-agent debate, tool-calling economies).

Live at [matthughes.ca](https://matthughes.ca).

## Stack

Plain HTML/CSS/JS, no build step. Fonts (Fraunces, IBM Plex Sans/Mono) load from Google Fonts; everything else is self-contained in [`index.html`](index.html).

## Local development

```bash
npm install
npm start
```

Serves the page at `http://localhost:$PORT` (defaults to whatever `serve` picks if `PORT` isn't set).

## Deployment

Hosted on [Railway](https://railway.app), deployed straight from this repo — `npm start` runs [`serve`](https://github.com/vercel/serve) against the static files. Pushing to `main` triggers a redeploy.

## The experiments

| Project | Repo | Live |
|---|---|---|
| The Philosopher's Bar | [fungame03](https://github.com/mhughes72/fungame03) | [Play](https://web-production-17a4a7.up.railway.app/) |
| AI Driven Haunted Mansion | [fungame02](https://github.com/mhughes72/fungame02) | [Play](https://web-production-54fd0.up.railway.app/) |
| Definitely Not an AI Rip-off of Jeopardy! | [fungame04](https://github.com/mhughes72/fungame04) | [Play](https://fungame04-production.up.railway.app/) |
| Republic of Veridia | [fungame05](https://github.com/mhughes72/fungame05) | [Play](https://fungame05-production.up.railway.app/) |
