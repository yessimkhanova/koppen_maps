# Köppen–Geiger Climate Map Generator


This project, part of a doctoral research conducted by **Kalamkas Yessimkhanova** under the supervision of Dr. Matyas Gede at Eötvös Loránd University, Budapest, utilizes Google Earth Engine and various datasets to generate Köppen–Geiger Climate Classification maps. These maps classify the climate of Kazakhstan and worldwide based on monthly mean temperature and precipitation amount parameters.


## Data Sources and Approaches
In this project, there are two approaches to generate Köppen maps in Google Earth Engine, depending on the data source:

### 1.	Using Earth Engine Dataset Collection (ERA5-Land, specific models of CMIP6 ensemble):
- Modify the script by adjusting the path to the collection.
- Update band names, check and modify units if necessary, and change metadata as required.

### 2.	Using Uploaded Data as an Asset (CRU, CMIP6):
- Modify the script by updating the path to the collection, filtering scenario and specifying the start and end times of the dataset.
- Adjust band names, check and modify units, and change metadata as needed.


## In the specific project context:

**ERA5-Land** use the first method as they are part of the Earth Engine dataset collection.

**CRU** data follows the second method since it is uploaded as an asset.

**CMIP6** data is available within the Earth Engine dataset collection, but its processing follows the second approach. 
This is because, in order to integrate CMIP6 data into the classification process, a series of preprocessing steps are required. These steps are outlined in three phases:
1.	Calculate ensemble monthly mean temperature and ensemble mean of monthly precipitation sum. Export images for each year with calculated monthly variables.
2.	Combine all yearly images into a multiband image.
3.	Apply Köppen classification to the prepared data.
Therefore, despite being part of the Earth Engine dataset collection, CMIP6 data needs additional processing steps, making it align with the second method of Köppen maps generation.


## GitHub Files Description

Each file in the repository is associated with a specific dataset:

**CMIP6:** Corresponds to the Climate Model Intercomparison Project Phase 6 (CMIP6) dataset **(historical, SSP2-4.5 and SSP5-8.5 scenarios data)**.

**CRU:** Corresponds to the Climatic Research Unit (CRU) dataset.

**ERA5-Land:** Corresponds to the ERA5-Land dataset.


### Explore the GEE Apps for Köppen Climate Classification

[Köppen Climate Classification GEE apps gallery](https://kalamkas.users.earthengine.app/) features following Köppen maps based on

- CRU data
- ERA5-Land data 
- CMIP6 ensemble, mean of 32 models (historical data, SSP 2-4.5 and SSP 5-8.5 scenario data) 
- Fusion model 1, GISS-E2-1-G (temperature data) and MIROC-ESL2L (precipitation data) models (historical data, SSP 2-4.5 and SSP 5-8.5 scenario data)
- Fusion model 2, CESM2 (temperature data) and BCC-CSM2-MR (precipitation data) models (historical data, SSP 2-4.5 and SSP 5-8.5 scenario data)

## Contact Information

For questions, comments, and feedback, please contact **Kalamkas Yessimkhanova**

**Email:** kalamkasyessimkhanova@gmail.com.

## Credits

Credit is given to the tools and datasets used in this work:
- Google Earth Engine (Gorelick, N., Hancher, M., Dixon, M., Ilyushchenko, S., Thau, D., & Moore, R. (2017). Google Earth Engine: Planetary-scale geospatial analysis for everyone. Remote Sensing of Environment.)
- NEX-GDDP-CMIP6: NASA Earth Exchange Global Daily Downscaled Climate Projections (Thrasher, B., Maurer, E. P., McKellar, C., & Duffy, P. B., 2012: Technical Note: Bias correcting climate model simulated daily temperature extremes with quantile mapping. Hydrology and Earth System Sciences, 16(9), 3309-3314. doi:10.5194/hess-16-3309-2012)
- ERA5-Land Monthly Aggregated - ECMWF Climate Reanalysis (Muñoz Sabater, J., (2019): ERA5-Land monthly averaged data from 1981 to present. Copernicus Climate Change Service (C3S) Climate Data Store (CDS). (<date 2024>), doi:10.24381/cds.68d2bb30)
- CRU dataset (World Bank, Climate Change Knowledge Portal (2024). URL: https://climateknowledgeportal.worldbank.org/. Date Accessed: 2024)
