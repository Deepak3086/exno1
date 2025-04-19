# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
### REG NO:212224220019
### NAME: DEEPAK JG


```
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS (1) (1).csv')
df
 ```
![Screenshot 2025-04-19 180748](https://github.com/user-attachments/assets/a76d61d2-32ac-4658-9345-bfbec3a3b096)
```
df.shape
```
![image](https://github.com/user-attachments/assets/c3d2139f-548f-41e4-8b15-d76be4edb882)
```
df.info()
```
![Screenshot 2025-04-19 180755](https://github.com/user-attachments/assets/66a0d6ff-8d44-47c8-a7c0-b590b54fa585)
```
df.describe()
```
![image](https://github.com/user-attachments/assets/0758f0f6-3338-4418-b1c2-3b18098ffb6e)
```
df.head(10)
```
![image](https://github.com/user-attachments/assets/9b61c000-dff8-4bd1-a1ce-dbccfca19ddf)
```
df.tail(10)
```
![image](https://github.com/user-attachments/assets/aa954922-dcd3-4fa7-98aa-0f90c6124587)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/d5b11e8c-7184-470b-af4a-0ea62b5b86ec)
```
df.dropna(how='any').shape
```
![image](https://github.com/user-attachments/assets/fbcf3496-3359-40fe-95d0-f2fd7a20774d)
```
df.shape
```
![image](https://github.com/user-attachments/assets/65d6e615-c416-4320-93fd-da44e11ddf3d)
```
x=df.dropna(how='any')
x
```
![image](https://github.com/user-attachments/assets/8d1f1445-ce1c-4a6e-bdfb-078bba9ae4c2)
```
m=df.TOTAL.mean()
m
```
![image](https://github.com/user-attachments/assets/c1f8dba1-260d-4c59-a9c1-7b58e1ec9113)
```
df.TOTAL.fillna(m,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/abf4494c-1280-4f06-85ca-b37c6e77c30b)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/74c81e7a-9f39-426e-a603-ad3ad715adb6)
```
df.M1.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/9abbb762-8267-4aed-bea6-d2acead2680e)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/0ff3b0b2-ffb8-4d3a-a85d-d98eecf36b47)
```
df.M2.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/2661aa3b-884c-4f79-876f-0cb16cd82389)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/031eadb7-ae8b-4e19-a892-230c1298ae93)
```
df.M3.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/5a1919ad-8769-4819-9c5d-c33d8137e20c)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/fa2cb3f8-5eed-4f5f-ab32-801c563aada8)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/8bc81c09-80e8-443e-9a53-c4dff8500dc0)
```
df.drop_duplicates(inplace=True)
df
```
![image](https://github.com/user-attachments/assets/94bf8b7a-5b2d-4bbe-8f27-a1f8059b1bf5)
```
df['DOB']
```
![image](https://github.com/user-attachments/assets/43ae84d9-e594-49cd-88d5-e464c309a49d)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/b5823635-d187-4ab7-843d-7694931f7351)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/9f4c0bb9-8c15-4884-939f-b16e6d81baa6)
```
age=[1,2,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
```
![image](https://github.com/user-attachments/assets/052812de-ab20-4e28-a297-33873e7dbd8c)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/924057d5-6a57-460c-a6ee-67a6456b106b)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/06993630-316e-41ff-b114-743725da3993)


OUTLIER DETECTION AND REMOVAL USING IQR
```
q1=df.quantile(0.25)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/c90aa7b7-e61e-44cb-94ae-d788391a2c37)
```
import numpy as np
Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR
```
![image](https://github.com/user-attachments/assets/a6da63fd-f240-443d-8242-939e218e07a8)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
print(lower_bound,upper_bound)
```
![image](https://github.com/user-attachments/assets/4758e65c-96b5-4792-8a91-3dee920d2f7c)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q3:",Q3)
print("Q1:",Q1)
print("IQR:",IQR)
print("Lower bound:",lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/b165b7e9-794f-4fd7-a999-95af30ab4cc8)
```
df=df[((df>lower_bound)&(df<=upper_bound))]
df
```
![image](https://github.com/user-attachments/assets/88d21f97-7579-49a7-a00f-4258253b8d52)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/970a14d8-1410-4d9f-8692-9619c3125a0f)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/aa4a63b9-21f8-4291-8f40-b778e7d0ed8d)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/ec84a73b-b1d6-459b-93d7-026aa3157c51)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('standard deviation is',std)
```
![image](https://github.com/user-attachments/assets/31c97ecc-383b-4ab3-8b7a-774bb01e3b47)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/d7de3efb-2975-47c6-b0f4-b195eedf11d2)
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/a2863b90-f7f9-4b7f-a22f-bb78e8f7b9dd)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/user-attachments/assets/5849805b-26be-4a43-9ec6-563f56ee2a1f)




# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
