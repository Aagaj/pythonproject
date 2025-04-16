
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
df=pd.read_csv("/Users/aagaj/Downloads/3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69 (1).csv")
df.head(2)
df.fillna(df.mean(numeric_only=True), inplace=True)
df.fillna(df.mode().iloc[0], inplace=True)
df.head()
if 'station' in df.columns and 'pollutant_avg' in df.columns:
    plt.figure(figsize=(8, 6))
    sns.barplot(x='station', y='pollutant_avg', data=df, palette="Blues_d")
    plt.title('Bar Chart: Average Pollutant by Station')
    plt.show()
    if 'city' in df.columns:
    city_counts = df['city'].value_counts()
    plt.figure(figsize=(7, 7))
    city_counts.plot.pie(autopct='%1.1f%%', startangle=90, colors=sns.color_palette('Set3', len(city_counts)))
    plt.title('Pie Chart: city Distribution')
    plt.ylabel('')
    plt.show()
if 'pollutant_avg' in df.columns:
    plt.figure(figsize=(8, 6))
    sns.histplot(df['pollutant_avg'], kde=True, color='blue', bins=10)
    plt.title('Histogram: Distribution of Pollutant Average')
    plt.xlabel('Pollutant Avg')
    plt.ylabel('Frequency')
    plt.show()
    if 'pollutant_avg' in df.columns and 'latitude' in df.columns:
    plt.figure(figsize=(8, 6))
    sns.scatterplot(x='pollutant_avg', y='latitude', data=df, hue='country', palette='Set1')
    plt.title('Scatter Plot: Pollutant Average vs Latitude')
    plt.xlabel('Pollutant Avg')
    plt.ylabel('Latitude')
    plt.show()
df.describe()
if 'longitude' in df.columns and 'pollutant_avg' in df.columns:
    plt.figure(figsize=(8, 6))
    sns.lineplot(x='longitude', y='pollutant_avg', data=df, marker='o', color='green')
    plt.title('Line Plot: Pollutant Avg over Longitude')
    plt.xlabel('Longitude')
    plt.ylabel('Pollutant Avg')
    plt.show()
numeric_df = df.select_dtypes(include=[np.number])
corr = numeric_df.corr()
plt.figure(figsize=(8, 6))
sns.heatmap(corr, annot=True, cmap='coolwarm', linewidths=0.5, fmt='.2f', center=0)
plt.title('Correlation Heatmap')
plt.show()
if 'country' in df.columns and 'pollutant_avg' in df.columns:
    plt.figure(figsize=(8, 6))
    sns.boxplot(x='country', y='pollutant_avg', data=df, palette="Set2")
    plt.title('Box Plot: Pollutant Avg by Country')
    plt.show()
summary = df.describe()
print("Summary Statistics:")
print(summary)

if all(col in df.columns for col in ['country', 'pollutant_avg', 'latitude']):
    plt.figure(figsize=(10, 8))
    sns.pairplot(df, hue='country', palette='Set1')
    plt.title('Pair Plot: Relationships between Columns')
    plt.show()

if 'country' in df.columns and 'pollutant_avg' in df.columns:
    Q1 = df['pollutant_avg'].quantile(0.25)
    Q3 = df['pollutant_avg'].quantile(0.75)
    IQR = Q3 - Q1
    df_no_outliers = df[(df['pollutant_avg'] >= Q1 - 1.5 * IQR) & (df['pollutant_avg'] <= Q3 + 1.5 * IQR)]
    plt.figure(figsize=(8, 6))
    sns.boxplot(x='country', y='pollutant_avg', data=df_no_outliers, palette="Set2")
    plt.title('Box Plot: Pollutant Avg by Country (Outliers Removed)')
    plt.show()
