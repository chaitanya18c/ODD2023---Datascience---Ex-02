# Ex02-Outlier

# AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:
# STEP 1:
Read the given Data.
# STEP 2:
Get the information about the data.
# STEP 3:
Detect the Outliers using IQR method and Z score.
# STEP 4:
Remove the outliers:
# STEP 5:
Plot the datas using box plot.
# PROGRAM:
```
DEVELOPED BY: CHAITANYA
REGISTER NUMBER: 212222230024

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
# OUTPUT:
# bhp.csv:
# df.head():
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/dccfeeee-0586-4be0-8988-fc75d321180f)
# df.describe():
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/ecae24a6-2009-4ad7-a903-c7c3bd6be8fc)
# df.info():
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/f3a222f3-ad0a-4f1f-800b-e64b9d1e327d)
# df.shape
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/8139bab9-cd3a-4396-8d59-37cdabccc16c)
# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/9b85c1c1-d59c-4068-8497-560661b960cd)
# NEWDATA USING IQR
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/2f5a6116-63c8-484c-98c0-52705044c8d8)
# OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/488128f1-b53a-4b30-89f4-dd930754c3cc)
# newdata.shape
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/c43cd0f5-574a-4314-a6ef-918bc03e755a)
# BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/7caaa273-3482-4cc5-89c0-dd4c525dc4cb)
# Zscore of 3
# NEWDATA USING Zscore
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/51c6341b-adb9-44f2-857b-63772b8e7e4c)
# OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/dd314c16-30d1-4b5c-b462-d5714c880331)
# newdata2.shape
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/470146b4-e231-4ade-b647-f6baedba8ff8)
# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/4be8e577-943e-4cfe-8dc9-387d8f2f7a89)
# height_weight.csv
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/65fcf50e-edc0-4150-b698-6602e71a0538)
# dataset.describe()
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/3cb91f70-073e-4666-9d60-6f7d3e623a53)
# dataset.info()
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/632c48e7-1504-454c-b852-1d23f7513f9b)
# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/13eb60bd-58a8-4f44-8709-76c82cc274f2)
# HEIGHT OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/333887dc-eb45-4768-b9c3-28b2580ad410)
# DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/2d37472f-f3a5-4d92-8e4d-ce41319a8aed)
# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/174e6731-27d7-40aa-9ba6-44c4ba834ef8)
# WEIGHT OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/46c1c529-072f-4cc3-948d-062553f3b6c4)
# DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/72eb0591-5827-472e-a270-f511f31d2323)
# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://github.com/tharikasankar/ODD2023---Datascience---Ex-02/assets/119475507/03588439-3aab-44fb-882e-5de2af00ce39)
# RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
