# ExNo:1
## Data Cleaning Process

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

# Coding and Output:
```py
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS.csv')
df
```
![o1](https://github.com/abdulwasih2003/exno1/assets/91781810/dcab775a-6aa8-4829-8edb-2041c410d839)

```py
df.head()
```
![o2](https://github.com/abdulwasih2003/exno1/assets/91781810/4ce1db9b-b039-4a29-83eb-f9f6e8315fcd)

```py
df.tail()
```
![o3](https://github.com/abdulwasih2003/exno1/assets/91781810/6905d38c-d6f9-4ca8-8fb5-bec5a96c458f)

```py
df.describe()
df.info()
```
![o5](https://github.com/abdulwasih2003/exno1/assets/91781810/4a2bcb5e-0194-4ef0-9909-9c69bccd74e2)

```py
df.shape
```
![o6](https://github.com/abdulwasih2003/exno1/assets/91781810/15787dde-cb6a-4663-b70f-771623605eff)

```py
df.isnull().sum()
df.nunique()
df['GENDER'].value_counts()
mm=df.TOTAL.mean()
df.TOTAL.fillna(mm,inplace=True)
x=df.M4.min()
df.M4.fillna(x,inplace=True)
df.duplicated()
df.drop_duplicates(inplace=True)
```
![o15](https://github.com/abdulwasih2003/exno1/assets/91781810/7fef135f-f960-455d-8b6f-482989841f36)

```py
df['DOB']
y=pd.to_datetime(df['DOB'])
df['DOB']=pd.to_datetime(df['DOB'])
df
```
![o18](https://github.com/abdulwasih2003/exno1/assets/91781810/4babe68c-7fd9-4914-99a9-27a3268983c5)

```py
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![o19](https://github.com/abdulwasih2003/exno1/assets/91781810/f009a170-0795-483d-9d8a-9a8071dbc413)

```py
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![o20](https://github.com/abdulwasih2003/exno1/assets/91781810/73ebcf09-e63a-4217-ac12-2786b0539036)

```py
df.shape
```
![o21](https://github.com/abdulwasih2003/exno1/assets/91781810/88bb2f30-56bc-4636-8f60-466cd45c22ca)

## Outlier Detection and Removal:
```py
import pandas as pd
import seaborn as sns
import numpy as np
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![o22](https://github.com/abdulwasih2003/exno1/assets/91781810/e8ab5ba4-7d7b-452b-a78e-fa76bc94e1a8)

```py
sns.boxplot(data=af)
sns.scatterplot(data=af)
```
![o23](https://github.com/abdulwasih2003/exno1/assets/91781810/446ff3bd-b23a-4683-89bb-d1822a2db35a)

```py
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
![o25](https://github.com/abdulwasih2003/exno1/assets/91781810/db23e9d0-fe1a-49bf-a66e-7c34acc32e29)

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
![o26](https://github.com/abdulwasih2003/exno1/assets/91781810/59e8c257-ce90-4895-96c6-80306955952c)

```py
af=af[((af>=lower_bound)&(af<=upper_bound))]
af.dropna()
sns.boxplot(data=af)
```
![o29](https://github.com/abdulwasih2003/exno1/assets/91781810/8349c72b-b5be-4b48-b77c-34b4f8c7989a)

```py
sns.scatterplot(data=af)
```
![o30](https://github.com/abdulwasih2003/exno1/assets/91781810/4cea6076-2e5e-44d4-9b22-72b897e58c82)

```py
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'Weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
z=np.abs(stats.zscore(df))
```
![o32](https://github.com/abdulwasih2003/exno1/assets/91781810/b6429c37-8876-4815-9d46-55febd5d10a1)

```py
print(df[z['Weight']>3])
```
![o33](https://github.com/abdulwasih2003/exno1/assets/91781810/b62675a0-7d89-4682-97fe-3c1a00b27b3b)

# Result:
Hence the Data Cleaning process is performed successfully on the given data using python code.
