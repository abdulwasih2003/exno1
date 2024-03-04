# Ex No:1
## 1.Data Cleaning Process:

# Aim:
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation:
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm:
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```py
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS.csv')
df
```
![img](https://github.com/DHINESH-SEC/exno1/assets/91781810/1882833d-df1d-47e5-a271-cea501eb06a0)

```py
df.head()
```
![o2](https://github.com/DHINESH-SEC/exno1/assets/91781810/e014869e-f650-4e0d-ad09-823e91fab59e)

```py
df.tail()
```
![o3](https://github.com/DHINESH-SEC/exno1/assets/91781810/ef1ffca5-a229-46cc-a079-b0e1194c5fcc)

```py
df.describe()
df.info()
```
![o5](https://github.com/DHINESH-SEC/exno1/assets/91781810/29856818-a3e4-4e3d-aca3-91b6eaf9eedb)
```py
df.shape
```
![o6](https://github.com/DHINESH-SEC/exno1/assets/91781810/aef5cfbe-bab4-49f1-ab55-105547112049)

```py
df.isnull().sum()
df.nunique()
df['GENDER'].value_counts()
mm=df.TOTAL.mean()
df.TOTAL.fillna(mm,inplace=True)
df
```
![o11](https://github.com/DHINESH-SEC/exno1/assets/91781810/3270d65e-5199-4243-afc7-d46f445cd1d0)

```py
x=df.M4.min()
df.M4.fillna(x,inplace=True)
df
```
![o13](https://github.com/DHINESH-SEC/exno1/assets/91781810/6e309fde-0e01-4475-ac89-232582390eae)
```py
df.duplicated()
df.drop_duplicates(inplace=True)
```
![o15](https://github.com/DHINESH-SEC/exno1/assets/91781810/02c842f1-9147-4afd-a6bd-fc656a77776f)

```py
df['DOB']
y=pd.to_datetime(df['DOB'])
y
df['DOB']=pd.to_datetime(df['DOB'])
df
```
![o18](https://github.com/DHINESH-SEC/exno1/assets/91781810/dac647d4-0066-449e-9b18-7580a12a846f)

```py
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![o19](https://github.com/DHINESH-SEC/exno1/assets/91781810/cb6c7828-deec-47a9-b836-1808d438a4fc)

```py
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![o20](https://github.com/DHINESH-SEC/exno1/assets/91781810/31dbb052-83ce-407c-938b-eee77d76e149)

```py
df.shape
```
![o21](https://github.com/DHINESH-SEC/exno1/assets/91781810/5be453f1-59d2-45c9-81af-48ff6559bbb6)

## 2.Outlier Detection and Removal
```py
import pandas as pd
import seaborn as sns
import numpy as np
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![alt text](o22.png)
```py
sns.boxplot(data=af)
```
![alt text](o23.png)
```py
sns.scatterplot(data=af)
```
![alt text](o24.png)
```py
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
![alt text](o25.png)
```py
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
outliers=[x for x in age if x< lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:"),upper_bound
print("outliers:",outliers)
```
![alt text](o26.png)
```py
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![alt text](o27.png)
```py
af.dropna()
```
![alt text](o28.png)
```py
sns.boxplot(data=af)
```
![alt text](o29.png)
```py
sns.scatterplot(data=af)
```
![alt text](o30.png)
```py
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'Weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![alt text](o31-1.png)
```py
z=np.abs(stats.zscore(df))
```
![alt text](o33.png)
```py
print(df[z['Weight']>3])
```
![alt text](o32.png)
# Result
Hence the Data Cleaning process is performed successfully on the given data using python code.
