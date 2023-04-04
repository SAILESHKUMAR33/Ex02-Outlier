# Ex02-Outlier
# AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

# ALGORITHM:
# STEP 1
Read the given Data.

# STEP 2
Get the information about the data.

# STEP 3
Detect the Outliers using IQR method and Z score.

# STEP 4
Remove the outliers.

# STEP 5
Plot the datas using Box Plot.

# PROGRAM:

DEVELOPED BY: SAILESHKUMAR.A
REGISTER NUMBER: 212222230126

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

# OUTPUT:
# bhp.csv
# df.head()
![image](https://user-images.githubusercontent.com/113497410/229702294-14caac03-237e-4c93-9d52-15dad20fa3fb.png)
# df.describe()
![image](https://user-images.githubusercontent.com/113497410/229702389-df19d030-5dd7-45f2-a544-363cf69e8276.png)
# df.info()
![image](https://user-images.githubusercontent.com/113497410/229702498-7fd0386f-53d1-47a6-91b8-afe65d2e6258.png)
# df.shape
![image](https://user-images.githubusercontent.com/113497410/229702583-a548da49-f8d8-4831-9431-e1058a9d5d7b.png)
# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229702671-9f28b02b-7c80-4602-b1ec-fc94e880752c.png)
# NEWDATA USING IQR
![image](https://user-images.githubusercontent.com/113497410/229702777-9b0529e3-dcb1-4574-8d8f-d8356461b7b6.png)
# OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229702855-09f315de-1c52-4604-95fa-875a2e216c01.png)
# newdata.shape
![image](https://user-images.githubusercontent.com/113497410/229703057-a5511e71-a5d7-4cac-8fc6-543d54e181f6.png)
# BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://user-images.githubusercontent.com/113497410/229703170-c6293d42-7e8a-4533-9dc7-fba192fb5072.png)
# Zscore of 3
# NEWDATA USING Zscore
![image](https://user-images.githubusercontent.com/113497410/229704344-18c36256-b9c1-4fe5-8bf1-308e70033649.png)
# OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229704499-4bb4605c-e765-4cce-8d7d-fdfc9a554e53.png)
# newdata2.shape
![image](https://user-images.githubusercontent.com/113497410/229704605-583125f4-2428-42a9-ad5b-49e52e3014cc.png)
# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://user-images.githubusercontent.com/113497410/229704722-ff02e224-efc6-4cef-9d8b-880e501caee7.png)
# height_weight.csv
dataset.shape
![image](https://user-images.githubusercontent.com/113497410/229704921-8c2d8654-328c-4900-8c87-79ccb8081f67.png)
# dataset.describe()
![image](https://user-images.githubusercontent.com/113497410/229705018-0b243673-3cf6-48bd-ae26-af50d8966a84.png)
# dataset.info()
![image](https://user-images.githubusercontent.com/113497410/229705189-6bff3186-58b3-46bf-8c51-437685bc297c.png)
# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229706983-ca85fe16-3786-4774-b73c-9a0e94233797.png)
# HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229707077-963935cf-5324-4154-89d6-d3129a52fee6.png)
# DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229707232-dd9c1483-e4c0-49b4-9ce6-dcd83bbdb6f4.png)
# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229707332-e6aacba9-d90b-447a-b7c2-a35953405214.png)
# WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229707443-8863f00a-5f71-469d-a08f-dfadebcb8d97.png)
# DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229707534-a1513936-e210-4719-b6b3-b44e10910975.png)
# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497410/229707655-92e0594c-a9a9-4c4e-87af-cc8317cf8857.png)
# RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.

