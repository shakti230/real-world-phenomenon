# real-world-phenomenon
# Mary McDonagh
# Programming for Data Analysis
# GMIT 2018


## Table of Contents
#### 1.0 Overview
#### 2.0 Prerequisites
#### 3.0 Github
#### 4.0 Summary
#### 5.0 References


## 1.0 Overview
This repository is intended to review the following in detail:
- Simulate a real world phenomenon which allows me to collect 100 data points across 4 variables. Use the numpy package to create this.
- Investigate the types of variables involved, their likely distributions and their relationships with each other.
- Sumulate a data set matching their properties as closely as possible.
- Detail my research and output the simulation using a Jupyter notebook.

As part of my research and investigation I chose to review data of world econometric factors in order to analyse the associations between the world GDP per capita, life expectancy, population, birth rate and neo natal mortality rate. This project is based on a pre existing dataset taken from the world databank indicators portal. The datset is called nations.csv.

The five variables reviewed in the project are as follows:
- gdp_percap
- life_expect
- population
- birth_rate
- Neo natal Mortal Rate.

To begin I studied the existing dataset to understand the different attributes, their relations with each other and the distribution they follow. Using these observations we will form an algorithym for a manual data sythesis.

## 2.0 Prerequisites
Install Python 3.0
Install all required python dependencies

# import packages
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
from collections import Counter

## 3.0 Github
Create repository and readme in github account.

## Download Data
In command line, cd (change directory) to this repo root directory
Execute setup script.
Clone github through command line.

## Jupter
Open the Jupyter notebook through Anaconda.
Create python 3 ipynb file and name it boxplot.

#### Import os
I used import os to return my current working directory.
import os
os.getcwd()

#### List Directory
I used the os.listdir below to show my directory for this project
os.listdir(os.getcwd())


#### Read csv
I read the csv and printed the list of headings in a list.
I printed the counter column and the output of the number of rows by columns.

predefined_data = pd.read_csv("nations.csv")
print(list(predefined_data))
year=sorted(predefined_data['year'].tolist())
print(Counter(year))
print(" Number of Rows by Columns", predefined_data.shape)

#### Section 2.2
Section 2.2 allowed me to investigate the types of variables involved, their distributions and relationships with each other.
To begin I extracted any data I would not be using (na & unused columns). I then defined the year I would anaylse for this project as 2000.

predefined_data_2000=predefined_data.loc[predefined_data['year'] == 2000].dropna().drop(columns=['iso2c', 'iso3c'])
predefined_data_2000.head()

I used the describe() function to display the statistical facts of the data as shown below such as min, max, mean and standard deviation.

I displayed the data types of the columns using:
predefined_data_2000.dtypes

This allowed me to understand the types of values of each.

#### Distribution of Data
Using histograms I plotted the data per variable to display the output graphically. I imported the package below for this:
import scipy.stats as stats

Then I plotted each variable using the data pulled from the list showing the mean and standard deviation from my statistical anaylsis  earlier using the describe function.

fit = stats.norm.pdf(predefined_data_2000['gdp_percap'].tolist(), np.mean(predefined_data_2000['gdp_percap'].tolist()), np.std(predefined_data_2000['gdp_percap'].tolist())) 

plt.plot(predefined_data_2000['gdp_percap'].tolist(),fit,'o')

plt.hist(predefined_data_2000['gdp_percap'].tolist(),normed=True)     
plt.suptitle("GDP per Capita following Poisson Distribution")
plt.show()   

I changed the variable name for each and the output was as follows:
GDP per cap, birth rate and neo natal mortality variables were poisson distributions.
Population was a binomial distribution.

#### Section 2.3 Simulate a data set 
I used the 5 variables and the np random function to simulate the data for 100 data points. np.random.exponential allowed me to draw samples from an exponential distribution.  

gdp_per_cap_syn = np.random.exponential(400, 100)
life_expect_syn = np.random.exponential(39, 100)
population_syn = np.random.exponential(20000, 100)
birth_rate_syn = np.random.exponential(7, 100)
neonatal_mortal_syn = np.random.exponential(2, 100)

I named the synthesized variables _ syn to distinguish and used the same code as preiously to plot the histograms to show the mean and standard deviation per variable.

fit = stats.norm.pdf(gdp_per_cap_syn, np.mean(gdp_per_cap_syn), np.std(gdp_per_cap_syn))
plt.plot(gdp_per_cap_syn,fit,'o')

plt.hist(gdp_per_cap_syn,normed=True)
plt.suptitle("GDP per Capita Synthesized data")
plt.show() 

Finally I output the synthesized data in a data frame using the code below:
New_Synthesised_Data = pd.DataFrame({'GDP_Per_Capita_Synthesised': gdp_per_cap_syn, 'Life_Expectancy_Synthesised': life_expect_syn, 'Population_Synthesised': population_syn, 'Birth_Rate_Synthesised': birth_rate_syn, 'Neonatal_mortal_rate_Synthesised': neonatal_mortal_syn})
New_Synthesised_Data


## 4.0 Summary

I have chosen to review data of world econometric factors in order to analyse the associations between the world GDP per capita, life expectancy, population, birth rate and neo natal mortality rate. This project is based on a pre existing dataset taken from the world databank indicators portal. The datset is called nations.csv. 

Five variables have been taken into consideration:
- gdp_percap
- life_expect
- population
- birth_rate
- Neo natal Mortal Rate.

To begin I analysed the existing dataset to understand the different attributes, their relations with each other and the distribution they follow. Using these observations we will form an algorithym for a manual data sythesis.

I read the csv file to anaylse, decided to focus on the year 2000 for my review. I removed any data rows with na values and removed additional columns which I was not using as part of the analysis. I chose the 5 variables listed above for this project. I used the describe function to output a statistical analysis of the data for the year 2000. I used the dtypes function to display the type of data in each column.I anaylysed the distribution of my data using histograms. This allows me to clearly define the type of distribution e.g. Poisson and Binomial. 

Once I had reviewed the chosen dataset I then used this data to simulate data based on the 5 chosen variables over 100 data points. I used the np.random.exponential to gather this data and the output was displayed in histograms. Finally I displayed the simulated data in a dataframe with 100 data points.

## 5.0 References

