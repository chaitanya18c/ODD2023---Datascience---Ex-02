# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.  

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

  -  (i) Using IQR detect weight outliers and print them

  -  (ii) Using IQR, detect height outliers and print them

## Explanation:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

## Algorithm:
  - Step1: Read the given Data.
  - Step2: Get the information about the data.
  - Step3: Detect the Outliers using IQR method and Z score.
  - Step4: Remove the outliers.
  - Step5: Plot the datas using Box Plot.

## Code:

### bhp.csv:
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```

### height.csv:
```
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('height_weight.csv')
df.info()
df.describe()
df.head()

#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
height_q1 = df['height'].quantile(0.25)
height_q3 = df['height'].quantile(0.75)
height_IQR = height_q3 - height_q1
height_low = height_q1 - 1.5 * height_IQR
height_high = height_q3 + 1.5 * height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=height_new)

#BEFORE REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]
#AFTER REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=weight_new)
```

## OUTPUT:

### bhp.csv:
![265059074-c62482aa-13d3-4e93-84f3-14d77e12ff94](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/585873b7-db35-4292-85a5-f07438a9ba22) ![265059155-77006c4a-5f65-4c46-b43d-62da3adeae72](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/2dc8e259-103a-4505-badb-60a8c12bea30)



![265059121-550161a2-7e49-4873-b9d3-2dee79909859](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/10a13109-52df-4994-81cd-5578693c5815)

![265059222-699f1ddd-dfb7-4d58-abd5-69614106d9d4](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/a7d5a2e3-cf7a-43ce-b410-1b6ca63bd3ea)

![265059167-6ab44ad1-3d24-49ac-8ed8-0a873ee9094c](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/07dc71b4-b403-4474-9868-acdf1605e79f)

![265059222-699f1ddd-dfb7-4d58-abd5-69614106d9d4](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/ce860c5c-aae1-4485-9805-f9df899b5a5d)

### weight.csv:

![265060058-ea846d57-a472-4b28-8d0a-3c405d80f8e0](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/4ddd9143-6bf7-4317-95cc-170bdce40c70)

![265060068-beead9e7-e4bc-4431-a536-bacdb947e6b6](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/b145fbd0-ac54-4a88-a8be-c0aa9a14ca6b)

![265060084-952f228c-8518-4f91-b966-fda9215eb959](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/693dc956-3fe6-4bf7-8b6b-27fa78b01694)

![265060101-35fbb5b8-69b9-4592-9685-d81d4cb0f844](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/39063522-4c11-424c-be51-f07a380abdfb)

![265060107-3606e325-b846-412f-b0c2-e56d74b16427](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/7ea733c7-c2a8-4f9c-9187-f76483e09303)

![265060126-14b3b742-5bfe-47c2-954b-7ee7315c6848](https://github.com/Janarthanan2/Datascience---Ex-02/assets/119393515/1d3c099a-339e-492a-b9cb-09e5851809f3)

## Result:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.





