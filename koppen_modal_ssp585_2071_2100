// CORRECTED
var path = "FAO/GAUL_SIMPLIFIED_500m/2015/level0"; var country_code = 132; // Set the country code for Kazakhstan.
var country = ee.FeatureCollection(path).filter(ee.Filter.eq('ADM0_CODE', country_code)); // Filter the country feature collection for Kazakhstan.

var model1 = ee.Image('users/kalamkas/corrected_koppen_models_modal/ACCESS-CM2_koppen_ssp585_2071_2100').select('zone');
var model2 = ee.Image('users/kalamkas/corrected_koppen_models_modal/BCC-CSM2-MR_koppen_ssp585_2071_2100').select('zone');
var model3 = ee.Image('users/kalamkas/corrected_koppen_models_modal/CESM2_koppen_ssp585_2071_2100').select('zone');
var model4 = ee.Image('users/kalamkas/corrected_koppen_models_modal/MIROC-ES2L_koppen_ssp585_2071_2100').select('zone');
var model5 = ee.Image('users/kalamkas/corrected_koppen_models_modal/ACCESS-ESM1-5_koppen_ssp585_2071_2100').select('zone');
var model6 = ee.Image('users/kalamkas/corrected_koppen_models_modal/CESM2-WACCM_koppen_ssp585_2071_2100').select('zone');
var model7 = ee.Image('users/kalamkas/corrected_koppen_models_modal/CMCC-CM2-SR5_koppen_ssp585_2071_2100').select('zone');
var model8 = ee.Image('users/kalamkas/corrected_koppen_models_modal/ACCESS-CM2_koppen_ssp585_2071_2100').select('zone');
var model9 = ee.Image('users/kalamkas/corrected_koppen_models_modal/CMCC-ESM2_koppen_ssp585_2071_2100').select('zone');
var model10 = ee.Image('users/kalamkas/corrected_koppen_models_modal/CNRM-CM6-1_koppen_ssp585_2071_2100').select('zone');
var model11 = ee.Image('users/kalamkas/corrected_koppen_models_modal/CanESM5_koppen_ssp585_2071_2100').select('zone');
var model12 = ee.Image('users/kalamkas/corrected_koppen_models_modal/EC-Earth3-Veg-LR_koppen_ssp585_2071_2100').select('zone');
var model13 = ee.Image('users/kalamkas/corrected_koppen_models_modal/EC-Earth3_koppen_ssp585_2071_2100').select('zone');
var model14 = ee.Image('users/kalamkas/corrected_koppen_models_modal/FGOALS-g3_koppen_ssp585_2071_2100').select('zone');
var model15 = ee.Image('users/kalamkas/corrected_koppen_models_modal/GFDL-CM4_koppen_ssp585_2071_2100').select('zone');
var model16 = ee.Image('users/kalamkas/corrected_koppen_models_modal/GFDL-ESM4_koppen_ssp585_2071_2100').select('zone');
var model17 = ee.Image('users/kalamkas/corrected_koppen_models_modal/HadGEM3-GC31-LL_koppen_ssp585_2071_2100').select('zone');
var model18 = ee.Image('users/kalamkas/corrected_koppen_models_modal/INM-CM4-8_koppen_ssp585_2071_2100').select('zone');
var model19 = ee.Image('users/kalamkas/corrected_koppen_models_modal/INM-CM5-0_koppen_ssp585_2071_2100').select('zone');
var model20 = ee.Image('users/kalamkas/corrected_koppen_models_modal/IPSL-CM6A-LR_koppen_ssp585_2071_2100').select('zone');
var model21 = ee.Image('users/kalamkas/corrected_koppen_models_modal/KACE-1-0-G_koppen_ssp585_2071_2100').select('zone');
var model22 = ee.Image('users/kalamkas/corrected_koppen_models_modal/KIOST-ESM_koppen_ssp585_2071_2100').select('zone');
var model23 = ee.Image('users/kalamkas/corrected_koppen_models_modal/MIROC6_koppen_ssp585_2071_2100').select('zone');
var model24 = ee.Image('users/kalamkas/corrected_koppen_models_modal/MPI-ESM1-2-HR_koppen_ssp585_2071_2100').select('zone');
var model25 = ee.Image('users/kalamkas/corrected_koppen_models_modal/MPI-ESM1-2-LR_koppen_ssp585_2071_2100').select('zone');
var model26 = ee.Image('users/kalamkas/corrected_koppen_models_modal/NESM3_koppen_ssp585_2071_2100').select('zone');
var model27 = ee.Image('users/kalamkas/corrected_koppen_models_modal/HadGEM3-GC31-MM_koppen_ssp585_2071_2100').select('zone');
var model28 = ee.Image('users/kalamkas/corrected_koppen_models_modal/NorESM2-MM_koppen_ssp585_2071_2100').select('zone');
var model29 = ee.Image('users/kalamkas/corrected_koppen_models_modal/TaiESM1_koppen_ssp585_2071_2100').select('zone');
var model30 = ee.Image('users/kalamkas/corrected_koppen_models_modal/UKESM1-0-LL_koppen_ssp585_2071_2100').select('zone');
var model31 = ee.Image('users/kalamkas/corrected_koppen_models_modal/MRI-ESM2-0_koppen_ssp585_2071_2100').select('zone');
var model32 = ee.Image('users/kalamkas/corrected_koppen_models_modal/CNRM-ESM2-1_koppen_ssp585_2071_2100').select('zone');


