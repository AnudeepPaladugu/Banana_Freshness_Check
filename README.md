# 🍌 Banana Freshness Check

> **An AI-powered browser app that checks whether a banana is fresh, ripe, overripe, or better thrown away.**

[![Made with TensorFlow.js](https://img.shields.io/badge/Made%20with-TensorFlow.js-orange?style=for-the-badge&logo=tensorflow)](https://www.tensorflow.org/js)
[![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow?style=for-the-badge&logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![HTML](https://img.shields.io/badge/HTML5-Frontend-red?style=for-the-badge&logo=html5)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![License](https://img.shields.io/badge/License-Open%20Source-green?style=for-the-badge)](#license)

## 👀 What is this?

**Banana Freshness Check** is a lightweight computer-vision web app that lets you upload a banana image or take a photo directly from your camera and get an AI-based freshness prediction.

The app runs the inference directly in the browser using **TensorFlow.js**, so there is no separate backend or API server required.

The freshness model currently returns one of four classes:

| Result | Meaning |
|---|---|
| 🍌 **Fresh Banana** | Fresh and ready to eat |
| ✅ **Ripe & Ready** | Ripe and good to eat now |
| ⚠️ **Overripe** | Very ripe and better suited for uses such as banana bread |
| 🗑️ **Throw it Away** | Past its best and recommended to discard |

The bundled model metadata defines these four classes and uses a **224 × 224** input size. fileciteturn4file0

---

## ✨ Features

### 📷 Upload or Use Your Camera
Upload an image from your device or use the device camera to capture a banana photo.

### 🧠 Two-Step AI Check
The app first attempts to verify that the image contains a banana using **MobileNet**, then sends the image through the dedicated banana-freshness model. This helps prevent unrelated images from being classified as banana freshness states. fileciteturn3file0 fileciteturn6file0

### 📊 Confidence Breakdown
The UI displays the prediction confidence for each freshness class instead of showing only the winning result. fileciteturn6file0

### ⚡ Runs in the Browser
The prediction flow is implemented with TensorFlow.js in the frontend. The repository contains the TensorFlow.js model definition, weights, and metadata needed by the app. fileciteturn1file0

### 📱 Responsive Interface
The UI is designed for a simple mobile-friendly experience, including camera support and drag-and-drop image upload. fileciteturn2file0 fileciteturn6file0

---

## 🧩 How It Works

```text
                ┌─────────────────────┐
                │ Upload image /      │
                │ Capture with camera │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Resize image to     │
                │ 224 × 224           │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ MobileNet           │
                │ Banana verification │
                └──────────┬──────────┘
                           │
                 ┌─────────┴─────────┐
                 │                   │
              Not banana           Banana
                 │                   │
                 ▼                   ▼
          🚫 Ask user to      ┌─────────────────┐
             try again        │ Freshness model │
                              └────────┬────────┘
                                       │
                         ┌─────────────┴─────────────┐
                         │                           │
                         ▼                           ▼
                  🟡 Fresh / Ripe             🟠 Overripe /
                                              🔴 Throw away
```

The frontend loads a local `model.json` TensorFlow.js model and its companion `weights.bin`, with class labels supplied through `metadata.json`. fileciteturn1file0 fileciteturn4file0

---

## 🗂️ Project Structure

```text
Banana_Freshness_Check/
│
├── index.html       # Main UI, styles, camera logic, and inference flow
├── model.json       # TensorFlow.js model architecture
├── weights.bin      # Trained model weights
├── metadata.json    # Model metadata and class labels
└── README.md        # Project documentation
```

The current repository contains these application and model files on the `main` branch. fileciteturn1file0

---

## 🚀 Run Locally

Because this project is a client-side web app, you can run it with a simple local web server.

### 1. Clone the repository

```bash
git clone https://github.com/AnudeepPaladugu/Banana_Freshness_Check.git
cd Banana_Freshness_Check
```

### 2. Start a local server

With Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

> **Why use a local server?** Camera access and browser model loading are generally more reliable when the page is served over `http://localhost` or HTTPS rather than opened directly as a `file://` page.

---

## 🌐 Deploy It

This project is well suited to static hosting because the frontend and TensorFlow.js model files are already stored in the repository.

You can deploy it to services such as:

- **GitHub Pages**
- **Netlify**
- **Vercel**
- **Cloudflare Pages**

For camera access in production, use an **HTTPS** deployment.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **HTML5** | Application structure and UI |
| **CSS3** | Styling, responsive layout, animations |
| **Vanilla JavaScript** | Application logic and browser interaction |
| **TensorFlow.js** | In-browser machine-learning inference |
| **MobileNet** | Banana verification step |
| **Teachable Machine model** | Banana freshness classification |
| **Web Camera API** | Capturing banana photos from supported devices |

The current frontend imports TensorFlow.js and loads a MobileNet model from Google's TensorFlow.js model storage, while the project-specific model is loaded from `./model.json`. fileciteturn2file0 fileciteturn3file0

---

## 🧪 Model Details

The repository includes a TensorFlow.js image-classification model exported for browser use. The metadata identifies it as a **Teachable Machine image model** with four freshness-related classes and a **224-pixel image size**. fileciteturn4file0

The inference pipeline normalizes the uploaded image before prediction and selects the class with the highest predicted score. fileciteturn6file0

### Important note about accuracy

This project is intended as a practical computer-vision demo and portfolio project. A prediction from the model should **not** be treated as a food-safety guarantee. Lighting, camera angle, background, banana variety, image quality, and training-data coverage can all affect the result.

---

## 🔐 Privacy

The freshness inference is designed to run in the browser. Images selected by the user are converted into browser image data and passed to the client-side model for analysis rather than being uploaded to a custom application backend. fileciteturn6file0

You should still review the hosting provider's policies and browser permissions when deploying the project publicly.

---

## 💡 Ideas for Future Improvements

- Add a visible **overall confidence score** for the winning class.
- Improve banana detection with a dedicated object-detection model.
- Add support for multiple bananas in a single image.
- Store optional prediction history locally in the browser.
- Add accessibility improvements such as stronger keyboard navigation and screen-reader descriptions.
- Add a small visual guide showing what fresh, ripe, and overripe bananas typically look like.
- Add automated tests for the UI and inference flow.
- Add a GitHub Actions workflow for deployment.
- Upgrade the model with a larger and more diverse training dataset for better real-world robustness.

---

## 🎯 Why I Built This

This project is a practical example of combining **machine learning with a simple, usable web interface**.

Instead of keeping the model inside a notebook, the project turns it into an interactive browser application where a user can immediately test an image, see the prediction, and understand the model's confidence.

It is a useful portfolio example for demonstrating:

**Computer Vision · TensorFlow.js · Frontend Development · Model Deployment · Browser APIs · AI Product Prototyping**

---

## 👨‍💻 Author

**Anudeep Paladugu**

GitHub: [@AnudeepPaladugu](https://github.com/AnudeepPaladugu)

Project: [Banana Freshness Check](https://github.com/AnudeepPaladugu/Banana_Freshness_Check)

---

## 📄 License

This repository does not currently include a dedicated license file. Add a `LICENSE` file if you plan to explicitly define how others may use, modify, and distribute the project.

---

## ⭐ Support the Project

Found this project useful or interesting?

**Give the repository a ⭐ on GitHub and feel free to fork it, experiment with the model, and improve the app.** 🍌
