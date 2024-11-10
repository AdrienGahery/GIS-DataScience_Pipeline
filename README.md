# GIS-DataScience_Pipeline

Using [PySAL library](http://pysal.org/pysal/) libraries to perform GeoSpatial Data Science on PostGIS-hosted data. We're performing these tasks through Jupyter NoteBooks, in the optics of using these methods in a full-scaled environnement featuring a PostGIS server to host datasets.

This series of Jupyter Notebooks are going though using Python's libraries in a database administration context. The first two Notebooks are written in French. I'm writing the latest in English, as a mean to showcase my ability to present my work in english. I'm supplying their download links in the Notebooks. It's free and widely available.

## VS Code Setup

It's a beginner's guide to setting up VS Code for SQL, Markdown and Python. It's dealing with installing the extension we need inside your virtual environments.

## SQL use showcase [in French]

The only file that isn't a Jupyter NoteBook! It's a Markdown file. I originally sent it as a demo to my peers, as they were curious about my SQL proficiency. I'm featuring a single, very short SQL request, but it is a mighty one. I'm describing the purpose of the request, and the thinking process leading to the actual script. I wrote it while I was new to VS Code. I was pleased with its capabilities in being a PostGres client, which came handy for the jobs the next Notebooks are achieving.

## PostGIS to GeoPandas

In this NoteBook, we're manipulating Python to create a hexagonal grid over a geographical polygon. There is one parameter, the mesh size. We're using the results of the script in the next Notebooks. As I'm discussing inside the Notebook, I could certainly have done that job in SQL if I had to in a production environnement. Still, the challenge allowed me to set a workflow from Python to PostGIS, and back, through SQL Alchemy's [binding parameters](https://docs.sqlalchemy.org/en/13/core/tutorial.html#specifying-bound-parameter-behaviors).

## Tobler Spatial Interpolation

We'll use a complete dataset, and we'll manipulate various interpolation variable categories (intensive & categorical), and we'll combine the results in the hexagonal mesh we've calculated before. We're using the [Tobler Package](https://pysal.org/tobler/), which is part of [PySAL library](http://pysal.org/pysal/). This is done in a Jupyter Notebook. The code is built upon the previous Notebooks.

## ESDA Spatial AutoCorrelation

We're making use of [Exploratory Spatial Data Analysis](https://pysal.org/esda/), which is also part of the [PySAL library](http://pysal.org/pysal/) to come up with a quantitative measure of how much neighboring cells are affecting each other. Our exeample is using the same dataset we've been using throughout, focusing on the population repartition over an administrative circonscription of France, the Hérault Département.

## Map creation and Data visualization

The purpose of this notebook is to displaying a map of our data, nested with histograms pointing at their corresponding hexagonal cell on the map. 
In order to doing so, we're doing data manipulation in Python: sorting lists, creating dictionnaries of Panda's DataFrames. We're also using GridSpec to arranging several plots inside a single figure.
We're also using [Contextily](https://contextily.readthedocs.io/en/latest/reference.html) to enhance the visual experience.

## PCA Using python

[PCA(Principal Component Analysis)](https://scikit-learn.org/stable/modules/decomposition.html#pca) is an unsupervised machine learning method allowing you reduce the dimension of your data. It is the first method in the realm of data mining we're going to use and interpret.
Adapting [Ostwal Prasad](https://github.com/ostwalprasad/ostwalprasad.github.io/tree/master)'s Notebook to my workflow so I can pull an interpretation of a selected subset of the my PostGIS-hosted dataset from the previous Notebooks. This is the first Notebook featuring a [SciKit Learn](https://scikit-learn.org/stable/index.html) library.

## Decision Tree and Random Forest Classifier

Using the findings of our PCA to let a [Decision Tree](https://scikit-learn.org/stable/modules/tree.html) model predict the classes for the whole dataset from a few manually picked exeamples. We are using another [SciKit Learn](https://scikit-learn.org/stable/index.html) library here. We are using the [Random Forest classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) to performing the same process. We are using dictionnaries of datasets to perform a parallel analysis throughout on different subsets of our dataset. 

## Soon to expect !

Soon to expect is some more [SciKit Learn](https://scikit-learn.org/stable/index.html) in the next Notebook! Applying a supervised machine learning method on my PostGIS-hosted dataset.

Feel free to give any feedback ! :)

Yours,

Adrien
