# Using Bayesian Hierarchical Models to Analyze Graduation Rates in New York State 
![](https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/banner.jpg)
#
*Author: Kevin Alexis Mendez*
## Prerequisites
This project was ran using a `WINx64` operating system. To replicate the environment used, download the `.txt` file located in the `requisites` folder in this repository. Running the following code will allow you to generate the same `conda env` used throughout this project.
```
conda env create -- file <file_name.txt>
```

`PyMC3` may present environmental issues. To resolve this, create a separate environment to use when constructing the Bayesian models. Running the following code will create a new environment and install `PyMC3`. Additionally, the `multilevel modeling.ipynb` notebook uses `GraphViz` to visualize the model architecture. Running `pip install graphviz` will download `GraphViz` to the respective environment. In order to visualize/generate the DOT source code, `GraphViz` must be installed to the system PATH [here](https://www.graphviz.org/)

## Stakeholder Understanding 

## Overview

## Data

## Method 

## Linear Mixed Effects Model (LMER)  
   
## Bayesian Hierarchical Modeling 


### Complete Pooling Approach
<p align="center">
  <img width="460" height="300" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/pooledmodel.png">
</p>


### Unpooled/No Pooling Approach
<p align="center">
  <img width="460" height="300" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/unpooledmodel.png">
</p>

### Hierarchical Modeling (w. Varying Intercepts)
![](https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/varying_ic_model.png)


## Model Evaluation 

### Posterior Predictive Check 
<p align="center">
  <img width="640" height="480" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/posterior_predictive_check.png">
</p>


### Data Suppression & Potential Biases 
<p align="center">
  <img width="912" height="547" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/graduationrates_subgroup.png">
</p>

<p align="center">
  <img width="912" height="390" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/missingvals_dist.png">
</p>

## Key Insights 

## Next Steps 
## Acknowledgements & Credits 
