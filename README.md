# RWS hysteresis FE-ML explorer

Static GitHub Pages-style GUI for the European IPE circular reduced web section (RWS) hysteresis database.

The app shows, for each database record:

- FE cyclic moment-rotation history.
- FE backbone envelope in FE benchmark mode.
- Calibrated mIK hysteresis reconstruction.
- Machine-learning predicted mIK hysteresis reconstruction.
- Hysteresis overlays for FE, calibrated mIK and predicted mIK curves.
- Added-curve comparison so a pinned model can be compared with another selected model.
- Matched von Mises and PEEQ contour images.
- Calibrated and predicted mIK labels used in the Engineering Structures draft.

Mode behaviour:

- FE benchmark mode shows FE hysteresis, optional FE backbone, and calibrated mIK hysteresis only.
- ML prediction mode shows FE hysteresis, calibrated mIK hysteresis, and predicted mIK hysteresis; FE backbone is not shown in this mode.

The app is intentionally chunked by `Profile + Grade + 2L/h`. This keeps the initial page load small while still covering the full 7,575-record laterally restrained database.

## Local preview

Run a static server from this folder:

```powershell
python -m http.server 8765
```

Then open:

```text
http://127.0.0.1:8765/
```

Opening `index.html` directly with `file://` is not recommended because browsers usually block JSON `fetch()` calls from local files.

## Data provenance

Generated from:

- `restrained_calibrated_rws_database_20260507.csv`
- `laterally_restrained_rws_hysteresis_histories_7575.csv`
- FE backbone arrays are extracted from cyclic reversal points in the same histories shown in the GUI.
- mIK hysteresis curves are reconstructed with OpenSees IMKBilin internally, but the GUI labels them as mIK curves for consistency.
- `compiled_contours_GitHub_ready_LR/contours` for the laterally restrained contour images.
- the same train-validation split and model family used in the Engineering Structures draft.

Full hysteresis point arrays are exported for each record. Metrics are computed on the full arrays.
