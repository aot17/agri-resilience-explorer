## 2026-06-08

- Repository created
- Earth Engine configured
- First Sentinel-2 image displayed from Kenya
- Learned:
  - Earth Engine evaluates lazily
  - getInfo() should be used carefully
  - Large global queries can timeout

## 2026-06-09

Computed first NDVI map for Makueni County.

Mean NDVI:
0.5423

### Key learning:
NDVI is a vegetation indicator derived from NIR and Red reflectance.
The project is now producing environmental measurements rather than just satellite imagery.

## 2026-06-10

### Objective

Build a monthly NDVI time series for Makueni County.

### Accomplishments

- Created a reusable monthly_mean_ndvi() function.
- Computed monthly average NDVI for Makueni from 2023-01 to 2024-12.
- Exported results to CSV.
- Produced first NDVI time-series plot.

### Key Learnings

- NDVI is computed from Sentinel-2 bands B8 (NIR) and B4 (Red).
- reduceRegion() converts an image into a summary statistic.
- Monthly composites provide a cleaner vegetation signal than individual images.

### Observations

- NDVI generally peaks between December and May.
- January 2023 appears less vegetated than January 2024.
- This may be related to rainfall differences and should be investigated.

### Next Steps

- Build monthly rainfall time series using CHIRPS.
- Compare rainfall and NDVI trends.

## 2026-06-11

### Rainfall–Vegetation Relationship

Correlation between monthly NDVI and rainfall:

- Current month rainfall: 0.35
- Rainfall lagged by 1 month: 0.69
- Rainfall lagged by 2 months: 0.54

Observation:

Vegetation appears to respond more strongly to rainfall from the previous month than to rainfall occurring in the same month.

This suggests a lagged vegetation response, likely due to the time required for rainfall to affect soil moisture and plant growth.