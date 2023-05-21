### Ex-08-Data-Visualization-

### AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

### ALGORITHM

### STEP 1

Read the given Data

### STEP 2

Clean the Data Set using Data Cleaning Process

### STEP 3

Apply Feature generation and selection techniques to all the features of the data set

### STEP 4

Apply data visualization techniques to identify the patterns of the data.

### CODE

NAME:A.ARUVI

REG NO: 212222230014.
```# DATA
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import seaborn as sbn
df=pd.read_csv("/content/Superstore.csv",encoding='windows-1252')
df.head()

# DATA CLEANING
df.info()

df.isnull().sum()

1.Which Segment has Highest sales?
sbn.barplot(x=df['Segment'],y=df['Sales'])
plt.title("Highest Sales of the segment")

2.Which City has Highest profit?
sbn.barplot(x=df['City'],y=df['Profit'])
plt.title("Highest Profit of cities")

City=df.loc[:,["City","Profit"]]
df.head(5)
City=City.groupby(by=["City"]).sum().sort_values(by="Profit")
plt.figure(figsize=(10,10))
sbn.barplot(x=City.index,y="Profit",data=City)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()

3.Which ship mode is profitable?
sbn.barplot(x=df['Ship Mode'],y=df['Profit'])
plt.title("Profitable Ship Mode")

4.Sales of the product based on region.
sbn.barplot(x=df['Sales'], y=df['Region'])
plt.title("Sales of Product based on Region")

5.Find the relation between sales and profit.
sbn.lineplot(x=df['Sales'], y=df['Profit'])
plt.title("Relation between Sales and Profit")

6.Find the relation between sales and profit based on the following category. i) Segment ii)City iii)States iv)Segment and Ship Mode v)Segment, Ship mode and Region

i) Segment
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()

ii) City
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()

iii) States
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()

iv)Segment and Ship Mode
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()

v)Segment, Ship mode and Region
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.legend(title='Region')
plt.show()
```
### OUTPUT

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/0359860f-3db3-42c3-929d-e509d6b9a662)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/00a6e94a-89cd-440f-a648-7b28f904e573)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/1ae22178-4438-461c-bb51-fe3686332552)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/cfca8e10-29ad-4de5-a6c1-f00363b5828e)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/66bf2576-a95f-44cd-a1ba-5634e14619f9)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/dfd4f02d-3f49-4dd8-8eaa-5abc20514a50)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/c2a545cc-1c91-48ad-8723-93037b50bfad)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/8c58df57-cc03-4fd2-93d2-bb091ad1e40f)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/a8534f2d-c309-43ee-858a-019b49ef91bb)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/b19bbbe7-6e6f-486c-b4ba-895cce1548f3)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/217e32fa-9ed3-42df-a37b-b09b873cd671)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/16c9abd2-ee7a-421d-81aa-94a49dec1935)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/0f4f1c5f-b533-4040-adb6-b417bb940d98)

![image](https://github.com/Anandanaruvi/Ex-08-Data-Visualization-/assets/120443233/41c78f0d-1dd3-4351-b8ed-4289b05c1763)

### RESULT:

Hence the data visualization method for the given dataset applied successfully.
