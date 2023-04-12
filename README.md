# README for the data from https://doi.org/10.14459/2022mp1655470

filenames_train_val_test_split: this folder includes .txt files which specify the train - val - test split for the networks trained for the paper.

images_annotation_experiment_geotiff: this folder includes 26 images, one for each building labeled in the annotation experiment. Images are downloaded
using the Google Maps Static API. The images are georeferenced to be able to create the masks from the georeferenced annotation data. On github, you can
find code to save the geotiffs as .pngs

images_roof_centered_geotiff: this folder includes 1880 images downloaded using the Google Maps Static API. The images are georeferenced to be able to
create the masks from the georeferenced annotation data.

masks_segments_reviewed: this folder includes 1880 masks for semantic segmentation of roof segments. Masks contain values from 0-17 which refer to the
classes background, 16 azimuth classes (e.g. south, south-east etc.) and flat. You can create masks with different class configurations with our code on github.
The masks are derived from the labels in the version “reviewed”, meaning after the first revision step. You can find the initial annotations and code to generate
respective masks on github.

masks_superstructures_annotation_experiment: this folder includes 130 masks which function as test dataset for our paper. The masks are derived from the 26
images and include annotations of 5 different labelers for the 26 buildings.

masks_superstructures_reviewed: this folder includes 1880 masks for semantic segmentation of roof superstructures. Masks contain values with respect to
superstructure classe (e.g. pvmodule, window, etc.). See the paper for more information. You can create masks with different class configurations with our code
on github. The masks are derived from the labels in the version “reviewed”, meaning after the first revision step. You can find the initial annotations and code to
generate respective masks on github. 

# Some notes from Jelly
use shapely < 2, otherwise it will not work

# RID - Roof information dataset
This code refers to the publication "RID—Roof Information Dataset for Computer Vision-Based Photovoltaic Potential Assessment", https://doi.org/10.3390/rs14102299.

This repository includes datasets for semantic segmentation of roof superstructures and roof roof segments. The code supports data preparation, training and model evaluation. Furthermore, it includes the labels of an annotation experiment with five labelers and its evaluation.
 
## Getting Started
- First clone the repository
- Download required raster data (images and masks) from https://doi.org/10.14459/2022mp1655470
- Create a folder with the name "segmentation_model_data" and copy "filenames_train_val_test_split" to this folder
- Copy all other data folders into the "data" folder
 
### Prerequisites
Required packages are included in the requirements.txt.
 
### Installing
When running the code on Windows, packages fiona, gdal, and geopandas need to be installed from wheel files. 
When using Python 3.7, package dataclasses is already included in python and can be deleted from requirements.txt.
Code can be used with Python 3.9 by installing packages from requirements_python_39.txt

## Running the Model/Code
The whole pipeline can be run using main.py. The steps include:
1) Create roof superstructure masks from vector labels
2) Create roof segment masks from vector labels
3) Analyze the dataset
4) Evaluate annotation experiment and visualize results
5) Train model for semantic segmentation of superstructure 
6) Evaluate model and visualize results
7) Conduct PV potential assessment

The pipeline can be run using different input datasets:
1) initial labels (with inferior label quality)
2) reviewed labels (with enhanced label quality)

Settings should be defined in definitions.py

It is recommended to run parts of the pipeline seperately, e.g. when training the model for semantic segmentation of roof segments, or when optimizing the model parameters.
 
## Deployment
Built With [Python](https://www.python.org/) 3.6

## Versioning
V0.1 Initial version
 
## Authors
Author: Sebastian Krapf

## Contributors
Fabian Netzler, 
Lukas Bogenrieder, 
Nils Kemmerzell

## Credits
This work would not have been possible without numerous python packages such as keras, segmentation models, shapely, geopandas, and more. See requirements.txt for packages used.

## License
1) This project is licensed under the LGPL License - see the LICENSE.md file for details

2) The use of Google Satelite Images is allowed under principles of fair use. Images can be used for non-commercial purposes such as news, blogs, educational, recreational, or instructional use. For information, see: https://about.google/brand-resource-center/products-and-services/geo-guidelines/

