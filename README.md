# Ex-07-Data-Visualization-

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
