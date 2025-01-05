# GIS-DataScience_Pipeline

Using [PySAL library](http://pysal.org/pysal/) libraries to perform GeoSpatial Data Science on PostGIS-hosted data. We are performing these tasks through Jupyter NoteBooks, in the optics of using these methods in a full-scaled environnement featuring a PostGIS server to host datasets.

This series of Jupyter Notebooks are going though using Python's libraries in a database administration context. The first two Notebooks are written in French. I am writing the latest in English, as a mean to showcase my ability to present my work in english. I am supplying their download links in the Notebooks. The data is free and widely available.

## [VS Code Setup](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/0_VSCode_setup.ipynb)

It's a beginner's guide to setting up VS Code for SQL, Markdown and Python. It's dealing with installing the extension we need inside your virtual environments.

## [SQL use showcase (in French)](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/1_SQL.md)

The only file that is not a Jupyter NoteBook! It's a Markdown file. I originally sent it as a demo to my peers, as they were curious about my SQL proficiency. I am featuring a single, very short SQL request, but it is a mighty one. I am describing the purpose of the request, and the thinking process leading to the actual script. I wrote it while I was new to VS Code. I was pleased with its capabilities in being a PostGres client, which came handy for the jobs the next Notebooks are achieving.

## [PostGIS to GeoPandas](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/2_PostGIS_to_GeoPandas.ipynb)

In this NoteBook, we are manipulating Python to create a hexagonal grid over a geographical polygon. There is one parameter, the mesh size. We are using the results of the script in the next Notebooks. As I am discussing inside the Notebook, I could certainly have done that job in SQL if I had to in a production environnement. Still, the challenge allowed me to set a workflow from Python to PostGIS, and back, through SQL Alchemy's [binding parameters](https://docs.sqlalchemy.org/en/13/core/tutorial.html#specifying-bound-parameter-behaviors).

## [Tobler Spatial Interpolation](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/3_Spatial_Interpolation.ipynb)

We will use a complete dataset, and we will manipulate various interpolation variable categories (intensive & categorical), and we will combine the results in the hexagonal mesh we have calculated before. We are using the [Tobler Package](https://pysal.org/tobler/), which is part of [PySAL library](http://pysal.org/pysal/). This is done in a Jupyter Notebook. The code is built upon the previous Notebooks.

## [ESDA Spatial AutoCorrelation](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/4_Spatial_autocorrelation.ipynb)

We are making use of [Exploratory Spatial Data Analysis](https://pysal.org/esda/), which is also part of the [PySAL library](http://pysal.org/pysal/) to come up with a quantitative measure of how much neighboring cells are affecting each other. Our exeample is using the same dataset we have been using throughout, focusing on the population repartition over an administrative circonscription of France, the Hérault Département.

## [Map creation and Data visualization](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/5_maps_and_dataviz.ipynb)

The purpose of this notebook is to displaying a map of our data, nested with histograms pointing at their corresponding hexagonal cell on the map. 
In order to doing so, we are doing data manipulation in Python: sorting lists, creating dictionnaries of Panda's DataFrames. We are also using GridSpec to arranging several plots inside a single figure.
We are also using [Contextily](https://contextily.readthedocs.io/en/latest/reference.html) to enhance the visual experience.

## [PCA Using python](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/6_PCA.ipynb)

[PCA(Principal Component Analysis)](https://scikit-learn.org/stable/modules/decomposition.html#pca) is an unsupervised machine learning method allowing reduce the dimension of your data. It is the first method in the realm of data mining we are going to use and interpret.
Adapting [Ostwal Prasad](https://github.com/ostwalprasad/ostwalprasad.github.io/tree/master)'s Notebook to my workflow so I can pull an interpretation of a selected subset of the my PostGIS-hosted dataset from the previous Notebooks. This is the first Notebook featuring a [SciKit Learn](https://scikit-learn.org/stable/index.html) library.

## [Decision Tree and Random Forest Classifier](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/7_Descision_Tree_Random_Forest.ipynb)

Using the findings of our PCA to let a [Decision Tree](https://scikit-learn.org/stable/modules/tree.html) model predict the classes for the whole dataset from a few manually picked exeamples. We are using another [SciKit Learn](https://scikit-learn.org/stable/index.html) library here. We are using the [Random Forest classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) to performing the same process. We are using dictionnaries of datasets to perform a parallel analysis throughout on different subsets of our dataset. 

## [*k*-Nearest Neighbors](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/8_k-Nearest_Neighbors.ipynb)

We are using another [SciKit Learn](https://scikit-learn.org/stable/index.html) classifier. As per the Random Forest classifier, we are using the [*k*-Nearest Neighbors](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html) classifier to predict classes. We are then setting [elbow charts](https://en.wikipedia.org/wiki/Elbow_method_(clustering)) to determine our best value for *k*.
We are also making maps to have a sense of the established classification.

## [*k*-Means Neighbors](https://github.com/AdrienGahery/GIS-DataScience_Pipeline/blob/main/9_KMeans_Neighbors.ipynb)

[*k*-Means Neighbors](https://scikit-learn.org/stable/modules/clustering.html#k-means) is our first dip into clustering. We are performing a *k*-Means Neighbors clustering on a few different subsets. We are then trying to evaluate its performance with [calisnski-harabasz index](https://scikit-learn.org/stable/modules/clustering.html#calinski-harabasz-index), as well as trying out [Geosilhouettes](https://pysal.org/esda/notebooks/geosilhouettes.html). Lastly, we are trying to get a feel on how consistent the clustering is, given a few iterations.

We made creative use of Moran's ${I}$ [binary cases](https://pysal.org/esda/notebooks/spatialautocorrelation.html) throughout. This allowed us to quickly evaluate differences in clustering by the color palette of the resulting maps.
