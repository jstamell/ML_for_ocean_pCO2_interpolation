Strengths and weaknesses of three Machine Learning methods for pCO2 interpolation
==============================
Authors: Jake Stamell, Rea R. Rustagi, Lucas Gloege, Galen A. McKinley
- Columbia University, New York, NY 10027 USA
- Lamont-Doherty Earth Observatory, Palisades, NY 10964 USA

Abstract
------------
Using the Large Enemble Testbed, a collection of 100 members from four independent Earth system models, we test three general-purpose Machine Learning (ML) approaches to understand their strengths and weaknesses in statistically reconstructing full-coverage surface ocean pCO2 from sparse in situ data. To apply the Testbed we sample the full-field model pCO2 as real-world pCO2 collected from 1982-2016 for each ensemble member. We then use ML approaches to reconstruct the full-field and compare with the original model full-field pCO2 to assess reconstruction skill.  We use feed forward neural network (NN), XGBoost (XGB), and random forest (RF) approaches to perform the reconstructions. Our baseline is the NN, since this approach has previously been shown to be a successful method for pCO2 reconstruction. The XGB and RF allow us to test tree-based approaches. We perform comparisons to a test set, which consists of 20% of the real-world sampled data that are withheld from training. Statistical comparisons with this test set are equivalent to that which could be derived using real-world data. Unique to the Testbed is that it allows for comparison to all the "unseen" points to which the ML algorithms extrapolate. When compared to the test set, XGB and RF both perform better than NN based on a suite of regression metrics. However, when compared to the unseen data, degradation of performance is large with XGB and even larger with RF. However, degradation is relatively small with NN. Despite its larger degradation, XGB slightly outperforms NN and greatly outperforms RF against unseen data, with lower mean bias and more consistent performance across Testbed members. However, for the challenging task of reconstructing decadal variability, NN has the lowest overestimate of amplitude and the best reconstruction of phase. All three approaches perform best in the open ocean and for seasonal variability, but performance drops off at longer time scales and in regions of low sampling, such as the Southern Ocean and coastal zones. Even so, XGB is best able to reduce bias due to limited data coverage.

Steps to recreate this analysis
------------
	1. Clone the github repo: https://github.com/jstamell/ML_for_ocean_pCO2_interpolation
	2. Download data files from figshare and place in specified directories:
		a. /data/raw - raw ensemble member data in netcdf format - https://figshare.com/collections/Large_ensemble_pCO2_testbed/4568555
		b. /data/processed - Processed data stored in pandas dataframes
		c. /models/trained - Trained models, serialized in pickle or h5 format depending on the algorithm 
		d. /models/reconstructions - pCO2 reconstructions in netcdf format
		e. /models/performance_metrics/map_data_approach.pickle - map data for output plots
		f. /models/performance_metrics/map_data_ens.pickle - map data for output plots
	3. Follow the sequence of jupyter notebooks to recreate any of the files included in these repositories, aside from the raw data or jump to notebook 07_output_analysis.ipynb to explore the results
		a. The top of each notebook contains the values that should be adjusted by the user; this is typically just setting the path to the project's root directory on your system

Other notes
------------
- NN training evaluation may not be exactly reproducible, as Keras does not guarantee this when using multiple cores
- For any analysis on the temporal deconstructions, please note that the deconstructions of the actual member data is only stored with the RF reconstruction
- Some tables contain information on ensemble members beyond the 100 included in the LET; raw and processed data is not included on figshare for these additional members and all analysis used for the paper excludes them

Project Organization
------------

    ├── LICENSE
    ├── README.md          <- The top-level README for developers using this project.
	├── requirements.txt   <- Python module versions used
    ├── data
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks for recreating this analysis
    │
    ├── references         <- Data dictionaries and random seeds



--------