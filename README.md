# Classroom Occupancy Estimation using WiFi Channel State Information (CSI)

Estimating the number of people in a classroom from WiFi CSI collected with low-cost ESP32
microcontrollers. This repository contains the machine learning and deep learning code from my
B.Sc. thesis at CUET (Dept. of CSE, supervised by Dr. Asaduzzaman), published at
**ICCIT 2023** — *[TODO: add full paper title, DOI/IEEE Xplore link]*.

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

*[TODO: re-run the notebooks and confirm these numbers; see "Notes" below.]*

## Repository structure

```
notebooks/
  01_cnn_lstm_concat_model.ipynb          # CNN + LSTM, input reshaped to 13x4
  02_ensemble_bagging_lgbm_xgb_rf.ipynb   # Bagging ensemble with GridSearchCV
data/
  README.md                               # expected data format
requirements.txt
```

## Getting started

```bash
git clone https://github.com/<your-username>/wifi-csi-classroom-occupancy.git
cd wifi-csi-classroom-occupancy
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

Place `labelled_final.csv` in `data/` and change the path in the first data-loading cell
(the notebooks currently read `/content/labelled_final.csv`, a Colab path).

## Notes

- Train/validation split is 75/25. Please check that the final model is evaluated only on data
  it did not train on before quoting results.

## Citation

```
[TODO: add BibTeX for the ICCIT 2023 paper]
```

## Contact

Snaholata Mondal — snaholata.cse@iubat.edu
