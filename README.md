# Confidence-Aware Speech Classification (Prototype)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]([PASTE_YOUR_COLAB_LINK_HERE](https://colab.research.google.com/drive/1Ax9a9JcOzdX1bQDAyFXQRsFKbX95dxOd#scrollTo=TYgV8LZ4USOs))
Prototype exploring calibration and predictive reliability for transformer-based models, motivated by Alzheimer’s disease detection in clinical settings.

## What’s in this repo
- `calibration_demo.ipynb`: end-to-end demo (baseline → temperature scaling → reliability metrics)
- `reliability_before.png`, `reliability_after.png`: reliability diagrams

## Key idea
In clinical applications, calibrated probabilities can be as important as accuracy. This prototype evaluates reliability using:
- Negative Log-Likelihood (NLL)
- Expected Calibration Error (ECE)
- Brier score

## Calibration
Temperature scaling is fitted on a validation split.
Observation from initial experiments:
- NLL improves consistently after scaling
- ECE can be sensitive to binning choices (histogram-based metric)
- Brier score provides a more stable complementary view
## Results

### Baseline validation performance

- **Accuracy:** 0.895  
- **F1 score:** 0.897  

### Calibration analysis

- **NLL before scaling:** 0.2629  
- **NLL after scaling:** 0.2608  
- **Learned temperature:** T ≈ 1.11  

Temperature scaling consistently reduced negative log-likelihood, indicating improved probabilistic fit. 

Reliability diagrams suggest mild overconfidence in high-confidence regions prior to scaling, which becomes slightly attenuated after calibration.

Histogram-based ECE exhibited sensitivity to bin configuration, highlighting the instability of binning-based calibration metrics. The Brier score provided a more stable complementary assessment of predictive reliability.
## Next steps
- Selective prediction (accuracy–coverage trade-off)
- MC Dropout uncertainty estimation
- Borderline-case analysis for safe deployment
