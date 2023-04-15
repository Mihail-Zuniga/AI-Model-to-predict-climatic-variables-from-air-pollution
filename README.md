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
</br>

###### Figure 1
  Data pipeline used in the study.
  
![CHEESE](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Data%20Pipeline.png)

Note. Own authorship.

### Selection and definition of variables
Four variables have been selected for the analysis: one objective and three independent. The objective variable is the one to be predicted: PM 2.5, it is expressed in µg/m3 and corresponds to the average of the PM 2.5 measurements of the three sensors in the data set (Xuhui, Jingan and US Post). 


The average value has been chosen in order to (i) have a more approximate value of PM 2.5 and (ii) reduce the number of records without PM 2.5 measurements. Independent variables are those that will be used to predict the target variable. Three variables have been selected that are highly related to the PM 2.5 level: temperature, relative humidity and atmospheric pressure. Air temperature is expressed in degrees Celsius (°C) as it has been shown to have a significant impact on climate change and has been linked to PM 2.5 levels (Xing et. al, 2021). Relative humidity is expressed as a percentage, it corresponds to the fraction of water vapor present in 1m3 of water and is closely related to the temperature level (Vassoler and Zebende, 2012). 

Finally, the atmospheric pressure, which is expressed in hectopascals (hPa) and directly influences the compaction of high-concentration minute materials, which is why there would be a high correlation with PM 2.5 (Haiming and Xiaoxiao, 2013).
### Cleaning and Preprocessing
In the first phase of the cleaning, the selection of the research time range was carried out. Only data after 2012 has been taken into account due to the great dispersion and lack of data during previous years, which would affect the performance of the regression model. Figure 2 shows the missing data gaps for PM 2.5 (data with NaN value), which correspond to the period prior to the year 2012.
Once the analysis period was established, the data distribution was evaluated to determine the number of outliers in the data set. For this, box plots of each of the variables were made. Boxplots are widely used in statistics to visually analyze the measures of dispersion (median, quartiles, and distribution) of a variable. Figure 3 shows the results for the different variables, showing that they all have a different distribution. </br>
</br>

##### Figure 2
PM 2.5 measurements (µg/m2) recorded chronologically.

![CHEESE](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Chronological%20PM%20measurement.png)

Note. Own authorship.

</br>
In the case of the objective variable (PM 2.5), a Gaussian distribution is observed with a negative mean asymmetry and with the presence of a large number of outliers that can occur during festive dates or due to measurement errors (Fatahi et. al, 2021 ).
In the case of the humidity variable, a Gaussian distribution can be seen with a mean positive asymmetry and the presence of a considerable number of outliers that may be due to the nature of the variable and certain periods of torrential rains, floods and high temperatures that they increase the amount of water vapor present in the air (Singh et. al, 2019). In the case of temperature and atmospheric pressure, a symmetric Gaussian distribution is observed without outliers. </br>
</br>

##### Figure 3
Box plots of the study variables.
![CHEESE](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Boxplots%20of%20the%20variables.png)

Note. Own authorship.

</br>
In addition to the study of data dispersion, the analysis of the box plots allows determining the most appropriate cleaning method to be used for each variable (Zuniga et. al., 2019). In the case of variables with a large number of outliers, data cleaning was performed based on percentiles: PM 2.5 (only measurements within the 1st to 90th percentiles are used), humidity (only measurements within the 1st to 90th percentiles are used). 10 to 100). In the case of variables without outliers (temperature and atmospheric pressure), a simple filter was performed, eliminating all measurements without values: NaN. Figure 4 shows the variables after the cleaning process, observing the absence of outliers compared to Figure 3. </br>
</br>

##### Figure 4
Box plots of the study variables after cleaning out outliers.

![CHEESE](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Boxplots%20after%20data%20cleanning%20of%20atypical%20values.png)

Note. Own authorship.

