*Disclaimer - Domino Reference Projects are starter kits built by Domino researchers. They are not officially supported by Domino. Once loaded, they are yours to use or modify as you see fit. We hope they will be a beneficial tool on your journey!

# Dask Reference Project

This reference project covers the various functionality that Dask has to offer. There are three files that contain the code for this project

* [dask_data_analysis.ipynb](dask_data_analysis.ipynb) : This file has infographics that show the different collections and components that are available in Dask. In this file we analyse the NYC Taxi cab dataset and show how to load the dataset, subset the data, run statistical analysis and remove outliers. Along with the results, the shapes of the Dask collections and the task graphs that executed behind the scenes are also plotted. The purpose of this file is to illustrate how a user can run data analysis and exploration on a dataset using Dask's inbuilt functions. The data that has been used for analysis is available at ```s3://dask-reference-project-data/``` folder. For the data to be available to all the Dask nodes seamlessly, please upload this data as a [Domino Dataset](https://docs.dominodatalab.com/en/5.0/user_guide/0a8d11/domino-datasets/).

* [pso.ipynb](pso.ipynb) : This file is an example of how to solve an optimisation problem in Dask. The particle swarm optimiser algorithm has been implemented in this file and is meant to serve as an example of running a compute intensive task using Dask. In this particular case, we split the search space into a grid and the PSO algorithm finds a minima for each cell of the grid. Once the minima of all the cells in the grid have been computed, the lowest of these minima is reported as the global minima of the optimisaton

* [dask_ml.ipynb](dask_ml.ipynb) : This file demonstrates the different capabilities that are part of the Dask ML framework and how it integrates with the PyData ecosystem. There are examples of model training, pipelines and model inference in this file that covers the ML model development aspect of the development lifecycle


## Setup instructions

This project requires the following [compute environments](https://docs.dominodatalab.com/en/latest/user_guide/f51038/environments/) to be present:

### dask_2022.1.0_workspace

**Environment Base** 

`quay.io/domino/dask-environment:ubuntu18-py3.8-r4.1-dask2022.1.0-domino5.1`

**Dockerfile Instructions**

```
USER root
RUN apt-get install graphviz -y
RUN pip install numba graphviz
USER ubuntu
```

**Pluggable Workspace Tools**


```
jupyter:
  title: "Jupyter (Python, R, Julia)"
  iconUrl: "/assets/images/workspace-logos/Jupyter.svg"
  start: [ "/opt/domino/workspaces/jupyter/start" ]
  httpProxy:
    port: 8888
    rewrite: false
    internalPath: "/{{ownerUsername}}/{{projectName}}/{{sessionPathComponent}}/{{runId}}/{{#if pathToOpen}}tree/{{pathToOpen}}{{/if}}"
    requireSubdomain: false
  supportedFileExtensions: [ ".ipynb" ]
jupyterlab:
  title: "JupyterLab"
  iconUrl: "/assets/images/workspace-logos/jupyterlab.svg"
  start: [  /opt/domino/workspaces/jupyterlab/start ]
  httpProxy:
    internalPath: "/{{ownerUsername}}/{{projectName}}/{{sessionPathComponent}}/{{runId}}/{{#if pathToOpen}}tree/{{pathToOpen}}{{/if}}"
    port: 8888
    rewrite: false
    requireSubdomain: false
vscode:
  title: "vscode"
  iconUrl: "/assets/images/workspace-logos/vscode.svg"
  start: [ "/opt/domino/workspaces/vscode/start" ]
  httpProxy:
    port: 8888
    requireSubdomain: false
rstudio:
  title: "RStudio"
  iconUrl: "/assets/images/workspace-logos/Rstudio.svg"
  start: [ "/opt/domino/workspaces/rstudio/start" ]
  httpProxy:
    port: 8888
    requireSubdomain: false
```

### dask_2022.1.0_cluster

**Environment Base** 

``quay.io/domino/dask-environment:ubuntu18-py3.8-r4.1-dask2022.1.0-domino5.1``

**Supported Cluster Settings**

Dask


**Dockerfile Instructions**

```
USER root
RUN apt-get install graphviz -y
RUN pip install numba graphviz
USER ubuntu
```
