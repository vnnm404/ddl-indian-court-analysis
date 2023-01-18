# DDL Indian Court Analysis
This repository explores the [Development Data Lab](https://www.devdatalab.org/) dataset on cases recorded in the Indian Legal System. It finds and analysis patterns present in the data based on gender, year and criminality. It also explores whether case metadata is enough to determine whether a person is guilty or not; a model was trained for this purpose exactly and has scores high accuracy (0.97%).

All analysis is done with jupyter notebooks with python using libraries like pandas, numpy, matplotlib, sklearn and keras.

# Dependencies Required
Ensure `python3` is installed, then install the following libraries with `pip3`.
```
jupyterlab
pandas
numpy
matplotlib
pickle
sklearn
tensorflow
keras
```

First, clone the repository then `cd` into it, start `jupyterlab` in the directory with,
```
jupyterlab .
```
The notebooks can now be explored and run.

# Directory Structure
```
├───assets
│   └───india_plot
│       └───.vs
│           └───india_plot
│               └───v17
├───data
│   ├───cases
│   ├───keys
│   ├───_baked
│   │   └───ml
│   └───_raw
├───models
└───notebooks
    ├───.ipynb_checkpoints
    └───.virtual_documents
```

`/assets/` contains assets such as the data visualised as a sql database and an Indian statewise map details.
`/data/` contains the actual csv data that is worked with.
`/models/` contains the models that scored highly in terms of accuracy, they are stored as binary files and are loaded with the python library `pickle`.
`/notebooks/` contains the actual jupyter notebook where the code resides.

In the `/notebooks/`, 
* data_exploration notebooks are notebooks that explore the data trying to understand what data we can work with and how to work with it.
* analysis_ notebooks analyze the data to come to concrete insights such as the number of unresolved cases increases exponentially through the years.
* classification notebooks are attempts at classification problems given the data. 

# Big Data
The data consists of 66 million rows of data, this is quite a large amount of data and fitting all of it into memory was an impossibility. To handle such large data, the following measures were done,
* Chunking, by reading only some rows at a time into memory, analysis could be performed on that chunk and the results could be aggregated.
* Storing intermediate results, some cells in the notebooks take hours to run, however they often only need to be run once, the output is usually stored to disk in the `/data/_baked/` folder. This folder stores files that are used often and so they are computed once and stored. Filed created here are mentioned in the data_exploration notebooks.
* Although not needed for the above analysis, for especially large data, one could use parallalize all operations with libraries like `ray`, `modin`, and `dask`.

# Models Used
For the notebook with title "Classification ~ *The Sequel*", the below classifer achieved 97% accuracy in being able to classify whether the defendant was guilty or not.

RandomForestClassifer [download](https://mega.nz/file/QhlhFCKQ#slTnOrEGbmsX09NM0Ux4AHUT6XjPC5Mj8HcC2SZf_PQ)