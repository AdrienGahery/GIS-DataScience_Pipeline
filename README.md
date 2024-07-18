# GIS-DataScience_Pipeline

Using PySAL libraries and Tobler package to perform GeoSpatial Data Science on PostGIS-hosted data. We're performing these tasks through Jupyter NoteBoks. 

This series of Jupyter Notebooks are going step-by-step though using Python's libraries in a database administration context. The first two notebooks are in French. Don't let this hinder you from having a peek, they're very approachable. I'm picking from the results from script to script to perform the treatments therein. The data is free, and available on the internet. I'm supplying their download links.

## VS Code Setup 

It's a beginner's guide to setting up VS Code for SQL, Markdown and Python once you've installed it. It's also dealing with virtual environments. Written in French.

## SQL use showcase

The only file that isn't a Jupyter NoteBook! It's originally sent as a demo to my french peers, as they were curious about my SQL proficiency. It's in French, the request is a mighty one, but the main takeaway from it is you can use VS Code as a postgres client.

## PostGIS to GeoPandas 

In this NoteBook, we're manipulating Python to create a hexagonal grid over a geographical polygon. There is one parameter, the mesh size. We're using the results of the script throughout. As I'm discussing inside the Notebook, I'm knowingly taking some routes that aren't the optimal ones. This document is mostly meant to getting to know the tools I'm using, and letting me reuse tidbits of commands that I consider useful in the future.

## Tobler Spatial Intepolation

We're not yet *guessing* the data from its position relative to known data, we'll play with a complete and reliable dataset, and we'll manipulate various interpolation variable categories (intensive & categorical), and we'll combine the results in the hexagonal mesh we've calculated before.

## Soon to expect...

Soon to expect is some SciKit Learn usage on the dataset I'm building.

Feel free to give any feedback ! :)

Yours,

Adrien
