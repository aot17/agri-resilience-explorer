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

## 2026-07-12

### Cropland Analysis

To better represent agricultural conditions, vegetation analysis was restricted to cropland pixels using the ESA WorldCover land-cover dataset.

### Accomplishments

- Integrated ESA WorldCover into the analysis workflow.
- Computed monthly cropland NDVI time series.
- Built a combined cropland NDVI–rainfall dataset.
- Compared rainfall and cropland vegetation dynamics.

### Key Learnings

- County-wide NDVI can include vegetation unrelated to agriculture.
- Land-cover masking enables a more representative measure of agricultural vegetation.
- Vegetation response to rainfall remains strongest with a one-month lag after restricting the analysis to cropland.

### Results

Correlation between cropland NDVI and rainfall:

- Same month rainfall: 0.24
- Rainfall lagged by 1 month: 0.69
- Rainfall lagged by 2 months: 0.65

The lagged relationship remained strong after masking non-agricultural land, suggesting that cropland vegetation responds to rainfall over several weeks rather than immediately.

## 2026-06-13

### Drought Response Framework

The project evolved from descriptive time-series analysis toward measuring agricultural resilience to climatic stress.

### Accomplishments

- Extended the analysis period to 2020–2024.
- Developed a methodology to identify candidate drought events from rainfall time series.
- Built a workflow to quantify vegetation decline following drought events.
- Implemented recovery metrics based on pre-drought vegetation conditions.
- Generated the first resilience indicators for Makueni County.

### Key Learnings

- Drought detection and vegetation response should be treated as separate analytical steps.
- Candidate drought events do not necessarily lead to measurable vegetation decline.
- Recovery metrics require defining a baseline, a response window, and an objective recovery criterion.

### Methodology

The resilience workflow now consists of:

1. Monthly rainfall analysis.
2. Candidate drought event detection.
3. Cropland vegetation response analysis.
4. Recovery time estimation.
5. Resilience indicator computation.

This establishes a reusable framework that can be applied to additional counties without modifying the overall methodology.