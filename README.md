# SkySeek

*A private, login‑free ChatBot powered by **GPT‑5**, with lightweight **agents** and a clean, no‑frills UI.*

> Privacy first: no accounts, no analytics, no server logs. Your API key and chats stay on your device.

---

## ✨ Features

* **GPT‑5 chat** with streaming replies
* **Zero sign‑in** — paste your API key locally
* **Agents** — small, editable role presets (system prompts + defaults)
* **Simple UI** — markdown, code blocks, copy buttons, keyboard shortcuts
* **Local history** — export/import chats; clear with one click

---

## 🧰 Tech Stack

* Web app (React/TypeScript + Vite) — client‑only, no backend logging
* HTTP client with SSE for streaming
* Local storage for key & chats (or IndexedDB)

> Optional Android client (Kotlin/Compose) can mirror the same API layer.

---

## ⚙️ Setup

Create `.env.local` (never commit) and add your key/base URL:

```env
OPENAI_API_KEY=sk-***
OPENAI_BASE_URL=https://api.openai.com/
DEFAULT_MODEL=gpt-5
```

Install & run:

```bash
pnpm i
pnpm dev
```

Build:

```bash
pnpm build && pnpm preview
```

---

## 🧭 Using Agents

Agents live in `agents/` (YAML/JSON). Switch from the header dropdown or via `/agent` command.

Example:

```yaml
id: coder
name: "Coder"
system: |
  You write concise, correct code with brief explanations.
model: gpt-5
temperature: 0.2
```

Included presets: **General**, **Coder**, **Researcher**, **Teacher**. You can duplicate and edit them inline.

---

## 🔒 Privacy

* No accounts, no telemetry.
* API key stored only in browser storage (or Android app prefs). Clear anytime.
* Chats are local; exporting is manual and encrypted only if you choose to.

---

## ⌨️ Shortcuts

* **Ctrl/⌘ + Enter** — send
* **Shift + Enter** — new line
* **/agent** — quick agent switch
* **/clear** — clear chat
* **/temp 0.2** — set temperature

---

## 📦 Project Structure

```
skyseek/
├─ agents/                 # agent presets
├─ src/
│  ├─ lib/openai.ts        # API client
│  ├─ store/               # state + persistence
│  ├─ components/          # Chat UI
│  └─ pages/               # routes
├─ public/
└─ .env.local.example
```

---

## 🐞 Troubleshooting

* **401/403** — key missing/invalid; check `.env.local`
* **No streaming** — provider plan may not support SSE; fallback to non‑streaming
* **Rate limits** — shorten messages, reduce max tokens, add retries

---

## 🗺️ Roadmap

* [ ] Per‑agent tools (web search, calculators) with permission prompts
* [ ] E2E encryption for exported chats
* [ ] Desktop build (Tauri) and Android parity module

---

## 📝 License

MIT — Privacy first.

---

**Author:** Diogo Serra (Diiicode) — building simple, private AI tools.
