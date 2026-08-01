# 📡 IMD High-Resolution Spatial Climate Pipeline & Extreme Heatwave Monitoring System

An end-to-end Python-based Geospatial & Spatial-Temporal Climate Analytics Engine designed to process synthetic IMD 3D grid data ($10 \times 10$ spatial grid across 30 temporal days), perform Land/Sea masking, compute baseline climatology, apply spatial noise reduction, and isolate extreme heatwave hotspots using percentile thresholding.

---

## 📊 Executive Analytics Dashboard

![IMD Executive Analytics Dashboard](Imd_Heatwave_Executive_Dashboard.png)

---

## 🚀 Key Features & Pipeline Architecture

1. *Phase 1: Spatial Data Ingestion & Land/Sea Masking*
   - Synthesized a 3D Temporal-Spatial Array (30 Days x 10 Lat x 10 Lon).
   - Built a dynamic binary matrix mask (1.0 for Land, 0.0 for Sea) to isolate terrestrial thermal dynamics using np.nan values.

2. *Phase 2: Baseline Climatology & Z-Score Anomaly Engine*
   - Calculated pixel-wise spatial climatological mean ($\mu$) and standard deviation ($\sigma$) using np.nanmean and np.nanstd.
   - Identified extreme regional thermal deviations using the Z-Score engine:
     $$Z = \frac{X - \mu}{\sigma}$$
   - Flagged extreme heatwaves where $Z > 1.5$.

3. *Phase 3: 2D Spatial Smoothing & Symmetric Edge Padding*
   - Implemented np.pad(..., mode='symmetric') (Mirror Padding) to eliminate boundary distortion artifacts.
   - Applied a $3 \times 3$ Spatial Convolution Kernel via scipy.signal.convolve2d(..., mode='valid') for sensor noise reduction.

4. *Phase 4: 90th Percentile Thresholding & Hotspot Isolation*
   - Computed regional thermal extremes using np.nanpercentile(..., 90).
   - Isolated critical warning zones by filtering grid values exceeding the 90th percentile threshold.

---

## 🛠️ Tech Stack & Tools

- *Language:* Python 3.x
- *Core Analytics:* NumPy, SciPy (convolve2d)
- *Data Visualization:* Matplotlib
- *Environment:* Jupyter Notebook / JupyterLab

---

## 💻 How to Run

1. Clone the repository:
   ```bash
   git clone [https://github.com/isaacantony2805-afk/IMD-Spatial-Climate_Pipeline.git](https://github.com/isaacantony2805-afk/IMD-Spatial-Climate_Pipeline.git)
