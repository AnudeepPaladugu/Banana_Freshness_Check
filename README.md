# 🍌 Banana Freshness Check

A simple AI-powered web application that analyzes a banana image and predicts its freshness level directly in the browser.

## ✨ Features

- 📷 Upload a banana image
- 📸 Capture a photo using your device camera
- 🤖 AI-based freshness classification
- 🚫 Checks whether the uploaded image is actually a banana
- 📊 Shows confidence scores for all freshness classes
- ⚡ Runs directly in the browser
- 📱 Clean, responsive interface

## 🧠 Freshness Classes

The model classifies bananas into four categories:

| Result | Meaning |
|---|---|
| 🍌 Fresh Banana | Fresh and safe to eat |
| ✅ Ripe & Ready | Ripe and ready to eat |
| ⚠️ Overripe | Very ripe and better suited for other uses |
| 🗑️ Throw it Away | Past its best |

The model uses **224 × 224** image input and these four classes are defined in the project metadata.

## 🔄 How It Works

```text
Upload Image / Capture Photo
            ↓
     Banana Verification
            ↓
      ┌─────┴─────┐
      │           │
 Not a Banana   Banana
      │           │
      ↓           ↓
   🚫 Stop    Freshness Model
                  ↓
        ┌─────────┼─────────┐
        ↓         ↓         ↓
      Fresh      Ripe    Overripe / Bad
```

The application first uses **MobileNet** to verify that the image contains a banana. If it passes that check, the custom TensorFlow.js model predicts the banana's freshness level.

## 🛠️ Technologies Used

- **HTML5**
- **CSS3**
- **JavaScript**
- **TensorFlow.js**
- **MobileNet**
- **Teachable Machine Image Model**
- **Web Camera API**

## 📁 Project Structure

```text
Banana_Freshness_Check/
│
├── index.html       # Web app, UI, camera and prediction logic
├── model.json       # TensorFlow.js model architecture
├── weights.bin      # Model weights
├── metadata.json    # Model labels and metadata
└── README.md        # Project documentation
```

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/AnudeepPaladugu/Banana_Freshness_Check.git
cd Banana_Freshness_Check
```

### 2. Start a local web server

Using Python:

```bash
python -m http.server 8000
```

Open the application at:

```text
http://localhost:8000
```

A local web server is recommended, especially when using the camera feature.

## 📸 How to Use

1. Open the application.
2. Upload a banana image or click **Use Camera**.
3. Allow camera permission if required.
4. Wait while the image is analyzed.
5. View the predicted freshness result.
6. Check the confidence breakdown.
7. Click **Try Another** to test another image.

## 🎯 Project Purpose

This project demonstrates how a trained image-classification model can be integrated into a real browser application using TensorFlow.js.

The complete prediction process happens on the client side, without a custom backend server.

## ⚠️ Note

The prediction is an AI model output and should not be treated as a guaranteed food-safety assessment. Results can vary depending on image quality, lighting, camera angle, and the type of banana being analyzed.

## 👨‍💻 Author

**Anudeep Paladugu**

[GitHub Profile](https://github.com/AnudeepPaladugu)

[Banana Freshness Check Repository](https://github.com/AnudeepPaladugu/Banana_Freshness_Check)

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.