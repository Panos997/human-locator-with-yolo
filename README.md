# 📷 People Counter — Real-time AI on your phone

A single-page web app that uses your phone camera and **YOLOv8 nano** to detect and count people in real time.
Everything runs **directly on the device** — no server, no uploads, no privacy concerns.

🔗 **Live demo:** https://panos997.github.io/human-locator-with-yolo/

---

## ✨ Features

- 🟢 **Live count** — how many people are in the frame right now
- 🔝 **Peak counter** — the highest number seen during the session
- 📦 **Bounding boxes** — green corner markers drawn around each detected person
- 🔒 **100% private** — camera feed never leaves your device
- 📱 **Mobile-first** — works on any modern phone browser (Chrome / Safari)
- ⚡ **No server needed** — pure HTML + JS, hosted on GitHub Pages for free

---

## 🗂️ Files in this repo

| File | What it does |
|------|-------------|
| `index.html` | The entire app — camera, AI inference, UI |
| `yolov8n.onnx` | YOLOv8 nano model file (12 MB), served from this repo |
| `README.md` | This file |

No build tools, no npm, no backend. Just two files.

---

## 🛠️ How it works

| Component | Technology |
|-----------|-----------|
| AI model | YOLOv8 nano — detects only people (COCO class 0) |
| Model format | ONNX (`.onnx`) |
| Inference engine | [ONNX Runtime Web](https://onnxruntime.ai/) via WebAssembly |
| Model hosting | This GitHub repo (no external auth or CORS issues) |
| Hosting | GitHub Pages (free) |
| Dependencies | One CDN script tag for ONNX Runtime — that's it |

The model (`yolov8n.onnx`) is served directly from this repo alongside the HTML file.
On first load it takes a few seconds to compile for your device. Subsequent visits are instant.

---

## 📲 How to deploy your own copy

### Step 1 — Download the model file
Open this link in your browser and save the file:
```
https://github.com/yoobright/yolo-onnx/raw/refs/heads/master/yolov8n.onnx
```

### Step 2 — Create a GitHub repo
1. Go to [github.com](https://github.com) and create a free account
2. Click **+ → New repository**, name it anything (e.g. `people-counter`), set it to **Public**

### Step 3 — Upload both files
- Click **Add file → Upload files**
- Upload `index.html` and `yolov8n.onnx` at the same time
- Click **Commit changes**

### Step 4 — Enable GitHub Pages
- Go to **Settings → Pages → Branch: main → Save**
- Wait 1–2 minutes

### Step 5 — Share your link
```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

---

## ⚙️ Configuration

Open `index.html` and find the config block near the top of the `<script>`:

```js
const CONF_THRESH = 0.45;  // confidence threshold — raise to reduce false positives
const IOU_THRESH  = 0.45;  // overlap threshold for merging duplicate boxes
const INTERVAL    = 300;   // ms between frames — lower = faster but heavier on CPU
```

You can also change the box color by finding `#34d399` and replacing it with any CSS color.

---

## 🔒 Privacy

- No data is sent anywhere
- No analytics, no tracking, no cookies
- The camera stream is processed locally on your device and never stored
- The model file is served from GitHub, not from any AI company's servers

---

## 📄 License

MIT — do whatever you want with it.
