# Data

The notebooks expect a file named `labelled_final.csv` (no header):

- columns 0–51: CSI amplitude values for 52 subcarriers (null subcarriers removed from the original 64)
- column 52: label, the number of people in the room (1 to 7)

Dataset size: 8,140 samples, 7 classes, collected with two ESP32 transmitter/receiver pairs.

**TODO before publishing:** state whether the CSV is shared (e.g., a Zenodo/Kaggle/Google Drive link)
or available on request. Do not commit it to GitHub if it is large or if CUET requires permission.
