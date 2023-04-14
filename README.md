## Summary

The purpose of this research is to develop a simple linear regression model between climatic variables: Temperature, Relative Humidity, Atmospheric Pressure, with PM 2.5 concentration levels through the application of basic artificial intelligence models with machine learning, supervised learning and data processing from programming environments. For its realization, a database that provides climatic values of the city of Shanghai in China was used. The development was based on a structured pipeline so that variables are identified, data cleaning and preprocessing occurs, correlation and causality analysis, and finally the predictive model is created so as to determine the extent to which the application of models Basic artificial intelligence can accurately predict climate variables, in addition the results have been corroborated by studies carried out to expedite the creation of models that predict the extent to which climate change is generated from particulate matter.

## 2. INDEX

1. Summary
2. Index
3. Introduction 
4. Development </br>
  4.1. Data pipeline </br>
  4.2. Variables selection and definition </br>
  4.3. Data cleanning and Preprocessing </br>
  4.4. Correlation Analysis </br>
  4.5. Causality Analysis </br>
  4.5.1. Behaviour among variables </br>
  4.6. Predictive model </br>
  4.6.1 Sample case: Predictive model </br>
5. Conclusions </br>
  5.1. Considerations
6. References and Bibliographies </br>
  6.1. References </br>
  6.2. Bibliography </br>

## Introduction

City air is an immense mixture of gases composed mostly of nitrogen, oxygen and "other gases" among which pollutants such as carbon dioxide (CO2) or methane gas (CH4) stand out. However, within said gaseous composition, the presence of tiny particles of organic chemicals, soot, dust and even metals with a size generally of 2.5, 5 and 10 micrometers can also be denoted, which is commonly measured gravimetrically through a process in which an air sample circulates through a fixed flow that has a filter where said substance known as particulate joint material remains, a substance that in high concentrations represents a significant health risk as it causes cardiovascular and respiratory diseases and even cancer at different organs such as the lungs.

In addition, studies have experimentally demonstrated a possible correlation between PM 2.5 particulate matter levels and climatic variables such as temperature, applying artificial intelligence models (Tai, 2010). Establishing models that relate these variables from measurements made in the United States (Westervelt, 2016).

For this reason, it has come to question different possible problems that this correlation entails with an effect on the increase in world temperature through climate change, this is how it was decided to carry out the study based on data presented in cities of China, a country to consider in the fight against climate change.

For this reason, for the present investigation, it has been decided to develop a basic artificial intelligence model to mathematically develop a linear regression where the change in PM 2.5 levels is predicted from climatic variables, in case there is a close correlation between said variables. with the corresponding levels of particulate matter.

Therefore, it has been decided to use a database published by the University of Peking by the Professor of Statistics and Econometrics Song Xi Chen in 2016 in the publicly open repository UCI Machine Learning where information covering from 2010 to 2015 of the levels is presented. of PM 2.5 and other climatic variables of five Chinese cities which are: Shenyang, Chengdu, Beijing, Guangzhou and Shanghai, showing more than 52,000 measurements of each of the variables per city.

It has been decided to use different mathematical concepts to introduce for the processing of the corresponding database and the development of the subsequent linear regression model that has been selected to evaluate the predictive capacity of said concentrations through basic models.

Finally, for the development of the database, due to the immense amount of information found in it, the use of different information processing tools such as the iPython Jupyter Notebook environment has been used as a means of development. optimal and ordered in the code to be generated, in turn the Orange3 environment has been used to develop the linear regression models.

## Development
### Data pipeline
The present study is based on the application of data pipelines widely used in science for machine learning and data analysis (Zuniga et. al., 2021); (Emenike et al, 2021). Figure 1 details the pipeline used. In the first stage, the variables to be analyzed are selected and defined according to their importance and availability in the database. Subsequently, data cleaning and preprocessing is performed to eliminate outliers. The third stage includes the correlation analysis to establish the most significant variables. Finally, the selection and implementation of the machine learning model is carried out to predict the value of PM 2.5 based on the significant variables.
![alt text](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/Graphs/Data-pipeline.png?raw=true)
