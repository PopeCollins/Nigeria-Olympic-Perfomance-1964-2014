# [Nigeria-Olympic-Perfomance-1964-2014](https://popecollins.github.io/Nigeria-Olympic-Perfomance-1964-2014/)

### The performance of Nigerian during the olympic
1. This data (name: athlete_events )was downloaded on kaggle 
2. An exploratory data analysis was carried out in other to know the performance of Nigeria during previous olympic
3. The data of those who ever won a medal was selected
4. Nigerian olympics participant data was selected 
5. The data analysis source code and chart were presented in this repository

## DATA ANALYSIS USING PYTHON 

### IMPORTING THE NECESSARY LIBRARY
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
%matplotlib inline
```

```python
sns.set_style('darkgrid')
plt.rcParams['font.size']=15
plt.rcParams['figure.figsize']= (10,7)
plt.rcParams['figure.facecolor']= '#FFE5B4'
```
### Loading athlete_events data
``` python
athletes= pd.read_csv(.... adjust base on location on your machine .../athlete_events.csv')
```
### Selecting Nigeria athletes who ever won a medal
```python
Nigeria= athletes_df[(athletes_df['Team']=='Nigeria')&(athletes_df['Medal'].notnull())]
Nigeria.shape
```
```python
Nigeria=Nigeria.reset_index()
Nigeria.head()
```
### Getting the Age distribution on those who ever won a medal
```python
plt.figure(figsize=(12,6))
plt.title('Age distribution of Nigeria athletes who ever won a medal at the olympic')
plt.xlabel('Age')
plt.ylabel('Number of participants')
plt.hist(Nigeria.Age, bins=np.arange(10,40,2), color='orange', edgecolor='white');
```
Age Distribution:
![alt text](https://github.com/PopeCollins/Nigeria-Olympic-Perfomance-1964-2014/blob/main/A1.png)

```python
Medal= Nigeria['Medal'].value_counts()
Medal
```
```python
Year= Nigeria.groupby('Year')['Year'].count()
Year
```
### Futher Analysis
```python
fig, axes=plt.subplots(1,2, figsize=(16,6))
plt.tight_layout(pad=2)
xlabels=Medal.index
axes[0].set_title("Medal Distribution")
axes[0].set_xticklabels(xlabels, rotation=45, ha='right')
sns.barplot(x = Medal.index, y = Medal, ax =axes[0], Label=Medal.index)
axes[0].set_xlabel('Medal')
axes[0].set_ylabel('Counts')

xlabels = Year.index
axes[1].set_title('Number of medals per year')
axes[1].set_xticklabels(xlabels, rotation=45, ha='right')
sns.barplot(x=Year.index, y=Year, ax =axes[1])
axes[1].set_xlabel('Year')
axes[1].set_ylabel('Counts')
```
### Image:
![](https://github.com/PopeCollins/Nigeria-Olympic-Perfomance-1964-2014/blob/main/A2.png)


### Performance base on Sport
```python
plt.figure(figsize=(10,5))
plt.title('Performance based on sport')
sns.countplot(data=Nigeria, x ="Sport", hue="Medal")
plt.grid(axis='x')
plt.legend(loc='upper right')
```
### Image:
![](https://github.com/PopeCollins/Nigeria-Olympic-Perfomance-1964-2014/blob/main/A3.png)

### Performance base on sport
``` python
plt.figure(figsize=(10,5))
plt.title('Medal based on Gender')
sns.countplot(data=Nigeria, x ="Medal", hue="Sex")
plt.grid(axis='x')
```
### Image:
![](https://github.com/PopeCollins/Nigeria-Olympic-Perfomance-1964-2014/blob/main/A4.png)
