## EXNO-3-DS

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
```
```
df=pd.read_csv("/content/Encoding Data (2).csv")
df
```
<img width="237" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/f123de62-d775-4d4a-ac01-d56379f47e9e">

```
from google.colab import drive
drive.mount('/content/drive')
```
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
<img width="164" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/72600df4-d9e2-4fdb-8e4e-bfc7a8fdd2a6">
```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
<img width="254" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/96561bda-34a5-4670-ac1c-827c28fd542a">
```
le=LabelEncoder()
dfc=df.copy()
dfc["ord_2"]=le.fit_transform(dfc["ord_2"])
dfc
```
<img width="278" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/f4fd2b73-e41d-48ef-95a3-21442d681802">

```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2
```
<img width="282" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/16e36ec9-3f71-43ad-8d58-f9dcee249379">

```
pd.get_dummies(df2,columns=["nom_0"])
```
<img width="412" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/b7e33c19-e9f7-4f18-afb3-44207c695e0c">

```
pip install --upgrade category_encoders
```
<img width="750" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/b9ee12ae-f07d-4a9b-a4e0-90e1934489f4">
```
from category_encoders import BinaryEncoder
df=pd.read_csv("")
```
```
pip install --upgrade category_encoders
```
<img width="731" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/aecad41c-6b13-4d62-8cb6-f9e4624b7626">

```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```
<img width="432" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/f7461fda-a3fd-45d7-84b0-70c0aea8a36d">

```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc
```
<img width="449" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/9a2bd082-0106-47c5-b3ca-cd4ba685e258">
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data (2).csv")
df
```
<img width="245" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/efae3b05-5912-45e2-969f-7b22d6d41f21">

```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df

```
<img width="467" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/ab576b24-72ac-4275-905f-86125df7e34e">

```
df.skew
```
<img width="514" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/3b889ada-91a1-464c-a1cd-bd6a8784e99e">
```
df.skew()
```
<img width="242" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/f38178be-88c9-4d09-97b8-349c82b76728">

```
np.log(df["Highly Positive Skew"])
```
<img width="424" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/bf48d9c9-8a36-4f2a-8cc3-322b4ac9c7d0">

```
np.reciprocal(df["Moderate Positive Skew"])
```
<img width="353" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/19772a39-5376-40b9-9398-66e9ba1a66ec">

```
np.sqrt(df["Highly Positive Skew"])
```
<img width="295" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/2b7ab12f-5d8e-45f8-9e66-839ec6ac67e2">

```
<img width="360" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/c7bdf03d-d423-4ee1-9435-667a0443c73f">

```
np.square(df["Highly Positive Skew"])
```
<img width="320" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/6043b866-f915-4583-9350-b7c97fc682d6">
```
df
```
<img width="249" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/3ef889ff-55b6-42a6-b4ab-5385b149b8da">

```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
<img width="596" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/d959a585-01e5-44c7-bbd6-1f22bf2932e1">

```
df.skew()
```
<img width="228" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/1ba28a42-413a-42cc-ae97-11a75f062ff5">

```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
```
<img width="264" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/54a3b99f-e99f-443a-95bb-a90cbfd41c32">

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
```
```
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show
```
<img width="521" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/a9f5ce8a-d2f4-486d-9abd-2e30593f3696">

```
sn.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
<img width="491" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/05f076d5-d16e-4dd1-b514-896357737f1f">

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="404" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/68663349-9684-41be-b754-2531c3210dfb">

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df['Highly Negative Skew'],line='45')
plt.show()
```
<img width="477" alt="image" src="https://github.com/Jeevapriya14/EXNO-3-DS/assets/121003043/94d32968-aa17-4fb2-91c9-d6c952cdb58f">








# RESULT:
       # INCLUDE YOUR RESULT HERE

       
