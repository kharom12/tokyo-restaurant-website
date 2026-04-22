# Tokyo Express — Hibachi and Boba

Official website for **Tokyo Express — Hibachi and Boba**, a family-owned Japanese restaurant in Greensboro, NC.

- 📍 3722 E. Battleground Ave, Greensboro, NC 27410
- 📞 336-707-2536
- 🍱 Hibachi · 🧋 Boba · 🎉 Catering

## Stack

Single-page static site. No build step.

- `index.html` — the whole website (HTML + CSS + JS inline)
- `images/` — food & restaurant photography
- `package.json` — only for running [`serve`](https://www.npmjs.com/package/serve) so Railway has a start command

## Run locally

```bash
npm install
npm run dev
# open http://localhost:3000
```

Or just open `index.html` directly in your browser — everything is self-contained.

## Deploy (Railway)

This repo is ready for Railway out of the box:

1. Create a new project on [railway.app](https://railway.app) → **Deploy from GitHub repo** → pick this repo.
2. Railway auto-detects Node via `package.json` and runs `npm start`.
3. In project settings → **Networking** → generate a public domain (or attach a custom domain).

`railway.json` pins the start command and retry policy.

## Project structure

```
.
├── index.html          # full website
├── images/             # 24 food & restaurant photos
├── package.json        # `serve` start script for Railway
├── railway.json        # Railway build/deploy config
├── README.md
└── .gitignore
```

## About

Website crafted for Snow, owner of Tokyo Express — a college boba-shop dream turned real.
