<div align="center">

# 🧬 Biomedical Image Processing

### Automatic image segmentation with Otsu's thresholding

*Load a folder of biomedical images → compute histograms & CDFs → auto-threshold → segment foreground/background — all through a simple Java Swing GUI.*

![Java](https://img.shields.io/badge/Java-8%2B-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/GUI-Java%20Swing-blue?style=flat-square)
![Algorithm](https://img.shields.io/badge/Algorithm-Otsu's%20Thresholding-6A5ACD?style=flat-square)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

</div>

---

## 🎥 Demo

<div align="center">

![Demo of Biomedical Image Processing app](./Visual%20working/output.gif)

</div>

---

## ✨ Features

| | |
|---|---|
| 📂 **Batch folder input** | Point the app at a directory of images and it picks up every file inside |
| 🖼️ **Auto preprocessing** | Every image is resized to 256×256 and converted to 8-bit grayscale |
| 📊 **Histogram & CDF** | Pixel intensity distribution (0–255) and cumulative distribution are computed per image |
| 🎯 **Otsu's thresholding** | Automatically finds the optimal binarization threshold — no manual tuning |
| 🌓 **Foreground/background split** | Produces clean binary masks above/below the computed threshold |
| 📈 **"Probability of affection"** | Reports the foreground pixel ratio as a quick region-of-interest estimate |
| 🖥️ **Interactive Swing GUI** | Select folder → process → preview all 4 images side by side → save results |
| 💾 **Exportable output** | Saves original/thresholded/foreground/background PNGs + a text processing log |

---

## ⚙️ How it works

```
   Input image
       │
       ▼
 Resize to 256×256  +  Convert to grayscale
       │
       ▼
 Histogram (0–255)  +  Cumulative Distribution Function
       │
       ▼
 Otsu's Method → optimal threshold t*
   (maximizes between-class variance of fg/bg pixel populations)
       │
       ├──► Foreground mask  (pixel > t*)
       └──► Background mask  (pixel ≤ t*)
       │
       ▼
 "Probability of affection" = foreground pixels / total pixels
```

The repo also ships `pixel_data.csv` — pre-computed pixel value / histogram / CDF data extracted from the sample images in `data/`, so you can explore or plot intensity distributions in Python/pandas or Excel without recompiling the Java app.

---

## 📁 Project structure

```
Biomedical-Image-Processing/
├── OtsuThresholding2.java   # Main application (GUI + Otsu thresholding pipeline)
├── OtsuThresholding2.class  # Compiled class file
├── data/                    # Sample input images (grayscale biomedical images)
├── pixel_data.csv           # Precomputed pixel value / histogram / CDF data
├── LICENSE                  # MIT License
└── Visual working/
    └── output.gif           # Demo recording of the app in action
```

---

## 🚀 Getting started

### Requirements
- Java JDK 8+ (uses `java.awt`, `javax.imageio`, `javax.swing` — all standard library, **zero external dependencies**)

### 1. Clone

```bash
git clone https://github.com/IshaaYadav/Biomedical-Image-Processing.git
cd Biomedical-Image-Processing
```

### 2. Compile

```bash
javac OtsuThresholding2.java
```

### 3. Run

```bash
java OtsuThresholding2
```

### 4. Use the app

1. Click **Select Folder** and choose `data/` (or any folder of your own images).
2. Click **Process Images** — the first valid image is processed and displayed: original, thresholded, foreground, and background, plus the probability of affection.
3. Click **Save Results** to export the four processed images and a processing log to a folder of your choice.
4. Click **Exit** to close.

---

## 📜 License

This project is licensed under the [MIT License](./LICENSE) © 2026 Isha Yadav.

<div align="center">

Made by [Isha Yadav](https://github.com/IshaaYadav)

</div>
