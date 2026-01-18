# Implementation of Deep Learning Methods Based on LSTM and STFT Architectures for Speech Signal Quality Enhancement

**Final Project (UAS) - Machine Learning** *Speech denoising using an LSTM-based direct spectrogram mapping approach trained on paired noisy and clean speech signals.*

---

## Project Structure
```text
.
├── docs/
│   ├── PPT UAS Machine Learning.pdf
│   ├── Poster UAS Machine Learning.pdf
│   ├── Paper UAS Machine Learning.pdf
│   └── Link Video.txt 
│
├── src/
│   ├── 1_Training_Pipeline.PY
│   └── 2_Inference_and_Demo.PY
│
└── README.md
```

## Project Description
This project aims to enhance the quality of speech signals degraded by background noise (e.g., traffic, cafe noise). By implementing a hybrid pipeline that combines **Digital Signal Processing (STFT)** with **Recurrent Neural Networks  (LSTM)**, the system effectively separates human speech from environmental interference.

### Key Methodology:
1.  **Pre-processing:** Audio is downsampled to **16 kHz** and transformed into the frequency domain using **Short-Time Fourier Transform (STFT)**.
2.  **Model Architecture:** A Stacked LSTM network is used to perform **Direct Spectral Mapping**, predicting the magnitude of clean speech from noisy input.
3.  **Reconstruction:** The cleaned audio is reconstructed using Inverse STFT (ISTFT) with the original noisy phase.

**Dataset:** Experiments were conducted using the **VoiceBank-DEMAND** dataset (Valentini-Botinhao, 2017), which contains paired recordings of clean and noisy speech.

---

## Experimental Results

Despite the challenges of non-stationary noise, the model achieved significant improvement in speech intelligibility.

| Metric | Initial (Noisy) | Final (Enhanced) | Improvement (Gain) |
| :--- | :--- | :--- | :--- |
| **Average SNR** | 8.51 dB | **14.83 dB** | **+6.32 dB** |

> **Note on SNR Results:**
> The final SNR of 14.83 dB represents a substantial gain (+6.32 dB) from heavily degraded inputs. The absolute value is constrained by the **16 kHz downsampling** (limiting high-frequency resolution) and the use of **Noisy Phase** for reconstruction. However, auditory analysis confirms that background noise is effectively suppressed while speech formants are preserved.

---

## How to Run the Code

The source code is organized into two sequential notebooks located in the `source_code/` folder:

### 1. Training (`1_Training_Pipeline.ipynb`)
Run this notebook to process the dataset and train the LSTM model from scratch.
* **Input:** Raw .wav dataset (VoiceBank-DEMAND).
* **Process:** STFT Feature Extraction -> LSTM Training.
* **Output:** Saved model file (`.h5`).

### 2. Inference & Demo (`2_Inference_and_Demo.ipynb`)
Run this notebook to evaluate the model or try the **Real-time Demo**.
* **Features:**
    * Loads the pre-trained model.
    * Calculates SNR metrics on the test set.
    * Visualizes Spectrograms (Before vs. After).
    * **Gradio Interface:** Launch a web UI to record your own voice and denoise it instantly.

---

## Team Members
**BINUS ASO School of Engineering**
**Automotive and Robotics Engineering**

* **Gabriel Ruben Weslie** - gabriel.weslie@binus.ac.id
* **Jordan Elishua Wibowo** - jordan.wibowo001@binus.ac.id
* **Rizky Kresnanto Dananjaya** - rizky.dananjaya@binus.ac.id
* **Takeshi Gobstan Lee** - takeshi.lee@binus.ac.id

---
*Created for Machine Learning Final Exam (UAS) - Odd Semester 2025/2026*
