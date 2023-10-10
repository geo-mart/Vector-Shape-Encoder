# Polygon encoding

## Code
* [Polygon encoding notebook](polygon_encoding.ipynb) for polygons
* [Polyline encoding notebook](polyline_encoding.ipynb) for polylines
* [Template matching notebook](template_matching.ipynb) for the case study

Just change the hyperparameters, select the features by commenting/uncommenting them in the list and run the code.

## Data
* [Link to repository of the building data set](https://figshare.com/articles/dataset/GCN-based_building_shape_coding_and_cognition_in_maps-Data_Codes/11742507) from [Yan et al. (2021)](https://doi.org/10.1080/13658816.2020.1768260) 
* [Coastline data](data/coastlines.shp): Coastline data, manual selection from © [European Marine Observation and Data Network (EMODnet)](https://emodnet.ec.europa.eu/en/geology) 
* [Case study data](data/case_study.shp): Buildings from the area of the case study in Beijing, © OpenStreetMap contributors
* [Building Templates](data/templates.shp): Manual selection from the dataset of [Yan et al. (2021)](https://doi.org/10.1080/13658816.2020.1768260) (see above)
* [Dense building data](data/map_area.shp): Manipulated data of [Yan et al. (2021)](https://doi.org/10.1080/13658816.2020.1768260) to be used for map-based normalization, as the buildings are in a smaller area

## How to for the case study

1. Train the models as described above with [the polygon encoding notebook](polygon_encoding.ipynb).
2. Predict the classes for the buildings in the case study and export as follows (example for 'RNN' model):
```
pred_case_study = {'index': [i for i in range(len(predictions))],
        'osm_id_ret': id_list,
        'clas_prediction': predictions,
        'shape_prediction': shape_predictions}
predictionsDF = pd.DataFrame(pred_case_study)
predictionsDF.to_csv('predictions_case_study-RNN.csv')
```
3. Repeat for other models if wanted.
4. Open [the template matching notebook](template_matching.ipynb), load the csv-file and run the code.