var koppenCollection = ee.ImageCollection([
  model1, model2, model3, model4, model5, model6, model7, model8,
  model9, model10, model11, model12, model13, model14, model15, model16,
  model17, model18, model19, model20, model21, model22, model23, model24,
  model25, model26, model27, model28, model29, model30, model31, model32
]);

var modelCount = koppenCollection.size();

var modalKoppen = koppenCollection
  .reduce(ee.Reducer.mode())
  .rename('modal_zone')
  .clip(country);

var zonecount = []; 

function matchi(img) { return img.eq(i).rename('agree'); }
var n = 32; // number of zones
for (var i = 0; i < n; i++ ) {
  var imeq = koppenCollection.map(matchi);
  zonecount[i] = imeq.reduce(ee.Reducer.sum()).rename('count');
}

var arrayImg = ee.ImageCollection(zonecount).toArrayPerBand();
// Map.addLayer(arrayImg,{},'zone counts'); // only for debugging - this way we can inspect the array image at any location
Map.setCenter(67.5, 48.0, 4);

// Generate an index array image
var indicesImage = ee.Image(ee.Array(ee.List.sequence(0, n-1)));

// Sort the indices array image by based on the values array image
var sortedIndices = indicesImage.arraySort(arrayImg);
// Then sort the values array image
var sortedArrayImg = arrayImg.arraySort();

var best1 = sortedIndices.arrayGet(n-1);
var best2 = sortedIndices.arrayGet(n-2);
var best1cnt = sortedArrayImg.arrayGet(n-1);
var best2cnt = sortedArrayImg.arrayGet(n-2);

// Assume sortedIndices and sortedArrayImg are defined from earlier
var best1Img = sortedIndices.arraySlice(0, n-1, n).arrayProject([0]).arrayFlatten([['best1']]).toInt16();
var best2Img = sortedIndices.arraySlice(0, n-2, n-1).arrayProject([0]).arrayFlatten([['best2']]).toInt16();
var best1cntImg = sortedArrayImg.arraySlice(0, n-1, n).arrayProject([0]).arrayFlatten([['best1cnt']]).toInt16();
var best2cntImg = sortedArrayImg.arraySlice(0, n-2, n-1).arrayProject([0]).arrayFlatten([['best2cnt']]).toInt16();

// Create the result image with the four bands
var resultImg = best1Img
  .addBands(best2Img)
  .addBands(best1cntImg)
  .addBands(best2cntImg);

// Define the region of interest (optional, you can change the geometry as needed)
var roi = ee.Geometry.Rectangle([45, 38, 90, 55]); // Adjust to your needs

// Add artificial constant bands (with value 1) to each of the four bands
var resultImgWithConstant = resultImg
  .addBands(ee.Image(1).rename('best1_constant'))
  .addBands(ee.Image(1).rename('best2_constant'))
  .addBands(ee.Image(1).rename('best1cnt_constant'))
  .addBands(ee.Image(1).rename('best2cnt_constant'));

// Reduce to vectors for each band (now with two bands)
var best1Vectors = resultImgWithConstant.select(['best1', 'best1_constant']).reduceToVectors({
  reducer: ee.Reducer.count(),
  scale: 1000,
  maxPixels: 1e8,
  geometryType: 'polygon',
  labelProperty: 'best1',
  geometry: roi
});

var best2Vectors = resultImgWithConstant.select(['best2', 'best2_constant']).reduceToVectors({
  reducer: ee.Reducer.count(),
  scale: 1000,
  maxPixels: 1e8,
  geometryType: 'polygon',
  labelProperty: 'best2',
  geometry: roi
});

