# LIBRARIES
from scipy.signal import medfilt
from scipy import stats
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

## DATAFRAME AND DATA TO WORK WITH

df = pd.read_csv("[OPEN YOUR DATASET CSV]") ##Here open your dataframe
start = 40000
df = df[(df.year >= 2013)] #Choose the period of time where the data is consistent
df['PM'] = df[['PM_city]].mean(axis=1)
n1 = 'PM' #This is the variable for air pollution
n2 = 'TEMP' # These and the following are climatic variables
n3 = 'HUMI'
n4 = 'PRES'

# Let's see the dataframe and its length
print(len(df))
print(df) 

# DATA CLEANNING

## Boxplots to evaluate the distribution
bx = df.boxplot(['PM','PRES','HUMI','TEMP'])
print(np.max(df.TEMP),np.min(df.TEMP))

## Apply the method of maximums and minimums and 
## delete the outliers with a percentil of 10-90

print(np.max(df.TEMP),np.min(df.TEMP))
df = df[(df[n2] <= np.max(df.TEMP)) & (df[n2] >= np.min(df.TEMP))]
print(np.max(df.PRES),np.min(df.PRES))
df = df[(df[n4] <= np.max(df.PRES)) & (df[n4] >= np.min(df.PRES))]

df = df[(df[n3] < np.percentile(df[n3].dropna(),100))] & #removing outliers depends on the distribution
        (df[n3] > np.percentile(df[n3].dropna(),10))]

df = df[(df[n1] < np.percentile(df[n1].dropna(),90))] & #removing outliers depends on the distribution
        (df[n1] > np.percentile(df[n1].dropna(),1))]

print(len(df))

#DATA PREPROCESSING

plt.figure(figsize=(18,5))

plt.plot(df.No, df['PM'])

plt.title('Concentrations of PM across the time before preprocessing', size = 18)
plt.ylabel('concentrations of PM', size=15)
plt.xlabel('Samples across time', size=15)
plt.show()

#Definition of windows
## In this case where selected 30 days

df['PM_U'] = df[n1].rolling(window=w).mean()
df['PR'] = df[n4].rolling(window=w).mean()
df['HU'] = df[n3].rolling(window=w).mean()
df['TE'] = df[n2].rolling(window=w).mean()

#Correlation Matrix
corr = df[['PM_U','PR','HU','TE']].corr(method = 'spearman')
corr.style.background_gradient(cmap='coolwarm')

plt.matshow(df[['PM_U','PR','HU','TE']].corr())

cb = plt.colorbar()
cb.ax.tick_params(labelsize=14)
plt.title('Correlation Matrix', fontsize=16)

##Evaluation of the behaviour among variables

sns.pairplot(df[['PM_U','PR','TE']]),kind='reg',plot_kws={'line_kws':{'color':'red'}}
sns.pairplot(df[['PM_U','PR','TE']]),kind="kde")

### Then evaluate the correlation without preprocessing data
print(df.HUMI.corr(df.PRES))
print(df.TE.corr(df.PM_U))

### Now it is time to normalize data
df['PM_Un'] = (df.PM_U - df.PM_U.min()) / (df.PM_U.max() - df.PM_U.min()) 
#min-max normalization
df['TEn'] = (df.TE - df.TE.min()) / (df.TE.max() - df.TE.min())
df['HUn'] = (df.HUn - df.HUn.min()) / (df.HUn.max() - df.HUn.min())
df['PRn'] = (df.PR - df.PR.min()) / (df.PR.max() - df.PR.min())

## Now we have to do a correlation analysis to se if it stills the same
print(df.TE.corr(df.PM_U))
corr = df[['PM_Un','PRn','HUn','TEn']].corr()
corr.style.background_gradient(cmap='coolwarm')

## Now see how the graphs between variables has changed after the normalization
## Now we can really apreciate if they are correlated graphically

plt.figure(figsize=(20,5))
plt.plot(df.No, df.TE)
plt.plot(df.No, df.PM_U)
plt.show()
plt.figure(figsize=(20,5))
plt.plot(df.No, df.PR)
plt.plot(df.No, df.PM_U)
plt.show()

plt.figure(figsize=(18,5))
plt.plot(df.No, df('TEn'))
plt.plot(df.No, df['PM_Un'])
plt.show()

##Finally, here is the dataset ready to apply the AI Model

df[['PM_Un','PRn','TEn','PM_U','PR','TE']].to_csv('output.csv',index=False)

