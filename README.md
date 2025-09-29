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
  import pandas as pd
df=pd.read_csv("Encoding Data.csv") <br>
df <br>
<img width="901" height="471" alt="image" src="https://github.com/user-attachments/assets/9ec0805f-5792-4e0a-aeb9-7ad2285f59b3" /> <br>
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder <br>
pm=['Hot','Warm','Cold'] <br>
e1=OrdinalEncoder(categories=[pm]) <br>
e1.fit_transform(df[["ord_2"]]) <br>
<img width="922" height="353" alt="image" src="https://github.com/user-attachments/assets/9706631b-8cb6-4b05-8772-f13a9c8e2658" /> <br>
df['bo2']=e1.fit_transform(df[["ord_2"]])<br>
df<br>
<img width="941" height="452" alt="image" src="https://github.com/user-attachments/assets/4363e5c4-4e3f-4d19-b1c8-7a8ba4ceb76c" /><br>
le=LabelEncoder()<br>
dfc=df.copy()<br>
dfc['ord_2']=le.fit_transform(dfc['ord_2'])<br>
dfc<br>
<img width="904" height="491" alt="image" src="https://github.com/user-attachments/assets/4c443a9b-2396-4b61-a76f-9d828af44732" /><br>
from sklearn.preprocessing import OneHotEncoder<br>
ohe=OneHotEncoder(sparse=False)<br>
df2=df.copy()<br>
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))<br>
df=pd.concat([df2,enc],axis=1)<br>
df2<br>
<img width="910" height="665" alt="image" src="https://github.com/user-attachments/assets/c70d40d5-4799-46c7-b792-bf54cfebd6e5" /><br>
 pd.get_dummies(df2,columns=["nom_0"])<br>
 <img width="904" height="436" alt="image" src="https://github.com/user-attachments/assets/4de166f9-d383-40c4-ae85-b1fac96d9a76" /><br>
 pip install --upgrade category_encoders<br>
 <img width="905" height="675" alt="image" src="https://github.com/user-attachments/assets/6f424765-2420-4450-8c02-338bf1d58e1c" /><br>
 from category_encoders import BinaryEncoder<br>
 df=pd.read_csv("data.csv")<br>
 df<br>
 <img width="905" height="462" alt="image" src="https://github.com/user-attachments/assets/aa631e89-3169-4d72-b2ac-9ad157267142" /><br>
 be=BinaryEncoder()<br>
 nd=be.fit_transform(df['Ord_2'])<br>
 be<br>
 <img width="900" height="461" alt="image" src="https://github.com/user-attachments/assets/3187fa4d-be1a-4687-93f2-25a234fc9952" /><br>
 dfb=pd.concat([df,nd],axis=1)<br>
 dfb<br>
 <img width="912" height="442" alt="image" src="https://github.com/user-attachments/assets/107ec96c-4f9d-4de5-ad8d-08e78b88b925" /><br>
 from category_encoders import TargetEncoder<br>
 te=TargetEncoder()<br>
 CC=df.copy()<br>
 new=te.fit_transform(X=CC["City"],y=CC["Target"])<br>
 CC=pd.concat([CC,new],axis=1)<br>
 CC<br>
 <img width="913" height="538" alt="image" src="https://github.com/user-attachments/assets/40c90746-05e6-477e-b002-764ad82d52fb" /><br>
 import pandas as pd<br>
 from scipy import stats<br>
 import numpy as np<br>
 df=pd.read_csv("Data_to_Transform.csv")<br>
 df<br>
 <img width="915" height="602" alt="image" src="https://github.com/user-attachments/assets/647e3739-a751-4996-9e4c-014bcdb87174" /><br>
 df.skew()<br>
 <img width="913" height="182" alt="image" src="https://github.com/user-attachments/assets/dcfc1095-5cbe-4363-871d-96d6279183f1" /><br>
 np.log(df["Highly Positive Skew"])<br>
 <img width="917" height="327" alt="image" src="https://github.com/user-attachments/assets/f931df03-055e-4c45-94bb-6f61533dce2b" /><br>
 np.reciprocal(df["Moderate Positive Skew"])<br>
 <img width="887" height="317" alt="image" src="https://github.com/user-attachments/assets/a898e81c-dbbf-487a-a098-3b769187c1a9" /><br>
 np.sqrt(df["Highly Positive Skew"])<br>
 <img width="890" height="331" alt="image" src="https://github.com/user-attachments/assets/da4b7a9f-8553-46a1-ab0a-c4b16fcfd1af" /><br>
 np.square(df["Highly Positive Skew"])<br>
 <img width="903" height="323" alt="image" src="https://github.com/user-attachments/assets/136608bf-d63c-4479-ba10-7eaa10c6a4f5" /><br>
 df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])<br>
