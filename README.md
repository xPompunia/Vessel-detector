# Vessel Detector

Automated retinal blood vessel detection in fundus images — pixel-wise binary
classification (vessel / background), comparing three approaches of increasing
complexity:

1. **Image processing** — preprocessing → Frangi filter → Otsu thresholding → morphology
2. **Classical ML** — Random Forest on image patches with feature extraction
3. **Deep learning** — U-Net (PyTorch)

Everything lives in a single notebook (`vessel_detector.ipynb`), including EDA,
hyperparameter search, metrics (ROC/PR curves, confusion matrices), method
comparison, and a small interactive GUI.

## Project structure

```
Vessel-detector/
├── vessel_detector.ipynb   # the whole pipeline
├── requirements.txt
├── data/                   # images + expert masks + FOV (not tracked)
│   ├── images/
│   ├── manual1/            # expert masks (gold standard)
│   └── mask/               # FOV masks
├── models/                 # saved models (RF, U-Net) (not tracked)
└── results/                # visualisations and metrics
```

## Getting the data

The images are not included due to size. Download one of the supported datasets
and unpack it as follows:

- original images → `data/images/`
- expert (gold standard) masks → `data/manual1/`
- field-of-view (FOV) masks → `data/mask/`

Supported datasets:

- **HRF**: https://www5.cs.fau.de/research/data/fundus-images/
- **STARE**: http://cecas.clemson.edu/~ahoover/stare/probing/
- **CHASE**: https://blogs.kingston.ac.uk/retinal/chasedb1/

## Running

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook vessel_detector.ipynb
```
