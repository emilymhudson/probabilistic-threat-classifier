# Advanced Probabilistic Threat Classifier & Calibration Engine

## Overview
This repository implements an end-to-end deep learning classification and statistical calibration pipeline designed to mitigate Security Operations Center (SOC) alert fatigue. By resolving the inherent "over-confidence" of standard machine learning classifiers, this architecture guarantees probabilistic honesty—translating raw, uncalibrated deep learning logits into empirically accurate threat probabilities for automated triage routing.

## Core Architectural Capabilities

* **Deep Learning Feature Extraction:** Utilizes Hugging Face Transformer architectures (`DistilBERT`) to extract 768-dimensional contextual text embeddings from adversarial social engineering payloads, capturing deep linguistic intent rather than relying on brittle keyword matching.
* **Multi-Modal Matrix Synthesis:** Structurally synthesizes contextual text vectors with simulated high-dimensional ingestion metadata to replicate complex, multi-signal enterprise telemetry.
* **Post-Hoc Probability Calibration:** Implements Platt's Scaling (Sigmoid) via cross-validation to rigorously map predicted model confidence to true empirical event frequencies, drastically minimizing Expected Calibration Error (ECE).
* **Quantized Severity Routing:** Mathematically translates calibrated continuous floats into discrete, automated operational tiers (Tiers 1-5). This logic actively suppresses low-confidence indicators, resolving analyst alert fatigue safely.

## Evaluation & Optimization Metrics
Unlike traditional ML engineering that relies solely on accuracy or F1-scores, this pipeline is optimized for operational SOC integration. Core validation metrics include:
* **Brier Score Loss:** Quantifying the absolute mean squared difference between predicted probabilities and actual outcomes.
* **Expected Calibration Error (ECE):** Measuring the discrepancy between accuracy and confidence across bounded probability bins.
* **ROC-AUC & Precision/Recall Yield:** Ensuring baseline discriminatory power remains intact post-calibration.

## Execution & Usage
The pipeline requires a cloud or local environment with `torch`, `transformers`, and `scikit-learn` installed.

```bash
# Execute the comprehensive classification and calibration pipeline
python Comprehensive_Pipeline.py
