# Bayesian Modeling of Public Transport Delays

This project explores how different Bayesian regression models perform when predicting public transport departure delays. The focus is on comparing several model structures that can handle the characteristics commonly seen in delay data, such as a spike at zero (on-time departures) and heavy positive tails for larger delays.

The models are implemented in **Stan** and run locally through **CmdStanPy** inside a Jupyter notebook.

---

## Project Overview

Public transport delay data has several features that make modeling difficult: many observations have zero delay, while others show highly skewed positive values. To study how different modeling approaches handle these properties, this project implements and compares four Bayesian models.

The goal is not only to fit the data but also to evaluate how well each model predicts delays and captures the underlying structure of the dataset.

---

## Models Implemented

Four models were built and compared:

**Model A – Student-t regression**  
A robust baseline model applied to a log-transformed delay variable.

**Model B – Two-regime Student-t mixture regression**  
A mixture model designed to capture different delay regimes in the data.

**Model C – Hurdle lognormal model**  
A two-part model separating zero delays from positive delays.

**Model D – Hierarchical Student-t regression**  
A model with route-level partial pooling to account for route-specific variation.

---

## Dataset

The analysis uses the dataset **“Public Transport Delays with Weather and Events”** from Kaggle.

https://www.kaggle.com/datasets/khushikyad001/public-transport-delays-with-weather-and-events/data

The main response variable is the **departure delay in minutes**.

For several models the response is transformed as:

`y = log(1 + delay_minutes)`

The dataset also contains additional covariates such as route identifiers, temporal features, weather indicators, and other operational variables.

---

## Workflow

The notebook follows a structured workflow:

1. Data loading and preprocessing  
2. Feature construction and design matrix creation  
3. Model implementation in Stan  
4. Bayesian inference using CmdStanPy  
5. Diagnostic checks and posterior summaries  
6. Posterior predictive checks  
7. Model comparison using **PSIS-LOO**

---

## Main Result

Among the tested models, the **two-component Student-t mixture model (Model B)** showed the best predictive performance under PSIS-LOO comparison.

---

## Repository Structure

- **ABDA_Local.ipynb** – main notebook containing the analysis  
- **stan_models/** – Stan model definitions used in the notebook  
- **requirements.txt** – Python dependencies required to run the project  
- **report.pdf** – final project report

---

## Requirements

Main Python libraries used:

- cmdstanpy  
- arviz  
- pandas  
- numpy  
- matplotlib  
- scipy  
- kagglehub

A working **CmdStan installation** is required to run the models.

---

## Authors

Abhishek Mishra  
Siddhant Mishra  

Advanced Bayesian Data Analysis  
TU Dortmund University