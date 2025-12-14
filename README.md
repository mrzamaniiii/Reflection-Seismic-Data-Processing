# Seismic Reflection Data Processing

## Overview

This repository documents the complete processing workflow applied to a Common Shot seismic reflection gather (RRAW.SGY). The project aims to convert raw field data into a clear stacked section by systematically addressing noise, determining the subsurface velocity structure, and enhancing resolution. The processing was primarily performed using the Reflexw software environment.

## Data Acquisition Specifications

| Parameter | Value |
| :--- | :--- |
| **Data Type** | Common Shot Gather |
| **Number of Channels** | 59 |
| **Spread Type** | Off-end |
| **Group Interval** | $\approx 12.3 \text{ m}$ |
| **Minimum Offset** | $33 \text{ m}$ (First Group) |
| **Maximum Offset** | $747 \text{ m}$ (Last Group) |
| **Initial Sample Rate** | $2 \text{ ms}$ (Implied, as data was resampled to $1 \text{ ms}$) |
| **Trace Length** | $2.0 \text{ SEC.}$ |

## Processing Workflow Sequence

The raw data was subjected to a rigorous processing sequence aimed at noise suppression, accurate velocity modeling, and high-resolution stacking.

### 1. Data Conditioning & Filtering
* **Resampling:** Standardized the temporal resolution to $1 \text{ ms}$.
* **Bandpass Filtering:** Applied a Butterworth filter with a lower cutoff of $10 \text{ Hz}$ to attenuate low-frequency Ground Roll energy.
* **FK Filtering (Two-Stage):**
    * **Stage 1:** Targeted residual Ground Roll removal.
    * **Stage 2:** Performed aliasing removal and further noise attenuation, carefully preserving near-surface reflections at long offsets.

### 2. Muting
* **First Arrival Muting:** Applied a custom muting curve to remove noise and linear events arriving earlier than the first reflections. 

### 3. Velocity Analysis (VA) & Stacking
* **Optimization:** Used the Semblance operator with an optimized $40 \text{ ms}$ time window for better velocity picking, as the window size is comparable to the wavelet duration.
* **Modeling:** Generated a 2D velocity model.
* **Stack:** Applied NMO corrections using the 2D model and produced the Single Trace Stack.

### 4. Resolution Enhancement
* **Deconvolution:** Applied Spectral Whitening (zero-phase deconvolution) to the stacked trace to flatten the spectrum and improve vertical resolution. 
