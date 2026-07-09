# 📧 Email Tone Agent

> Transform any email message into the perfect tone, context, and persona — powered by [NeuralSeek](https://neuralseek.com) Maistro AI.

**🌐 Live Demo:** This agent is published on the [NeuralSeek LATAM Demos page](https://demo.neuralseek.com/demos-page/email-expert)

---

## What it does

You paste a raw email, pick a tone, a communication context, and a sender persona — the agent rewrites it and explains every change it made. In seconds.

| Input | Output |
|-------|--------|
| Raw email message | Rewritten message in your chosen tone |
| Intended tone (reminder, formal, empathetic…) | Detailed explanation of what changed and why |
| Communication context (client project, internal team…) | |
| Persona type (project manager, executive…) | |

---

## Screenshots

### Input Form
![Email Tone Agent Form](./docs/form.png)

### Results — Explanation + Rephrased Output
![Email Tone Agent Results](./docs/results.png)

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| AI Engine | [NeuralSeek](https://neuralseek.com) — Maistro agent (`EmailTone_Expert1`) |
| Backend | Node.js + Express |
| Frontend | React 19 + Vite |
| Hosting | Replit |

---

## Project Structure

```
ToneAgent/
├── server.js              # Express backend — calls NeuralSeek Maistro API
├── package.json           # Root dependencies (express, node-fetch)
└── email-tone-ui/         # React frontend
    ├── src/
    │   ├── App.jsx        # Main component — form, state, API call, results
    │   ├── styles.css     # All styling (no external UI libraries)
    │   └── main.jsx       # React entry point
    ├── public/
    │   └── _redirects     # Netlify SPA redirect rule
    ├── index.html
    ├── vite.config.js     # Dev server with proxy to backend on :3001
    └── package.json
```

---

## Getting Started

### Prerequisites
- Node.js 18+
- A [NeuralSeek](https://neuralseek.com) account with a configured Maistro agent
- Your NeuralSeek API key

### 1. Clone the repo

```bash
git clone https://github.com/your-username/ToneAgent.git
cd ToneAgent
```

### 2. Set up environment variables

Create a `.env` file in the root:

```env
NEURALSEEK_API_KEY=your_api_key_here
```

> The NeuralSeek instance URL is set in `server.js`. Update it to point to your own instance if you're not using the same Maistro setup.

### 3. Install and start the backend

```bash
npm install
node server.js
# ✅ Backend running on port 3001
```

### 4. Install and start the frontend

```bash
cd email-tone-ui
npm install
npm run dev
# Open http://localhost:3000
```

That's it — the Vite dev server proxies `/api` calls to the backend automatically.

---

## How it works

```
User fills form
      ↓
React frontend (port 3000)
      ↓  POST /api/improve
Express backend (port 3001)
      ↓  POST to NeuralSeek Maistro
EmailTone_Expert1 agent
      ↓  Returns { answer }
Backend parses → { rephrasedMessage, explanation }
      ↓
UI displays results
```

The NeuralSeek Maistro agent receives four parameters: `inputMessage`, `intendedTone`, `communicationContext`, and `personaType`. It returns a rewritten message and a plain-English explanation of the changes.

---

## Available Options

**Intended Tone**
`empathetic` · `professional` · `direct` · `academic` · `polite` · `neutral` · or type your own

**Communication Context**
`internal team message` · `customer service reply` · `academic email` · `escalation response` · `external partner` · `executive update`

**Persona Type**
`student` · `internal employee` · `academic researcher` · `customer service representative` · `startup founder`

All fields support free-text input — you're not limited to the dropdown options.

---

## Deployment

### Replit
Import the repo directly into Replit. Set `NEURALSEEK_API_KEY` as a Replit Secret. The `.replit` config handles the run command.

### Netlify (frontend only)
```
Build command:   npm run build
Publish dir:     dist
```
Set the API URL in the frontend to point to your separately hosted backend.

### Self-hosted
Run `node server.js` on any Node-capable server. Build the frontend with `npm run build` and serve the `dist/` folder with any static file server or CDN.

---

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `NEURALSEEK_API_KEY` | ✅ Yes | Your NeuralSeek API key |

---

## Built by

**Esteban** — Babson College, November 2025

Powered by [NeuralSeek](https://neuralseek.com) · Built on Replit

---

## License

MIT — free to use, fork, and build on.
