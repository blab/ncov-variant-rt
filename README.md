# ncov-variant-rt
## About
Analysis of state-by-variant Rt estimates using CDC and GISAID data

Eslam Abousamra, John Huddleston, Marlin Figgins

This project involves a demonstration to build out a framework to perform comparative measurements of the effective reproductive number (Rt) using several methodologies, mostly involving Rstudio epidemiological tool packages which include EpiEstim (Cori A. et al., 2013), EpiNow (Abbott S. et al., 2020), ...

# Tidying Data

## Initial datasets

The SARS-CoV-2 genome data were obtained from the GISAID Initiative, please refer to https://www.gisaid.org for more information. To get access to the metadata dataset, register for a free GISAID account.

The SARS-CoV-2 daily case counts were obtained from the CDC, please refer to https://data.cdc.gov for more information.













## Exploratory Analysis

Here we fit a multinomial logistic regression on SARS-CoV-2 variant frequency growth (estimated from the GISAID metadata) and perfoming initial exploratory analysis and visualizing the competition among the lineages within divisions in the US. 

### Merging and Tidying the dataset 

1. Navigate in R the code found in the Rmd file below to merge the desired dataset (CDC & GISAID)

> Rt_dataset_tidy.Rmd


2. Output tidy dataset as

> write.csv(initial, "Rt_cdc&GISAID2.csv")


### Smoothing frequency (Multinomial Logistic Regression)

1. Navigate in R the code found in the Rmd file below to perform the MLR


> Expl_analysis_MLR.Rmd


2. Output tidy dataset with regression parameters as

> write.csv(final_mod, "Rt_MLR_cdc&GISAID.csv")









# Rt Estimation Analysis

## EpiEstim

Here we quantify transmissibility throughout an epidemic from the analysis of time series of incidence as described in Cori et al. (2013) on SARS-CoV-2 data.

### Installation

> install.packages("EpiEstim")


### Model Implementation





Citation: Anne Cori, Neil M. Ferguson, Christophe Fraser, Simon Cauchemez, A New Framework and Software to Estimate Time-Varying Reproduction Numbers During Epidemics, American Journal of Epidemiology, Volume 178, Issue 9, 1 November 2013, Pages 1505–1512.

















## EpiNow

Using this package, we can estimate Rt through a Bayesian variable approach using the probabilistic programming language Stan. According to a gaussian process, the fitted model of Rt is an multivariate normal distribution function. 


### Installation

> install.packages("EpiNow2")

### Model Implementation







Citation: Abbott SHellewell J, Sherratt K, Gostic K, Hickson J, Badr HS, DeWitt M, Thompson R, EpiForecasts , Funk S. 2020EpiNow2: estimate real-time case counts and time-varying epidemiological parameters. 




















