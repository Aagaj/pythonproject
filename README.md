
# 🌍 Air Pollution Data Analysis

This repository contains a data analysis and visualization notebook built using Python libraries like **Pandas**, **NumPy**, **Seaborn**, and **Matplotlib**. The dataset used contains information about pollution levels across various cities, stations, and countries.

## 📁 Dataset

The dataset used in this project is a `.csv` file (example: `3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69.csv`) that includes fields such as:
- `station`
- `city`
- `country`
- `pollutant_avg`
- `latitude`
- `longitude`

## 🔧 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn

## 📊 Visualizations Included

This project generates multiple types of visualizations to understand the dataset:

1. **Bar Plot** – Average pollutant by station
2. **Pie Chart** – Distribution of entries by city
3. **Histogram** – Distribution of `pollutant_avg` values
4. **Scatter Plot** – Pollutant Average vs Latitude with country-wise hue
5. **Line Plot** – Pollutant Average across Longitudes
6. **Correlation Heatmap** – Relationship among numeric columns
7. **Box Plot** – Pollutant Average distribution per country
8. **Pair Plot** – Country-wise scatter relationships
9. **Outlier-Free Box Plot** – Refined pollutant averages by country

## 🧼 Data Cleaning

- Missing numeric values are filled with column means.
- Categorical missing values are filled with the mode.
- Outliers are handled using the IQR (Interquartile Range) method.

## 📈 Summary Statistics

The notebook also prints descriptive statistics using `df.describe()` to get insights into the dataset's distribution, central tendency, and spread.

## 📂 Usage

To run this project:

1. Clone the repository or download the `.ipynb`/`.py` file.
2. Make sure you have the required libraries installed:

```bash
pip install pandas numpy matplotlib seaborn
```

3. Replace the CSV path in the `read_csv()` method with your dataset path.
4. Run the script or notebook.

## 🧪 Sample Output

- Visual plots for easy understanding of trends
- Insights into pollution averages by location
- Detection and removal of outliers
- Heatmaps showing correlation between numerical columns