df<br>
<img width="917" height="550" alt="image" src="https://github.com/user-attachments/assets/81494213-9a66-448c-8a8e-61fdd9100e1b" /><br>
 df.skew()<br>
 <img width="911" height="206" alt="image" src="https://github.com/user-attachments/assets/40dd9dd0-62cb-4c4d-9f18-213f5d993778" /><br>
 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])<br>
 df.skew()<br>
 <img width="903" height="261" alt="image" src="https://github.com/user-attachments/assets/c5087a1b-1387-4b3f-b989-c8f8ecfbcef5" /><br>
 from sklearn.preprocessing import QuantileTransformer<br>
 qt=QuantileTransformer(output_distribution='normal')<br>
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])<br>
 df<br>
 <img width="908" height="604" alt="image" src="https://github.com/user-attachments/assets/d06a211b-59d8-4f91-ab73-1bf5f728bf36" /><br>
 import seaborn as sns<br>
 import statsmodels.api as sm<br>
 import matplotlib.pyplot as plt<br>
 sm.qqplot(df["Moderate Negative Skew"],line='45')<br>
 plt.show()<br>
 <img width="906" height="567" alt="image" src="https://github.com/user-attachments/assets/72b1769d-2f66-48b5-9a57-1ff011b1c7c5" /><br>
 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')<br>
 plt.show()<br>
 <img width="875" height="563" alt="image" src="https://github.com/user-attachments/assets/b917db02-0cee-4cf9-bc7f-759fd674460b" /><br>
 from sklearn.preprocessing import QuantileTransformer<br>
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)<br>
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])<br>
 sm.qqplot(df["Moderate Negative Skew"],line='45')<br>
plt.show()<br>
<img width="873" height="561" alt="image" src="https://github.com/user-attachments/assets/c734da98-8bb5-4698-b199-85254000ac3c" /><br>
 df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])<br>
 sm.qqplot(df["Highly Negative Skew"],line='45')<br>
 plt.show()<br>
 <img width="880" height="550" alt="image" src="https://github.com/user-attachments/assets/53dc16d1-cb84-48c6-b6ce-a34f2e46a160" /><br>
 dt=pd.read_csv("titanic_dataset.csv")<br>
 dt<br>
 <img width="923" height="660" alt="image" src="https://github.com/user-attachments/assets/0f957100-f663-464f-8614-716d00a311df" /><br>
from sklearn.preprocessing import QuantileTransformer<br>
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)<br>
dt["Age_1"]=qt.fit_transform(dt[["Age"]])<br>
sm.qqplot(dt['Age'],line='45') <br>
plt.show()<br>
<img width="887" height="557" alt="image" src="https://github.com/user-attachments/assets/cb605c29-0784-4322-b470-ba30855319b4" /><br>
 sm.qqplot(df["Highly Negative Skew_1"],line='45')<br>
 plt.show()<br>
 <img width="860" height="553" alt="image" src="https://github.com/user-attachments/assets/1510c9a8-dcbd-401c-9faf-156349e016d7" /><br>

# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

       
