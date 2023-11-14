# Ex-04 Multivariate Analysis
## AIM:
To perform Multivariate EDA on the given data set.
## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
### STEP 1:
Import the built libraries required to perform EDA and outlier removal.

### STEP 2:
Read the given csv file

### STEP 3:
Convert the file into a dataframe and get information of the data.

### STEP 4:
Return the objects containing counts of unique values using (value_counts()).

### STEP 5:
Plot the counts in the form of Histogram or Bar Graph.

### STEP 6:
Use seaborn the bar graph comparison of data can be viewed.

### STEP 7:
Find the pairwise correlation of all columns in the dataframe.corr()

### STEP 8:
Save the final data set into the file.
## PROGRAM:
```
Developed by: Ragavendran A
Register number :212222230114
```
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt=pd.read_csv("titanic_dataset.csv")
dt
dt.info()
dt.set_index("PassengerId",inplace=True)
dt.shape
dt.nunique()
dt["Survived"].value_counts()

per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per

dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")

fig,ax1=plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2,height+20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
sns.jointplot(x="Age",y="Fare",data=dt)
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")

g=sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax=g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.
  format(p.get_height()),color='red',rotation='horizontal',size='small')

corr=dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)

```
## OUTPUT:
![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/6801fb97-8256-4730-8429-2e6e430506f8)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/48f3c47c-ddea-4023-a950-655d5affe5af)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/f70e51b6-3514-46cc-b6f8-9dd94f32ecb9)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/2e783d46-b81f-4779-8a3b-220ed8129096)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/42bcaa18-8a24-4888-8544-19c23deb8e15)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/6dadaefc-688a-4e0b-a371-d7336e7bc400)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/d12e102d-9044-48db-9ac2-3c8702e503b2)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/f91bf614-19de-439a-9195-9167eff26df4)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/9cd019b8-1de5-4bb9-9987-7df2d4c473a6)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/360661b9-c86c-48e0-a858-b2856be64048)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/d10d0f18-e349-4157-a5c2-3acbf8ec1898)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/4a5d9fb1-7c34-4502-9413-7fb085e766f6)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/dbf61892-b4a3-4aba-aa32-e8cdfa02a566)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/56fda393-7204-4abe-a191-081f91fa4f4f)

<br>

![image](https://github.com/kavinesh8476/ODD2023-Datascience-Ex-04/assets/118466561/8d415cfb-ffae-4d30-af6f-5806f542676c)

## RESULT:
Thus we have read the given data and performed the multivariate analysis with different types of plots.
