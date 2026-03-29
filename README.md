# 🧠 Ostris AI-Toolkit on Google Colab (Free T4 GPU)

Run [Ostris AI-Toolkit](https://github.com/ostris/ai-toolkit) for free on Google Colab using a T4 GPU — no local GPU required. Access the full AI-Toolkit web UI directly from your browser via a public Cloudflare tunnel URL.

---

## 📋 Requirements

- A Google account (to use Google Colab)
- (optional) A [Hugging Face](https://huggingface.co) account + API token
- No local GPU needed — everything runs on Colab's free T4

---

## 🚀 How to Use

### 1. Open Google Colab

Go to [colab.research.google.com](https://colab.research.google.com) and create a **New Notebook**.

### 2. Enable the T4 GPU

> **Runtime → Change runtime type → T4 GPU → Save**

This is required — the notebook won't work without a GPU runtime.

---

### 3. Run Cell 1 — Install

Paste and run the first cell. It will:

- Clone the AI-Toolkit repository
- Install Node.js 20 via `nvm`
- Install all Python dependencies (PyTorch, etc.)
- Build the web UI

⏱️ This takes **3–6 minutes** on first run. On subsequent runs it will skip cloning and just pull updates.

---

### 4. Run Cell 2 — Start the Server

Paste and run the second cell. It will:

- Start the AI-Toolkit backend server
- Open a **Cloudflare tunnel** to expose it publicly
- Print your public URL in the output

You will see something like this in the output:

```
✅ cloudflared ready
✅ Using Node: v20.20.2
⏳ Waiting for server to start...
🌐 Your public URL: https://log-passenger-installation-photographs.trycloudflare.com
✅ Server is up! Open the URL above.
```

### 5. Open the AI-Toolkit UI

Click the `trycloudflare.com` URL printed in the output — this opens the full Ostris AI-Toolkit interface in your browser.

> ⚠️ **The URL changes every session.** Each time you restart Colab, Cell 2 will generate a new URL. Just copy the new one from the output.

---

## 🔑 Setting Your Hugging Face Token

After opening the UI, go to **Settings** and paste your Hugging Face token. Without it, you won't be able to download models.

Get your token at: [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)

---

## ❓ Troubleshooting

### The URL isn't showing up
Scroll up in the Cell 2 output — the `trycloudflare.com` URL may appear before the "Server is up!" message. Look for a line starting with `🌐 Your public URL:`.

### Opening the URL shows "Bad Gateway" or a blank page
The server is still starting. Wait 30–60 seconds and refresh the page.

### `localhost:8675` doesn't work
That's expected — `localhost` only works on your own machine. **Always use the `trycloudflare.com` URL** printed in the Cell 2 output to access the UI. That URL is your "localhost" tunneled to the public internet.

### Session disconnected / runtime crashed
Colab free tier disconnects after ~1–2 hours of inactivity. Just re-run Cell 2 (you don't need to re-run Cell 1 unless the runtime was fully reset). A new public URL will be generated.

### Node or npm errors
Re-run Cell 1 from scratch. If the `ai-toolkit` folder already exists, the cell will `git pull` instead of re-cloning.

---

## 📁 Project Structure

```
├── README.md
├── Cell_1_Install.ipynb     # Installation notebook cell
└── Cell_2_Start.ipynb       # Server start notebook cell
```

---

## 📜 Credits

- [Ostris AI-Toolkit](https://github.com/ostris/ai-toolkit) by [@ostris](https://github.com/ostris)
- Easy-Install script by **ivo**
- Colab adaptation by this repo

---

## ⚠️ Disclaimer

This project is not affiliated with Ostris or Hugging Face. Google Colab free tier has usage limits — for heavy or extended training, consider upgrading to Colab Pro or using a paid GPU provider.
