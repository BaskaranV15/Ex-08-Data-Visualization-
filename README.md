# Ex-08-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.info()
df.isnull().sum()
df.duplicated().sum()

sns.lineplot(x='Segment',y='Sales',data=df,hue='Profit',marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation=90)
plt.show()
sns.lineplot(x='Segment',y='Sales',data=df)
plt.title("Segment vs Sales")
plt.xticks(rotation=90)
plt.show()

sns.barplot(x='Segment',y='Sales',data=df)
plt.title("Segment vs Sales")
plt.xticks(rotation=90)
plt.show()

hig_profit=df.loc[:,["City","Profit"]]
hig_profit=hig_profit.groupby(by=['City']).sum().sort_values(by=['Profit'])
plt.figure(figsize=(60,15))
sns.barplot(x=hig_profit.index,y='Profit',data=hig_profit)
plt.xticks(rotation=90)
plt.title("city vs profit")
plt.show()

sns.barplot(x="Segment",y="Profit",data=df)
plt.show()
sns.lineplot(x="Segment",y="Profit",data=df)
plt.show()

sns.barplot(x="Sales",y="Profit",data=df)
plt.show()

sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()
sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()

hig_profits=df.loc[:,["Ship Mode","Profit"]]
hig_profits=hig_profits.groupby(by=['Ship Mode']).sum().sort_values(by=['Profit'])
plt.figure(figsize=(18,8))
sns.barplot(x=hig_profits.index,y='Profit',data=hig_profits)
plt.xticks(rotation=90)
plt.title("Ship Mode vs profit")
plt.show()

reg_pro=df.loc[:,["Region","Sales"]]
reg_pro=reg_pro.groupby(by=["Region"]).sum().sort_values(by="Sales")
plt.figure(figsize=(18,7))
sns.barplot(x=reg_pro.index,y='Sales',data=reg_pro)
plt.xticks(rotation=90)
plt.title("Region vs Sales")
plt.show()

df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)
df["Sales"].corr(df["Profit"])
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()
sns.pairplot(df_corr, kind="scatter")
plt.show()

grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()



grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.legend(title='Region')
plt.show()
```
# OUPUT
![Screenshot 2023-05-30 152710](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/46d1b03d-d13d-43ff-a218-dd44f2da8490)
![Screenshot 2023-05-30 152740](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/1577e459-61f6-47c3-ae5b-85be47f34871)
![Screenshot 2023-05-30 152756](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/d9e0d574-8327-4370-bbc7-655b865c2954)
![Screenshot 2023-05-30 152820](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/5106d83f-8c65-4cdb-8ad3-7baeb180f6d5)
![Screenshot 2023-05-30 152831](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/0eaa593b-33ce-4a52-b671-9ec5100d5a1a)
![Screenshot 2023-05-30 152840](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/09080223-fd4a-4c59-993f-c3470ca08626)
![Screenshot 2023-05-30 152849](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/b8e3f57f-bb05-484a-a2f6-0c77e7d42f8c)
![Screenshot 2023-05-30 152858](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/97d1e8cb-02c1-4f25-abaa-4ff83191c0b2)
![Screenshot 2023-05-30 152907](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/4e2588e9-bba2-471e-be9c-f8a6af2a4d6a)
![Screenshot 2023-05-30 152915](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/f8d76e51-ea25-4308-bceb-7e90bee40a90)
![Screenshot 2023-05-30 152956](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/50ca2e32-0888-4e8e-be33-6a969d3c0a7b)
![Screenshot 2023-05-30 153007](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/f8b71872-ae93-481e-8f05-d220a3820faf)
![Screenshot 2023-05-30 153019](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/6b9a25b6-1da9-44a7-bcae-f7973445e623)
![Screenshot 2023-05-30 153025](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/dc49cdc3-d2ce-45f7-8212-41165b39bf94)
![Screenshot 2023-05-30 153036](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/1ad652cb-05a1-4a26-9d3e-a09c3efb2809)
![Screenshot 2023-05-30 153044](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/f147a709-4005-443f-8ceb-d5fb7b4d4160)
![Screenshot 2023-05-30 153053](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/9e9d2482-0aed-449c-98a6-2e09a4ec709d)
![Screenshot 2023-05-30 153108](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/7b2ff585-1208-4d1a-ae4d-ba0c8aeb1806)
![Screenshot 2023-05-30 153118](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/a6055a11-38b3-4211-afa8-46aa5eb4f58a)
![Screenshot 2023-05-30 153127](https://github.com/BaskaranV15/Ex-08-Data-Visualization-/assets/118703522/96c65660-f874-4ca8-8a36-1f2a82ee5c0d)
# RESULT 
By using visual elements like charts, graphs, etc, to visualization a data
