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
This project seeks to leverage the hierarchical nature of the data, using statistical methods, to investigate the relative effects of student demographics on graduation outcomes. Prior analysis revealed that standard linear regression and multivariate regression fail to extract robust insights because of said hierarchical structure. Thus, this project utilizes Bayesian inference to 

## Data
Data was compiled from the New York State Education Department’s Open Data [site](https://data.nysed.gov/). The original dataset has a hierarchical structure where information is compiled and grouped at the school level and across nine different student subgroups. Features were extracted from other datasets on the NYSED Open Data site including county, district name, and need-to-resource capacity index.

Target subgroups include: 

- Hispanic or Latinx Students
- English Language Learners
- Students with Disabilities
- White Students
- Black and African American Students
- American Indian or Alaska Native Students
- Asian/Pacific Islander/Native Hawaiian Students
- Economically Disadvantaged Students
- Multiracial Students
  
## Method 
Taking advantage of the hierarchical nature of the data, traditional linear regression methods were insufficient to map out relative effect differences between the graduation outcomes across different subgroups. 

## Linear Mixed Effects Model (LMER)  
A Linear Mixed Effects Regression Model was first tested to understand the significance of random effects (i.e., student subgroup) while controlling for the variance of subgroup. After modeling, insights were considered within the scope of an `$alpha$` = .05.  Three subgroups were determined to have statistically significant effects: 

- English Language Learners have **~15%** lower graduation rate compared to other subgroups
- Hispanic or Latinx students have **~4%** lower graduation rate compared to other students
- Students with Disabilities have **~10%** lower graduation rate compared to other students


## Bayesian Hierarchical Modeling 
Bayesian Hierarchical Modeling with `PyMC3` provides a powerful methodological approach, leveraging prior information and Bayesian methods to approximate the parameters of the posterior distribution. This method allows for the interpretation of results within a degree of uncertainty. 

### Complete Pooling Approach
<p align="center">
  <img width="460" height="300" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/pooledmodel.png">
</p>

For ease of interpretation and to build up a logical understanding of the Bayesian hierarchical model, a simple model that considers the effect of a single subgroup (i.e., Hispanic or Latinx Student). The complete pooling approach estimates a single graduation rate while treating all counties the same. This approach is the most basic and common approach, however, fails to estimate county-level differences. 

### Unpooled/No Pooling Approach
<p align="center">
  <img width="460" height="300" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/unpooledmodel.png">
</p>

The unpooled approach estimates graduation rates for each county (n=62), however, this approach can lead to uncertain estimates where counties have inadequate measurements across different predictor variables. 

### Hierarchical Modeling (w. Varying Intercepts)
![](https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/varying_ic_model.png)

The hierarchical approach provides a balance between both pooled and unpooled approaches for estimating graduation rates. In the Bayesian approach, priors, likelihood, and estimated functions can be modified and adjusted to reflect the underlying distribution of observed data in order to create robust predictions. In the following approach, a hierarchical model was built under the assumption of varying intercepts at the county-level (a group-level predictor). Thus, we assume there to be variation in base graduation rates across counties. 

## Model Evaluation 

### Posterior Predictive Check 
<p align="center">
  <img width="640" height="480" src="https://github.com/asoylatte03/nys-ell-grad-rate/blob/main/images/posterior_predictive_check.png">
</p>

To evaluate the overall fit of the model after Markov-Chain Monte-Carlo sampling methods, a posterior predictive check was conducted. Because of the non-normal distribution that explains the observed data, a normal or Gaussian prior and likelihood function proved ineffective at capturing the variance in the underlying data. The model fails to capture higher-probable observations where graduations rates > 82%. 

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