var best1cntVectors = resultImgWithConstant.select(['best1cnt', 'best1cnt_constant']).reduceToVectors({
  reducer: ee.Reducer.count(),
  scale: 1000,
  maxPixels: 1e8,
  geometryType: 'polygon',
  labelProperty: 'best1cnt',
  geometry: roi
});

var best2cntVectors = resultImgWithConstant.select(['best2cnt', 'best2cnt_constant']).reduceToVectors({
  reducer: ee.Reducer.count(),
  scale: 1000,
  maxPixels: 1e8,
  geometryType: 'polygon',
  labelProperty: 'best2cnt',
  geometry: roi
});

// Combine the vectorized features into a single FeatureCollection
var combinedVectors = best1Vectors
  .merge(best2Vectors)
  .merge(best1cntVectors)
  .merge(best2cntVectors);

// // Export the combined vectorized result as a single shapefile
// Export.table.toDrive({
//   collection: combinedVectors,
//   description: 'Combined_Polygons',  // Name for the exported shapefile
//   folder: 'GEE_Exports',  // Folder in your Google Drive
//   fileFormat: 'SHP'  // Export as Shapefile
// });



var koppenColors = [
  "000000", "0000FF", "4169E1", "6495ED", "00BFFF",
  "FF0000", "F08080", "FF8C00", "FFD700", "98FB98",
  "3CB371", "2E8B57", "ADFF2F", "00FF00", "32CD32",
  "FFFF00", "BDB76B", "808000", "7B68EE", "6A5ACD",
  "483D8B", "191970", "00FFFF", "87CEFF", "008080",
  "2F4F4F", "FF00FF", "9400D3", "800080", "D8BFD8",
  "A9A9A9", "696969"
];

// Add the modal Köppen class layer
Map.addLayer(modalKoppen, {
  min: 0,
  max: 31,
  palette: koppenColors
}, 'Modal Köppen Class');


var projectTitleLabel = ui.Label({ // Creates a label widget for the project title.
  value: 'Confidence in Climate Models: Köppen Climate Classification',
  style: {
    fontWeight: 'bold',
    fontSize: '24px',
    margin: '0px 0 0 0',
    textAlign: 'center',
    width: '100%'
  }
});

var infoPanel = ui.Panel({ // Creates a panel to display information about the project.
  widgets: [ // Contains multiple label widgets with project information.
    ui.Label('This work is part of a doctoral research project conducted by Kalamkas Yessimkhanova, supervised by Dr. Matyas Gede at ELTE Eötvös Loránd University, Budapest. ', { fontSize: '14px' }),
    ui.Label('This map is part of the research presented in the Köppen Climate Map Generator repository https://github.com/yessimkhanova/koppen_maps. ', { fontSize: '14px' }),
    ui.Label('The map classifies climate of Kazakhstan based on monthly mean temperature and precipitation amount parameters using CMIP6 datasets to generate future Köppen Climate Classification maps. ', { fontSize: '14px' }),
    ui.Label('This work specifically focuses on the confidence among 32 models from the CMIP6 ensemble for the SSP585 scenario (2071-2100). The confidence levels in the maps show how much agreement there is among the models regarding specific climate zones. Higher confidence levels indicate a stronger consensus among the climate models, while lower confidence levels suggest greater uncertainty.', { fontSize: '14px' }),
    ui.Label('Confidence Levels: ', { fontSize: '14px', fontWeight:'bold'}),
    ui.Label('The confidence levels shown in this map reflect the degree of agreement between the climate models. Models with higher agreement lead to stronger confidence in predicting climate zones, while areas with low model agreement show lower confidence in the projections. ', { fontSize: '14px', fontWeight:'bold'}),
    ui.Label('Credit is given to Google Earth Engine for its powerful geospatial analysis capabilities and NASA/Climate Analytics Group for providing valuable climate data. ', { fontSize: '14px' }),
    ui.Label('Please contact Kalamkas Yessimkhanova for questions, comments, and feedback. ', { fontSize: '12px' }),
    ui.Label('Email: kalamkasyessimkhanova@gmail.com', { fontSize: '12px', fontWeight: 'bold'}),
    
   ],
  style: {
    width: '350px'
  }
});

var leftMainPanel = ui.Panel({
  style:{
    width: '390px',
    position: 'middle-left',
    padding: '10px'
  }
});

leftMainPanel.add(infoPanel);
Map.add(projectTitleLabel);
Map.add(leftMainPanel);

var colorizedModalKoppen = modalKoppen.visualize({
  min: 0,
  max: 31,
  palette: koppenColors
});





