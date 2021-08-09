# ncov-variant-rt
## About
Analysis of state-by-variant Rt estimates using CDC and GISAID data

Eslam Abousamra, Marlin Figgins, John Huddleston, Trevor Bedford

This project involves a demonstration to build out a framework to perform measurements of the effective reproductive number (Rt) using bayesian inference methods of estimation, mostly involving Rstudio epidemiological tool packages which include EpiEstim (Cori A. et al., 2013), EpiNow (Abbott S. et al., 2020). In addition to questioning the effect of interventions such as vaccination and address prediction limitations and biases.

# Tidying Data

## Initial datasets

The SARS-CoV-2 genome data were obtained from the GISAID Initiative, please refer to https://www.gisaid.org for more information. To get access to the metadata dataset, register for a free GISAID account.

![Image 7-28-21 at 12 55 PM](https://user-images.githubusercontent.com/84752326/127387246-86b53335-837a-4240-aa14-aaba9ee0a62c.jpg)

### Sanitize metadata using Nextstrain platform
Please refer to https://docs.nextstrain.org/en/latest/tutorials/SARS-CoV-2/steps/data-prep.html to filter and sanitize metadata to fit the notebook

The SARS-CoV-2 daily case counts were obtained from the CDC, please refer to https://data.cdc.gov for more information.













## Exploratory Analysis

Here we fit a multinomial logistic regression on SARS-CoV-2 variant frequency growth (estimated from the GISAID metadata) and perfoming initial exploratory analysis and visualizing the competition among the lineages within divisions in the US. 

### Merging and Tidying the dataset 

1. Navigate in R the code found in the Rmd file below to merge the desired dataset (CDC & GISAID)

> Rt_dataset_tidy.Rmd


2. Output tidy dataset as

> write.csv(initial, "Rt_cdc&GISAID2.csv")


### Initial Analysis: Smoothing frequency (Multinomial Logistic Regression)

1. Navigate in R the code found in the Rmd file below to input tidy dataset and perform the MLR 


> Rt_MLR_tidy.Rmd

## Visualizing smoothed frequencies for lineages of concern (B.1.1.7, B.1.351, P.1, B.1.427, B.1.617)
list obtained from the cdc and can be altered according to the desired analysis, please refer to https://www.cdc.gov/coronavirus/2019-ncov/variants/variant-info.html for a complete SARS-CoV-2 Variant Classifications

![pred_freq](https://user-images.githubusercontent.com/84752326/128755422-ac2fb5aa-4987-44f3-ade1-e5e7f2349933.png)


## Visualizing Cross Validation of smoothed frequencies 

![arranged_cv1](https://user-images.githubusercontent.com/84752326/128755447-6aefb113-3529-4c4c-88a7-53839d29a330.png)






2. Output tidy dataset with regression parameters to pass in the estimation models as

> write.csv(final_mod, "Rt_MLR_cdc&GISAID.csv")










# Rt Estimation Analysis

## EpiEstim

Here we quantify transmissibility throughout an epidemic from the analysis of time series of incidence as described in Cori et al. (2013) on SARS-CoV-2 data.

*Citation: Anne Cori, Neil M. Ferguson, Christophe Fraser, Simon Cauchemez, A New Framework and Software to Estimate Time-Varying Reproduction Numbers During Epidemics, American Journal of Epidemiology, Volume 178, Issue 9, 1 November 2013, Pages 1505–1512.*

### Installation

> install.packages("EpiEstim")


### Model Implementation

1. Navigate in R the code found in the Rmd file below to run the analysis for the tidy data

> 06-28-21-Rt_EpiEstim_1.Rmd




## Visualizing Rt estimated from the EpiEstim package on a number of states 

![epiestim_r](https://user-images.githubusercontent.com/84752326/128755489-587fc3f2-2e32-4ea2-bfcd-7b6f8cf5efee.png)










## EpiNow

Using this package, we can estimate Rt through a Bayesian variable approach using the probabilistic programming language Stan. According to a gaussian process, the fitted model of Rt is an multivariate normal distribution function. 

*Citation: Abbott SHellewell J, Sherratt K, Gostic K, Hickson J, Badr HS, DeWitt M, Thompson R, EpiForecasts , Funk S. 2020EpiNow2: estimate real-time case counts and time-varying epidemiological parameters.*


### Installation

> install.packages("EpiNow2")

### Model Implementation

1. Navigate in R the code found in the Rmd file below to run the analysis for the tidy data

> 07-01-21-Rt_EpiNow_2.Rmd 

























