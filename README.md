# Vessel Detector — Segmentacja naczyń dna oka

Projekt 2 z przedmiotu Informatyka w Medycynie. Detekcja naczyń krwionośnych
na obrazach dna siatkówki oka (binarna klasyfikacja piksela: naczynie / tło).

## Struktura projektu

```
Vessel-detector/
├── vessel_detector.ipynb   # główny notebook z całym pipeline'em
├── requirements.txt        # zależności
├── data/                   # obrazy + maski eksperckie + FOV (np. baza HRF)
│   ├── images/
│   ├── manual1/            # maski eksperckie (gold standard)
│   └── mask/               # maski FOV
├── models/                 # zapisane modele (RF, U-Net)
└── results/                # wyniki, wizualizacje, metryki
```

## Pobieranie danych

Ze względu na rozmiar, obrazy nie są dołączone (folder data).
Przed odpaleniem programu pobierz dane z ponizszych zbiorów danych i rozpakuj według schematu:

- Obrazy oryginalne powinny trafić do `data/images/`
- Maski eksperckie (tzw. Gold Standard) trafiają do `data/manual1/`
- Maski widoczności (Field of View / FOV) trafiają do `data/mask/`

Linki do obsługiwanych zbiorów danych:

- **HRF**: https://www5.cs.fau.de/research/data/fundus-images/
- **STARE**: http://cecas.clemson.edu/~ahoover/stare/probing/
- **CHASE**: https://blogs.kingston.ac.uk/retinal/chasedb1/

## Uruchomienie

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook vessel_detector.ipynb
```

## Zakres realizacji

- [x] Wymagania obowiązkowe — przetwarzanie obrazu (filtr Frangi'ego + morfologia)
- [x] Wymagania na 4.0 — klasyfikator ML (np. Random Forest) na wycinkach z ekstrakcją cech
- [x] Wymagania na 5.0 — U-Net (PyTorch)
