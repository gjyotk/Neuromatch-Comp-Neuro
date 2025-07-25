# Differential Motor Intent Decoding in ECoG: Hand vs Tongue Movements

Repository for processing, analyzing, and visualizing electrocorticography (ECoG) data recorded during real and imagined motor tasks. Focus is on high‑gamma band (70–200 Hz) dynamics and channel‑wise responses for overt and imagined hand vs. tongue movements.

## Introduction

- **Electrocorticography (ECoG):** Records brain activity directly from the cortical surface, capturing high‑frequency signals in the high‑gamma band (70–200 Hz).  
- **Motor Execution Connection:** High‑gamma activity reflects neural processes during movement.  
- **BCI Applications:** Enables brain‑computer interfaces (BCIs) for neurorehabilitation—benefiting patients with stroke, paralysis, or movement disorders.

## Background

- **Key Challenge:** Distinguishing actual vs. imagined movement in single‑trial ECoG recordings remains difficult.  
- **Impact on BCIs:** Limits development of reliable, personalized clinical BCIs.  
- **Study Objective:** Investigate whether high‑gamma power can differentiate executed vs. imagined hand and tongue movements.

## Dataset

**Source:**  
- Collected by Dr. Kai Miller’s team at Stanford (2019 dataset).  
- 7 epilepsy patients performing motor (hand, tongue) and language tasks.

**Contents:**  
- Raw & preprocessed ECoG signals  
- Task‑onset annotations  
- Subject demographics  
- Electrode locations (registered to cortical surfaces)

**Why This Dataset?**  
- High‑resolution ECoG during overt vs. imagined movements  
- Clear labels for real execution vs. motor imagery  

## Preprocessing

- Extract voltage data from Brodmann Areas 2, 3, 4, 6, 9, 43, 45 (motor & sensory regions).  
- Band‑pass filter and downsample as needed.  
- Epoch around events (−0.2 s to +0.9 s) with baseline correction.

## Feature Extraction

1. **PSD via Welch’s Method**  
   - Compute per trial & electrode.  
   - Flatten frequency × channel matrix into 1D vector.  
2. **Dimensionality Reduction**  
   - Apply PCA → 11 principal components.  
3. **Labels**  
   - `0` = hand movement  
   - `1` = tongue movement  

## Key Findings

<img width="1398" height="682" alt="Screenshot 2025-07-24 at 12 16 38 AM" src="https://github.com/user-attachments/assets/768280fb-ea2b-4aef-b100-d38f69983909" />

<img width="610" height="545" alt="Screenshot 2025-07-24 at 4 42 48 PM" src="https://github.com/user-attachments/assets/8386a183-be58-4969-87b2-6529f14ab78c" />

- **Temporal Dynamics**  
  - Executed hand movements: rapid, high‑amplitude gamma surges peaking ~0.3–0.5 s after onset.  
  - Imagined tongue movements: smaller, delayed gamma increases in the same window.

- **Spatial Localization**  
  - **Hand Execution:** High‑gamma enhancements in primary motor cortex (Brodmann 4, 6).  
  - **Tongue Imagery:** Weaker activity in ventral regions (Brodmann 43, 45).

- **Single‑Trial Specificity**  
  - Channel‑wise comparisons at peak times confirm region‑specific patterns on each trial.
