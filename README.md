# automlk
Automated and distributed machine learning toolkit
--------------------------------------------------

This toolkit is designed to be integrated within a python project, but also independently through the interface of the app.

The framework is designed with similar principles than auto-sklearn, with the following improvements:
- web interface (flask) to review the datasets, the search results and graphs
- distributed architecture with multiple search workers
- include sklearn models, but also Xgboost, LightGBM, CatBoost and keras Neural Networks
- 2nd level ensembling with model selection and stacking
- can be used in competition mode (to generate a submit file from a test set), on public mode (separate train set and public set) and standard mode.

We have provided some public datasets to initialize the framework and compare results with best scores.

Find the documentation [here](http://automlk.readthedocs.io/en/latest/)

Installation
------------
download and then install:

    python setup.py install

Usage
-----

Launch the web app in /automlk-app folder:

    python run.py

This will launch the web app, which can be accessed via a web browser, at address:

    http://localhost:5001

From the web app, you can now import the example of datasets (import in the menu, then select the dataset.csv in the /data folder)

You can launch the search in a dataset simply by clicking on the |> button in the home screen, and view the results through with the web interface.
The search will continue automatically until the search is completed.


Requirements
------------
- category_encoders

optional:
- lightGBM
- Xgboost
- Catboost
- Keras with Theano or Tensorflow

- Redis (for in memory key/value storage and queues)

Architecture
------------

The architecture is distributed and can be installed on multiple machines
* the web app for user interaction and display results
* the controller manages the search between models and parameters
* the workers execute the pre-processing steps and cross validation (cpu intensive): the more workers are run in parallel, the quicker the results
* the Redis store is an in-memory database and queue manager

References
----------
Feurer, Matthias, et al. "Efficient and robust automated machine learning." Advances in Neural Information Processing Systems. 2015.