</br>
For preprocessing, the Simple Moving Average method was used. This preprocessing method is used to reduce noise in a signal and consists of applying a sliding time window throughout the measurement period in which the average value of the values within the window is taken (Ellis and Parbery, 2005). . In this study, 30 days has been defined as the time window. 30 days has been used since this period is descriptive of production cycles and seasons of the year. Figure 5 shows an example of the measurements before and after applying the Simple Moving Average. At the same time, it shows how preprocessing helps to reduce noise in PM 2.5 measurements, allowing a more clear observation of the behavior of the variables over time.
</br>

##### Figure 5
PM 2.5 measurements (µg/m2) before and after pre-processing.

![CHEESE](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Variables'%20measuring%20before%20and%20after%20preprocessing.png)

Note. Own authorship.

</br>
### Correlation analysis
Next, the level of relationship between the independent variables and the objective variable will be evaluated. For this, Spearman's correlation will be used, which is applied when the variables do not follow a normal distribution and is evaluated with the following formula.

The correlation coefficient can take values from -1 to 1, where rs = -1 indicates a strong negative correlation between the variables, rs = 1 a strong positive correlation between the variables and rs = 0 a null correlation (Galton, 1869). The correlation between variables is clearly presented using the correlation matrix that shows all the correlation coefficients between the variables and uses colors to highlight the level of correlation.

Figure 6 shows the correlation matrix between variables. The relationship between variables can be denoted, mainly between PM 2.5 and temperature with a high negative correlation (correlation index of -0.706) and between PM 2.5 concentrations and atmospheric pressure with a medium positive correlation (correlation index of 0.504). This indicates that when the temperature decreases the concentration of PM 2.5 rises, and that when atmospheric pressure rises the concentration of PM 2.5 increases. No relationship is shown between PM 2.5 and relative humidity (correlation index of -0.07). Based on this result, the variables with correlation coefficients less than -0.5 (Temperature) and greater than 0.5 (Atmospheric Pressure) have been selected, since this means that they are more suitable to be used in the PM 2.5 prediction model.

##### Figure 6

Correlation matrix between variables.

![cheese](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Correlation%20Matrix.png)

Note. Own authorship.

</br>
To validate the correlation results, the coefficients obtained in this study are compared with others previously scientifically validated. Figure 7 shows the correlation matrix from a study of factors contributing to air pollution in India (Bedi et. al, 2016). It can be seen in the figure that the correlation levels are similar to those obtained in the present study for the objective variable (PM 2.5) and the independent variables (atmospheric pressure, humidity), confirming the validity of the results of this study.

##### Figure 7
Correlation matrix between variables in New Delhi according to the PunjabiBagh (left) and RKPuram (right) census.

![cheese](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Correlation%20Matrix%20of%20previous%20studies.png)

Note. Retrieved from: “Complete Study of Factors Contributing to Air Pollution” by K. Gnanasekaran, S. Balasubramanian, S. Mahadevan, N. Shenoy, 2016. https://www.analyticsvidhya.com/blog/2016/10/complete- study-of-factors-contributing-to-air-pollution/
</br>

As theoretical support for the correlation between PM 2.5 concentration levels and atmospheric pressure is the presence of atmospheric pressure at the time of the creation of the particular articulated material, since said pressure can become the one that compacts particles detached from the materials that make up PM 2.5 (Jiang et. al, 2020). Figure 8 presents the results of said study confirming a positive correlation between the PM 2.5 level and atmospheric pressure.
</br>

##### Figure 8
  Correlation matrix between the variables in Fuzhou according to the Fuzhou sensor, scatter and numeric graph.
</br>
![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/correlation%20matrix%20of%20another%20previous%20study.png)
</br>

Nota. Recuperado de: “Temporal cross-correlations between air pollutants and outpatient visits for respiratory and circulatory system diseases in Fuzhou, China” por Y. Jiang, et al. 2020. https://bmcpublichealth.biomedcentral.com/articles/10.1186/s12889-020-08915-y
</br>

### Causality Analysis

To mitigate possible errors related to false correlations, a causality analysis has been carried out that is based on validating that the correlations found were not obtained by chance. Initially, the correlation between PM 2.5 and temperature was analyzed. The negative correlation between these variables indicates that as the ambient temperature decreases, the PM 2.5 level increases. However, it would be wrong to say that there is causality between both variables, since in that case one would be suggesting, for example, that the poles are the places with the highest level of pollution on earth, which is false.
</br>

The correct way to interpret causality in this case is by analyzing the behavior of energy consumption during the different seasons of the year, the months with the lowest temperatures being those that require the massive use of heaters, increasing the level of pollution due to higher energy consumption. . In the case of the correlation between PM 2.5 and atmospheric pressure, the causality can be determined by the freedom in the degree of movement of the particles. A higher atmospheric pressure helps to obtain a higher concentration of PM 2.5, since it can cause a greater cohesion of the particles (Haiming and Xiaoxiao, 2013). </br>

### Behavior between variables
The final part of verifying correlations between variables is performed by comparing the behavior of the correlated variables over time. The upper part of Figure 9 shows the comparison between PM 2.5 and temperature, confirming the negative correlation between both variables. The lower part of Figure 10 presents the comparison between PM 2.5 and atmospheric pressure, which is difficult to perform due to the ranges. To solve this problem, the variable normalization method is applied, which consists of taking the value of the variables to the same scale so that they can be easily compared, something commonly used in data analysis and necessary for the realization of certain models of prediction (Sola and Sevilla, 1997). </br>
</br>

##### Figure 9
Comparison graph between PM 2.5 and temperature (upper part), and PM 2.5 and Atmospheric Pressure (lower part).

![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/comparation%20graph%20between%20variables%20before%20normalization.png)

Note. Own authorship.

</br>
Figure 10 shows the normalized variables. As expected, the correlations between variables are much more visible when the axes are normalized: negative correlation between PM 2.5 and temperature and positive correlation between PM 2.5 and Atmospheric Pressure.
</br>

##### Figure 10
Normalized graph of comparison between PM 2.5 and temperature (upper part), and PM 2.5 and Atmospheric Pressure (lower part).
![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/comparation%20graph%20between%20variables%20after%20normalization.png)

Note. Own authorship.

### Predictive model

The objective of this study is to determine the degree of precision with which the level of PM 2.5 can be predicted using climatic variables (in this case temperature and atmospheric pressure) and artificial intelligence algorithms. For this case, the most basic machine learning algorithm for regression problems called linear regression has been used and its resolution through the Least Squares method, which is considered to have been created in ancient Greece and having Galileo Galilei as the first modern precursor, although finally exposed by Legendre in 1805. The linear regression model is based on two steps:
</br>
Apply the formula for the development of the method of least squares.
</br>
Find the coefficients that solve the equation of the line that minimizes the error.
</br>
As previously mentioned, the development of the linear function resorts to determining the coefficients that minimize the error of all the points with respect to a line.
</br>
The linear regression model for PM 2.5 and temperature of the data set with a 70% interval of data is given by the following equation:

#### y = 55.77- 0.663 X

The RMSE obtained a value of 5.48 g/m3 while the coefficient of determination R2 has a value of 0.484. This means that the percentage of variation of the response variable compared to the predictor variables is medium since it covers a range close to 0.5. Figure 13 shows the resulting line that minimizes the model error. </br>

##### Figure 11
Linear regression function, Temperature vs. PM2.5.

![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Linear%20Regression%20function's%20graph%20PM%20and%20Temperature.png)

Note. Own authorship.
</br>

The linear regression model for PM 2.5 and atmospheric pressure with a 70% data interval is given by the following equation:

#### y = -453.92 + 0.49 X

The RMSE obtained a value of 6.62 g/m3 coefficient of determination R2 has a value of 0.247, which means that the percentage of variation of the response variable compared to the predictor variables is low since it covers a range far from the mean value of 0.5 . Finally resulting with the following graph. Figure 14 shows the resulting line that minimizes the model error.
</br>

##### Figure 12
  Linear regression function, Atmospheric Pressure vs. PM2.5.

![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/Linear%20Regression%20function's%20graph%20PM%20and%20pressure.png)

Note. Own authorship.
</br>

Here is how to configure the AI model in Orange3, Here I used a Linear Regression Model to seem new in this bussines, but you can also apply a neural network which has a better performance.

![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/orange3%20configuration%201.png)

![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/orange3%20configuration%202.png)

![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/orange3%20configuration%203.png)

![che](https://github.com/Mihail-Zuniga/AI-Model-to-predict-climatic-variables-from-air-pollution/blob/main/Graphs/orange3%20configuration%204.png)

## Conclusions
- By using basic artificial intelligence models, a prediction of the PM 2.5 level can be obtained with a squared error of 0.48 and 0.24 units using temperature and atmospheric pressure as independent variables respectively. This error represents an approximate difference of 5.48 µg/m2 in each temperature prediction and 6.62 µg/m2 in the prediction based on atmospheric pressure.
- There is a correlation of 0.70 and 0.51 units between the independent variables: atmospheric pressure and temperature with the objective variable, PM 2.5. This correlation is useful to determine the degree of influence of these variables on the level of air pollution with causal analysis.
- Through the application of a data pipeline, an organization and adequate direction for the investigation can be obtained, in addition, with the use of cleaning as part of the pre-processing, the predictability capacity of the development of the data analysis and proposed model and the proposed model were increased. development of data analysis and model.
- The use of programming environments such as Python and Orange 3 streamlines the implementation of mathematical equations, statistical methods and artificial intelligence models, contributing to the development of scientific research and its practical implementation.
### Considerations
Linear regression is one of the most basic algorithms used in artificial intelligence for regression problems. This work can be extended using other more complex algorithms such as neural networks. Overall, it can be noted that during the investigation the validity of the results was verified with other scientifically validated studies. It should be taken into account that possible differences in the results may be due to the area and time of year in which the study was carried out, since this influences the level of contamination and the components that can form PM 2.5.
## Bibliography and References
### References
- Bedi, J., Gnanasekaran, K., Balasubramanian, S., Mahadevan, S., & Shenoy, N. (2016). Complete Study of Factors Contributing to Air Pollution. Great Lakes Institute. https://bit.ly/3HDaMWp
- Ellis, C.A., and Parbery, S.A. (2005). Is it smarter better? A comparison of adaptive, and simple moving average trading strategies. Research in International Business and Finance, 19(3), 399-411. https://bit.ly/34Jo3hU
- Emenike, H., Dar, F., Liyanage, M., Sharma, R., Zuniga, A., Hoque, M. A., … and Flores, H. (2021). Characterizing Everyday Objects using Human Touch: Thermal Dissipation as a Sensing Modality. 2021 IEEE International Conference on Pervasive Computing and Communications (PerCom), 1-8. https://bit.ly/3tpsjx2
- Fatahi, Y., Kouznetsov, R., & Sofiev, M. (2021). The effect of accounting for public holidays on the skills of the atmospheric composition model SILAM. Geoscientific Model Development, 14(12), 7459-7475. https://bit.ly/337jwVQ
- Galton, F. (1869). Hereditary Genius. Macmillan and Company (pp. 130-136). https://bit.ly/3FrubrD
- Haiming, Z., & Xiaoxiao, S. (2013, June). Study on prediction of atmospheric PM2. 5 based on RBF neural network. 2013 Fourth International Conference on Digital Manufacturing & Automation, 1287-1289. https://bit.ly/3LnuPuk
- Jiang, Y., Chen, J., Wu, C., Lin, X., Zhou, Q., Ji, S., ... and Liu, B. (2020). Temporal cross-correlations between air pollutants and outpatient visits for respiratory and circulatory system diseases in Fuzhou, China. BMC public health, 20(1), 1-13.
https://bit.ly/33bZr0O
- Liang, X., Li, S., Zhang, S., Huang, H., & Chen, S. X. (2016). PM2. 5 data reliability, consistency, and air quality assessment in five Chinese cities. Journal of Geophysical Research: Atmospheres, 121(17), 10-220. https://bit.ly/3LfvcY1
- Alone, J., and Sevilla, J. (1997). Importance of input data normalization for the application of neural networks to complex industrial problems. IEEE Transactions on nuclear science, 44(3), 1464-1468. https://bit.ly/3fmUp3S
- Singh, M.S., Warren, R.A., & Jakob, C. (2019). A steady‐state model for the relationship between humidity, instability, and precipitation in the tropics. Journal of Advances in Modeling Earth Systems, 11(12), 3973-3994.
https://bit.ly/3rzZVHp
- Vassoler, R.T., & Zebende, G.F. (2012). DCCA Cross-correlation Coefficient apply in time series of air temperature and air relative humidity. Physica A: Statistical Mechanics and its Applications, 391(7), 2438-2443. https://bit.ly/3qkEcm5
- Xing, H., Wang, G., Liu, C., & Suo, M. (2021). PM2. 5 concentration modeling and prediction by using temperature-based deep belief networks. Neural Networks, 133, 157-165. https://bit.ly/3oByn2h
- Zuniga, A., Flores, H., Lagerspetz, E., Nurmi, P., Tarkoma, S., Hui, P., & Manner, J. (2019, May). Tortoise or hare? Quantifying the effects of performance on mobile app retention. The World Wide Web Conference. 2517-2528. https://bit.ly/3J5V0nw
Zuniga, A., Nurmi, P., and Flores, H. (2021). Ripe or Rotten? Low-Cost Produces Quality Estimation Using Reflective Green Light Sensing. IEEE Pervasive Computing. https://bit.ly/3uzS6Dx
### Bibliography
- Aromolo, R., Savi, F., Salvati, L., Ilardi, F., Moretti, V., & Fares, S. (2015). Particulate matter and meteorological conditions in Castelporziano forest: a brief commentary. Rendiconti Lincei, 26(3), 269-273. https://bit.ly/3uK4twC
- Chen, Z., Xie, X., Cai, J., Chen, D., Gao, B., He, B., ... and Xu, B. (2018). Understanding meteorological influences on PM 2.5 concentrations across China: a temporal and spatial perspective. Atmospheric Chemistry and Physics, 18(8), 5343-5358.
https://bit.ly/3HHxT2q
- Diaz, V., Bahamonde, M. (2020). ANNUAL REPORT ON AIR QUALITY YEAR 2018. Ministry of Environment. Municipality of the Metropolitan District of Quito. https://bit.ly/3GxCDpH
- Liang, X., Zou, T., Guo, B., Li, S., Zhang, H., Zhang, S., ... & Chen, S. X. (2015). Assessing Beijing's PM2. 5 pollution: severity, weather impact, APEC and winter heating. Proceedings of the Royal Society A: Mathematical, Physical and Engineering Sciences, 471(2182). https://bit.ly/3Lox8NG
- Liu, Y., Zhao, N., Vanos, J.K., & Cao, G. (2017). Effects of synoptic weather on ground-level PM2. 5 concentrations in the United States. Atmospheric Environment, 148, 297-305. https://bit.ly/3oCNA3f
- Requia, W. J., Jhun, I., Coull, B. A., & Koutrakis, P. (2019). Climate impact on ambient PM2. 5 Elemental concentration in the United States: A trend analysis over the last 30 years. Environment international, 131. https://bit.ly/3Gxslac
- Tai, A.P., Mickley, L.J., & Jacob, D.J. (2010). Correlations between fine particulate matter (PM2. 5) and meteorological variables in the United States: Implications for the sensitivity of PM2. 5 to climate change. Atmospheric environment, 44(32), 3976-3984. https://bit.ly/3uAphGS
