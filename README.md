### Note: Due to repository size limitations, the following files are not included:
- Building_Footprint_20250311.geojson-Available for download via the link provided below.
- S2_sample.tiff-Can be generated using the Sentinel2_GeoTIFF.ipynb notebook.



# 1. Files and Data Sources
- Additional Data:
    -  Weather Data
    -  Building Footprint from Google Map
- NYC Open Data: [Building_Footprint_20250311.geojson](https://drive.google.com/file/d/1BQwBDrGNoi7mBtN36OiSU6pxapmvLqqe/view?usp=sharing)


- Satellite Features: Landsat 8 and Sentinel 2

- Training Data:
    - Longitude
    - Latitude
    - Datetime
    - UHI Index

# 2. Methodology
### Weather Data
- Use osmnx to identify and extract areas of interest (e.g., Manhattan, The Bronx).
- Match and merge training data with corresponding weather data based on location and timestamp.

### Building Footprint
- Create a 700m buffer around each training point.
- Within each buffer:
    - Count the number of buildings.
    - Calculate total building area.
    - Compute mean shape compactness.

### Building Metrics (NYC Open Data)
- Within each buffer:
    - Calculate average building height.
    - Estimate building density.
    - Compute Floor Area Ratio (FAR).

### Spectral Indices from Satellite Imagery
Landsat 8 / Sentinel 2:
- Extract bands to calculate:
    - NDVI (Normalized Difference Vegetation Index)
    - NDBI (Normalized Difference Built-up Index)
    - NDWI (Normalized Difference Water Index)
    - Emissivity
- Derive Land Surface Temperature (LST) from Landsat 8.

# 3. Modeling
- Combine all engineered features into a final dataset.
- Train a Random Forest Regression model to predict the Urban Heat Island (UHI) Index.

# 4. Future improvement (upcoming updates)
- Model Enhancement:
    - Integrate XGBoost for better performance and compare with Random Forest.
    - Apply hyperparameter tuning for optimal results.
- Data Quality: Calibrate Land Surface Temperature (LST) for improved accuracy in UHI estimation.
