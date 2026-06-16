# 📷 People Counter — Real-time AI on your phone

A single-page web app that uses your phone camera and a **YOLOv8 nano** AI model to detect and count people in real time.  
Everything runs **directly on the device** — no server, no uploads, no privacy concerns.

---

## ✨ Features

- 🟢 **Live count** — how many people are in the frame right now
- 🔝 **Peak counter** — the highest number seen during the session
- 📦 **Bounding boxes** — green corners drawn around each detected person
- 🔒 **100% private** — the camera feed never leaves your device
- 📱 **Mobile-first** — works on any modern phone browser (Chrome / Safari)

---

## 🚀 How to use

1. Open the link on your phone: `https://YOUR-USERNAME.github.io/people-counter/`
2. Tap **"Open Camera"**
3. Allow camera permission when prompted
4. Wait ~5–10 seconds for the AI model to load (first time only)
5. Point the camera at people — they'll be detected automatically

---

## 🗂️ Files in this repo

| File | What it does |
|------|-------------|
| `index.html` | The entire app — camera, AI inference, UI, everything |
| `README.md` | This file |

That's it. No build tools, no npm, no backend. Just one HTML file.

---

## 🛠️ How it works (technical)

| Component | Technology |
|-----------|-----------|
| AI model | YOLOv8 nano (COCO, detects class 0 = person only) |
| Model format | ONNX (`.onnx`) |
| Inference | [ONNX Runtime Web](https://onnxruntime.ai/) via WebAssembly |
| Model source | Hugging Face (`niconielsen32/yolov8n-onnx`) |
| Hosting | GitHub Pages (free) |
| Dependencies | Zero — one CDN script tag for ONNX Runtime |

The model (~12 MB) is fetched from Hugging Face on first load and cached by the browser automatically, so subsequent visits load instantly.

---

## 📲 Deploy your own copy (step by step)

1. **Create a free GitHub account** at [github.com](https://github.com)
2. Click **`+` → New repository**, name it `people-counter`, set it to **Public**
3. Upload `index.html` (and this `README.md` if you want)
4. Go to **Settings → Pages → Branch: main → Save**
5. After 1–2 minutes your link is live:

```
https://YOUR-USERNAME.github.io/people-counter/
```

---

## ⚙️ Configuration (optional)

If you want to tweak the detection, open `index.html` and look for the `CONFIG` section near the top of the `<script>`:

```js
const CONF_THRESHOLD = 0.45;   // raise to reduce false positives (0.0 – 1.0)
const IOU_THRESHOLD  = 0.45;   // controls how boxes overlap before merging
const BOX_COLOR      = '#34d399'; // change the box color (any CSS color)
```

---

## 🔒 Privacy

- No data is sent to any server
- No analytics, no tracking, no cookies
- The camera stream is processed locally and immediately discarded
- The AI model is downloaded from Hugging Face (a public model host) and cached in your browser

---

## 📄 License

MIT — do whatever you want with it.
