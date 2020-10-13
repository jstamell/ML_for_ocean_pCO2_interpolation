Strengths and weaknesses of three Machine Learning methods for pCO2 interpolation
==============================
Authors: Jake Stamell, Rea R. Rustagi, Lucas Gloege, Galen A. McKinley
- Columbia University, New York, NY 10027 USA
- Lamont-Doherty Earth Observatory, Palisades, NY 10964 USA

This repository contains code related to the paper of the above title. The paper has been submitted to the Geoscientific Model Development journal, and a link to the paper will be posted when available.

Using the Large Enemble Testbed, a collection of 100 members from four independent Earth system models, we test three general-purpose Machine Learning (ML) approaches to understand their strengths and weaknesses in statistically reconstructing full-coverage surface ocean pCO2 from sparse in situ data.

Steps to recreate this analysis
------------
- Clone the github repo: https://github.com/jstamell/ML_for_ocean_pCO2_interpolation
- Download data files from figshare and place in specified directories:
	- /data/raw - raw ensemble member data in netcdf format - https://figshare.com/collections/Large_ensemble_pCO2_testbed/4568555
	- /data/processed - Processed data stored in pandas dataframes
	- /models/trained - Trained models, serialized in pickle or h5 format depending on the algorithm 
	- /models/reconstructions - pCO2 reconstructions in netcdf format
	- /models/performance_metrics/map_data_approach.pickle - map data for output plots
	- /models/performance_metrics/map_data_ens.pickle - map data for output plots
- Follow the sequence of jupyter notebooks to recreate any of the files included in these repositories, aside from the raw data or jump to notebook 07_output_analysis.ipynb to explore the results
	- The top of each notebook contains the values that should be adjusted by the user; this is typically just setting the path to the project's root directory on your system

Other notes
------------
- NN training evaluation may not be exactly reproducible, as Keras does not guarantee this when using multiple cores
- For any analysis on the temporal deconstructions, please note that the deconstructions of the actual member data is only stored with the RF reconstruction
- Some tables contain information on ensemble members beyond the 100 included in the LET; raw and processed data is not included on figshare for these additional members and all analysis used for the paper excludes them

Project Organization
------------

    ├── LICENSE
    ├── README.md          
	├── requirements.txt   <- Python module versions used
    ├── data
    │   ├── processed      <- The processed data sets used for modeling (available at <insert link>)
    │   └── raw            <- The original LET member data (available at https://figshare.com/collections/Large_ensemble_pCO2_testbed/4568555)
    │
    ├── models             <- Trained and serialized models, model predictions, and performance metrics (available at <insert link>)
    │
    ├── notebooks          <- Jupyter notebooks for recreating this analysis
    │
    ├── references         <- Data dictionaries and random seeds



--------
