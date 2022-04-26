# Ex-04-EDA
## AIM
To perform EDA on the given data set.

## Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM
## STEP 1:
Import the required packages(pandas,numpy,seaborn).

## STEP 2:
Read and Load the Dataset

## STEP 3:
Remove the null values from the data and remove the outliers.

## STEP 4:
Remove the non numerical data columns using drop() method.

## STEP 5:
returns object containing counts of unique values using (value_counts()).

## STEP 6:
Plot the counts in the form of Histogram or Bar Graph.

## STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).

## STEP 8:
Save the final data set into the file.

## CODE:
```
DEVELOPED BY:LOGESHWARI.P
REG NO:212221230055
```
```
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
df= pd.read_csv('supermarket.csv')
df.head()
df.info()
df.isnull().sum()
df.boxplot()
cols = ['Tax 5%', 'Total','gross margin percentage','Payment']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
df["Total"].value_counts()
plt.title('Grouped by Total')
sns.countplot(x="Total",data=df)
df["Payment"].value_counts()
plt.title('Grouped by Payment')
sns.countplot(x="Payment",data=df)
df["City"].value_counts()
plt.title('Grouped by City')
sns.countplot(x="City",data=df)
df["Product line"].value_counts()
plt.title('Grouped by Product line')
sns.countplot(x="Product line",data=df)
sns.displot(df["Quantity"])
sns.countplot(x="Gender",hue="Product line",data=df)
sns.countplot(x="Total",hue="Customer type",data=df)
pd.crosstab(df["Total"],df["Payment"])
pd.crosstab(df["Quantity"],df["City"])
df.corr()
sns.heatmap(df.corr(),annot=True)
```
## OUPUT:
![1](https://user-images.githubusercontent.com/94211349/162873324-4506ca46-32bc-4748-b113-c93cd84b890c.png)
![2](https://user-images.githubusercontent.com/94211349/162873341-6b3d4b9b-825e-4e7d-ab62-1d04d7d03c2f.png)
![3](https://user-images.githubusercontent.com/94211349/162873368-5bb48132-7bce-40a5-97da-75417e707fcf.png)
![4](https://user-images.githubusercontent.com/94211349/162873392-63171e23-8f04-4302-83c1-6ac369ca5735.png)
![5](https://user-images.githubusercontent.com/94211349/162873414-d9b3b97a-512c-4fb6-8a28-103d21bd193d.png)
![6](https://user-images.githubusercontent.com/94211349/162873430-26a670f3-128d-4e80-8373-cd83580440e7.png)
![7](https://user-images.githubusercontent.com/94211349/162873443-4bf778cb-e5c7-4c32-90c8-be775c086b2f.png)
![8](https://user-images.githubusercontent.com/94211349/162873480-28b2e3c0-a0a6-4799-bd5e-613b215eb83d.png)
![9](https://user-images.githubusercontent.com/94211349/165212886-ff1d0ae7-8d7d-488b-9885-1f1e5f85013c.png)
![10](https://user-images.githubusercontent.com/94211349/165212917-e30f891f-4a08-45e0-931a-03b09ff51767.png)
![11](https://user-images.githubusercontent.com/94211349/165212943-5c074c62-a35a-44a5-a37c-b673ea301220.png)
![12](https://user-images.githubusercontent.com/94211349/165212965-60ff0606-e480-4b7e-9698-617c02230461.png)
![13](https://user-images.githubusercontent.com/94211349/165212979-e793c5f6-4837-4bb0-b786-0ed19fec4c81.png)
![14](https://user-images.githubusercontent.com/94211349/165213008-a6badf76-73de-4442-b22b-9c1c00c7a130.png)
![15](https://user-images.githubusercontent.com/94211349/165213029-5b2e0917-c5e2-4018-be5b-626000f0210b.png)
![16](https://user-images.githubusercontent.com/94211349/165213044-ba0d936e-14d7-4564-9fc4-c05c2c53c4e1.png)
![17](https://user-images.githubusercontent.com/94211349/165213056-bb034a11-b963-466d-80c7-5cf921e3bc6a.png)

### RESULT:
The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.
