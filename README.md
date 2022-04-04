# Ex-02_DS_Outlier
# Aim
To Detect and Remove Outliers from the given Dataset.
## Explanation
The analysis for outlier detection is referred to as outlier mining. There are many ways to detect the outliers, and the removal process is the data frame same as removing a data item from the panda’s data frame.

Here pandas data frame is used for a more realistic approach as in real-world project need to detect the outliers arouse during the data analysis step, the same approach can be used on lists and series-type objects.

## ALGORITHM
```
STEP 1
Importing Necessary Packages

STEP 2
Read and Load the Dataset

STEP 3
Plot the Distribution plots for the features

STEP 4
Finding the IQR,upper,lower limit and Outliers

STEP 5
Form a Box-plot for the skewed feature
```

## code
```
import pandas as pd
df=pd.read_csv("weight.csv")
df.drop("Gender",axis=1)
df.drop("Gender",axis=1,inplace=True)
df
df.boxplot()

from scipy import stats
import numpy as np
z=np.abs(stats.zscore(df))
z

df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1
df1.boxplot()

df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df2_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df2_new.boxplot()
df2_new

```
## output
output1:![image](https://user-images.githubusercontent.com/94165326/161598657-e07d7ff7-ef33-4302-ab65-6f26c496ece3.png)
output2:![image](https://user-images.githubusercontent.com/94165326/161598801-3add0019-6ea3-4e83-b0e6-293d7ab78bb9.png)
output3:![image](https://user-images.githubusercontent.com/94165326/161598880-884bded2-60d3-48c4-8b20-62290f0b357d.png)
output4:![image](https://user-images.githubusercontent.com/94165326/161599059-a305c92a-41bc-4fea-9c4a-c058c1b841ef.png)
output5:![image](https://user-images.githubusercontent.com/94165326/161599359-da0983ba-f931-4bc6-b1b8-8eb5e9666bc9.png)
## RESULT:
The Outliers are detected and removed from the Dataset.
