# Classroom Occupancy Estimation using WiFi Channel State Information (CSI)

Estimating the number of people in a classroom from WiFi CSI collected with low-cost ESP32
microcontrollers. This repository contains the machine learning and deep learning code from my
B.Sc. thesis at CUET (Dept. of CSE, supervised by Dr. Asaduzzaman), published at
**ICCIT 2023** — *A Framework to Estimate Classroom Occupancy using WiFi Channel State Information, https://ieeexplore.ieee.org/abstract/document/10441074*.

## Overview

Camera- and sensor-based people counting is costly or raises privacy concerns. WiFi CSI captures how
people in a room disturb the wireless channel, so occupancy can be estimated without cameras.

Pipeline:
1. **Hardware:** two pairs of ESP32 boards (one access point + one receiver per pair) using the ESP32 CSI Toolkit.
2. **Data collection:** CSI recorded in an indoor classroom for 1 to 7 people (8,140 samples, 7 classes).
3. **Preprocessing:** null subcarriers removed (64 → 52), amplitude extracted, labelled.
4. **Models:** compared a bagging ensemble and a CNN + LSTM network, evaluated with MAE.

## Models and results (from the thesis)

| Approach | Model | MAE |
|---|---|---|
| Machine learning | BaggingRegressor with LightGBM base estimator (also XGBoost, Random Forest) | 0.26 |
| Deep learning | Concatenated CNN + LSTM | 0.50 |

## Contact

Snaholata Mondal — snaholata.cse@iubat.edu
