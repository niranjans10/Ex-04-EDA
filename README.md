# Ex-04-EDA

## AIM
To perform EDA on the given data set.

## EXPLANATION
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM
## STEP 1
Import the required packages(pandas,numpy,seaborn).

## STEP 2
Read the given csv file and convert them into Dataframe.

## STEP 3
As the first step remove the null values from the dataframe

## STEP 4
Return the objects containing counts of unique values using (value_counts()).

## STEP 5
Plot the counts in the form of Histogram or Bar Graph.

## STEP 6
Find the pairwise correlation of all columns in the dataframe.corr() and save the cleaned data to the file.

## CODE:
```
import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("supermarket.csv")
df
df.info()
df.isnull().sum()
df.boxplot()
q1=df.quantile(0.25)
q3=df.quantile(0.75)
IQR=q3-q1
df = df[~((df < (q1 - 1.5 * IQR)) |(df > (q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
df["City"].value_counts()
df["Gender"].value_counts()
df["Customer type"].value_counts()
df["Product line"].value_counts()
df["Payment"].value_counts()
df["Branch"].value_counts()
sns.countplot(x="Gender",data=df)
sns.countplot(x="City",hue="Product line",data=df)
sns.countplot(x="Product line",hue="City",data=df)
sns.countplot(x="Branch",hue="Gender",data=df)
sns.countplot(x="City",data=df)
sns.countplot(x="Product line",data=df)
sns.countplot(x="Quantity",data=df)
sns.countplot(x="Time",data=df)
sns.countplot(x="City",hue="Payment",data=df)
sns.displot(df[df["Branch"]=="C"]["Payment"])
sns.displot(df[df["Product line" ]=="Home and lifestyle"]["Quantity"])
sns.displot(df[df["Payment"]=="Ewallet"]["City"])
sns.displot(df[df["Gender"]=="Female"]["City"])
sns.displot(df[df["Product line"]=="Home and lifestyle"]["Rating"])
pd.crosstab(df["Gender"],df["Branch"])
pd.crosstab(df["Branch"],df["Product line"])
pd.crosstab(df["Product line"],df["City"])
df.corr()
sns.heatmap(df.corr(),annot=True)

```

## OUPUT:
![O1](https://user-images.githubusercontent.com/102233600/163012106-ea8fde4a-72ba-41d0-befc-9c56d11146e2.png)
![O2](https://user-images.githubusercontent.com/102233600/163012130-c314e239-62e4-4997-bb10-45e1eb36db26.png)
![O3](https://user-images.githubusercontent.com/102233600/163012149-03de41be-2732-4fac-8ba8-db5d21ab64c7.png)
![O4](https://user-images.githubusercontent.com/102233600/163012155-9ff7f376-81e7-4efb-9265-807118f31c4c.png)
![O5](https://user-images.githubusercontent.com/102233600/163012162-82ea39e8-d1fc-42ae-b240-9b15d9b3aff7.png)
![O6](https://user-images.githubusercontent.com/102233600/163012174-71866c1b-9f27-4ea2-aba9-24e279e71693.png)
![O7](https://user-images.githubusercontent.com/102233600/163012183-246b9bca-7ba9-46c6-8e7a-28ff024ca582.png)
![O8](https://user-images.githubusercontent.com/102233600/163012201-a6a3ebb2-cdd5-4e92-83e3-de616ea54478.png)
![O9](https://user-images.githubusercontent.com/102233600/163012216-4c1c8362-d63f-4d71-8d03-12031982fe0f.png)
![O10](https://user-images.githubusercontent.com/102233600/163012255-2786bf31-25ac-4b1c-949d-82aa4e0f354b.png)
![O11](https://user-images.githubusercontent.com/102233600/163012272-29d9341b-4ac3-432d-90db-dade9966bb06.png)
![O12](https://user-images.githubusercontent.com/102233600/163012279-d507d042-0915-4c21-a76c-a9faeb62f14d.png)
![O13](https://user-images.githubusercontent.com/102233600/163012300-a2cce258-340d-4d68-b266-8a7fc2851a59.png)
![O14](https://user-images.githubusercontent.com/102233600/163012311-daf83d83-5b96-4ab7-a263-223559759e38.png)
![O15](https://user-images.githubusercontent.com/102233600/163012327-d7664c46-6ac5-4e74-8a08-d2b8a37d2ac8.png)
![O16](https://user-images.githubusercontent.com/102233600/163012335-fdd7bc1a-0ac4-49bd-ac9b-9349677aa141.png)

## RESULT
EDA on the given data set is performed successfully.
