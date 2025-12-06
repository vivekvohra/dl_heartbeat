

# 🫀 Automated ECG Arrhythmia Classification

> **A Hybrid Deep Learning approach (1D-CNN + BiGRU + Attention) to detect cardiac arrhythmias from raw ECG signals.**

## 📌 Project Overview

Cardiovascular diseases are a leading cause of death globally. Manual analysis of long-term ECG recordings (Holter monitors) is tedious and prone to human error.

This project implements an automated classification system that reads **raw 1D ECG voltage data** (time-series) and classifies heartbeats into 5 standard AAMI categories. Unlike standard models that treat ECGs as images, this model uses a hybrid architecture to learn both **Morphological** (Shape) and **Temporal** (Rhythm) features.

## 🧠 Model Architecture

We utilize a lightweight, high-performance architecture designed to run on standard hardware:

1.  **Input:** Raw ECG signal (window of 360 samples / 1 second).
2.  **1D-CNN Layers:** Extracts morphological features (e.g., shape of QRS complex, P-wave).
3.  **Bi-Directional GRU:** Captures temporal dependencies and rhythm context (swapped from LSTM for efficiency).
4.  **Attention Mechanism:** Focuses the model on the most critical parts of the heartbeat (e.g., R-peak) while ignoring noise.

## 📊 Dataset

  * **Source:** [MIT-BIH Arrhythmia Database](https://physionet.org/content/mitdb/1.0.0/) (PhysioNet).
  * **Classes (AAMI Standard):**
      * **N:** Normal
      * **S:** Supraventricular (Premature)
      * **V:** Ventricular (PVCs - Dangerous)
      * **F:** Fusion
      * **Q:** Unknown
  * **Validation Strategy:** **Inter-Patient Splitting**. We split by *Patient ID* (Records), not by individual beats. This ensures the model is tested on patients it has never seen before, preventing data leakage.
