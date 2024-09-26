## EXNO-3-DS
### suriya prakash.s
### 212223100055

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df

```
![alt text](1.png)

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=["Hot","Warm","Cold"]
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
df["bo2"]=e1.fit_transform(df[["ord_2"]])
df
```
![alt text](2.png)

```
le=LabelEncoder()
dfcpy=df.copy()
dfcpy["ord_2"]=le.fit_transform(dfcpy["ord_2"])
dfcpy
```
![alt text](3.png)

```
from sklearn.preprocessing import OneHotEncoder
OHE = OneHotEncoder()
df2 = df.copy() 
enc = pd.DataFrame(OHE.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2

```
![alt text](4.png)

```
pd.get_dummies(df,columns=["nom_0"])
```
![alt text](5.png)

```
pip install category_encoders
```
![alt text](6.png)

```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```
![alt text](7.png)

```
be=BinaryEncoder()
nd=be.fit_transform(df["Ord_2"])
dfb=pd.concat([df,nd],axis=1)
dfb1=dfb.copy()
dfb
```
![alt text](8.png)

```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc
```
![alt text](9.png)

```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```
![alt text](10.png)

```
df.skew()
np.log(df["Highly Positive Skew"])
```
![alt text](11.png)

```
np.reciprocal(df["Moderate Positive Skew"])
```
![alt text](12.png)

```
np.sqrt(df["Highly Negative Skew"])
```
![alt text](13.png)

```
np.sqrt(df["Highly Positive Skew"])
```
![alt text](14.png)

```
df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![alt text](15.png)

```
df["Moderate Negative Skew"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
df
```
![alt text](16.png)

```
df['Highly Negative Skew_yeojohnson'],parameters=stats.yeojohnson(df['Highly Negative Skew'])
df.skew()
```
![alt text](17.png)

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df['Moderate Negative Skew_1']=qt.fit_transform(df[["Moderate Negative Skew"]])  
df
```
![alt text](18.png)

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line="45")
plt.show()
```

![alt text](19.png)

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line="45")
plt.show()
```
![alt text](20.png)

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df['Moderate Negative Skew_2']=qt.fit_transform(df[["Moderate Negative Skew"]])  
sm.qqplot(df["Moderate Negative Skew_2"],line="45")
plt.show()

```
![alt text](21.png)

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line="45")
plt.show()
```
![alt text](22.png)

```
sm.qqplot(df["Highly Negative Skew_1"],line="45")
plt.show()
```
![alt text](23.png)

```
dt=pd.read_csv("/titanic_dataset.csv")
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt['Age_1']=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt["Age"],line="45")
plt.show()
```
![alt text](24.png)
```
sm.qqplot(dt["Age_1"],line="45")
plt.show()
```
![alt text](25.png)




# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.


       
