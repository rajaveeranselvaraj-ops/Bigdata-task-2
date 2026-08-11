# Superstore Sales and Profit Analysis

## 📌 Project Overview

This project performs **exploratory data analysis (EDA)** on the **Sample Superstore dataset** using Python. The main objective is to understand sales, profit, product categories, delivery time, discounts, and relationships between numerical variables.

The project uses popular Python data-analysis and visualization libraries such as:

* **Pandas** – Data loading, cleaning, transformation, and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization

The dataset is loaded from a CSV file named `samplesuperstore.csv`.

---

## 🎯 Objectives

The major objectives of this project are:

1. Load the Superstore dataset into Python.
2. Understand the structure and basic information of the dataset.
3. Generate descriptive statistics.
4. Convert order and shipping dates into proper datetime format.
5. Calculate the number of days required for delivery.
6. Identify the available product categories.
7. Check for missing values.
8. Calculate total sales for each category.
9. Visualize sales performance by category.
10. Analyze the distribution of sales.
11. Compare profit across different categories.
12. Analyze sales distribution across categories.
13. Study profit distribution and variation.
14. Analyze the relationship between discount and profit.
15. Calculate correlations between numerical variables.
16. Display the correlations using a heatmap.

---

## 🛠️ Technologies Used

| Technology                      | Purpose                        |
| ------------------------------- | ------------------------------ |
| Python                          | Main programming language      |
| Pandas                          | Data manipulation and analysis |
| NumPy                           | Numerical computation          |
| Matplotlib                      | Data visualization             |
| Seaborn                         | Statistical visualization      |
| Google Colab / Jupyter Notebook | Development environment        |
| CSV                             | Dataset format                 |

The Python program imports Pandas, NumPy, Matplotlib, and Seaborn before beginning the analysis.

---

## 📂 Project Structure

```text
Superstore-Analysis/
│
├── task_2_bda_(2).py
├── samplesuperstore.csv
└── README.md
```

### Files Description

#### `task_2_bda_(2).py`

Contains the complete Python implementation for loading, processing, analyzing, and visualizing the Superstore dataset.

#### `samplesuperstore.csv`

Contains the Superstore sales data used for analysis.

#### `README.md`

Provides project documentation, objectives, methodology, requirements, execution steps, and analysis details.

---

# 📊 Dataset

The project uses a **Sample Superstore dataset** containing information related to orders, shipping, categories, sales, profit, discounts, and other numerical attributes.

The dataset is loaded using Pandas:

```python
df = pd.read_csv("/content/samplesuperstore.csv")
```

The first few records are displayed using:

```python
df.head()
```

The structure and data types of the dataset are inspected using:

```python
df.info()
```

Descriptive statistical information is obtained using:

```python
df.describe()
```

These steps provide an initial understanding of the dataset.

---

# 🔄 Data Preprocessing

## 1. Date Conversion

The `Order Date` column is converted into datetime format:

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])
```

Similarly, the `Ship Date` column is converted:

```python
df['Ship Date'] = pd.to_datetime(df['Ship Date'])
```

Converting these columns into datetime format allows date-based calculations to be performed correctly.

---

## 2. Delivery Days Calculation

A new column named `Delivery Days` is created.

```python
df['Delivery Days'] = (df['Ship Date'] - df['Order Date']).dt.days
```

This calculates the number of days between the order date and shipping date.

### Formula

```text
Delivery Days = Ship Date - Order Date
```

The resulting value represents the delivery duration for each order.

---

## 3. Category Identification

The unique product categories in the dataset are identified using:

```python
df['Category'].unique()
```

This helps determine the different categories available for further sales and profit analysis.

---

## 4. Missing Value Analysis

Missing values are checked using:

```python
df.isnull().sum()
```

This provides the number of missing values present in each column.

---

# 📈 Exploratory Data Analysis

## 1. Sales by Category

The total sales for each product category are calculated using Pandas `groupby()`:

```python
category_sales = df.groupby('Category')['Sales'].sum()
```

This groups the data based on `Category` and calculates the total `Sales` for each category.

### Visualization

A bar chart is created:

```python
category_sales.plot(kind='bar', figsize=(8,5))
```

The chart represents:

* X-axis → Product Category
* Y-axis → Total Sales

The visualization helps compare sales performance between categories.

---

# 📊 Sales Distribution

A histogram is used to understand the distribution of sales values.

```python
sns.histplot(df['Sales'], bins=30)
```

The project uses 30 bins to divide the sales values into intervals.

```python
plt.title("Sales Distribution")
```

This visualization helps understand how sales values are distributed across the dataset.

---

# 💰 Profit Analysis

## 1. Profit by Category

A Seaborn bar plot is used to analyze profit across categories:

```python
sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)
```

The chart compares the profit associated with different product categories.

The visualization is titled:

```text
Profit by Category
```

---

## 2. Sales Distribution by Category

Another bar plot is created using:

```python
sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)
```

This visualization compares sales values across different product categories.

The chart title is:

```text
Sales Distribution by Category
```

---

# 📦 Profit Distribution

A box plot is used to analyze the overall distribution of profit:

```python
sns.boxplot(
    data=df,
    y="Profit"
)
```

The visualization is titled:

```text
Profit Distribution
```

A box plot can help identify:

* Median profit
* Spread of profit values
* Variation
* Potential outliers

---

# 📦 Profit Variation Across Categories

The project also analyzes how profit varies between product categories.

```python
sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)
```

The chart title is:

```text
Profit Variation Across Categories
```

This visualization allows the distribution and variation of profit to be compared across categories.

---

# 🏷️ Discount Analysis

The unique discount values are identified using:

```python
df["Discount"].unique()
```

This helps understand the discount values available in the dataset.

---

## Discount vs Profit

A scatter plot is used to examine the relationship between discount and profit:

```python
sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)
```

The chart is titled:

```text
Impact of Discount on Profit
```

The X-axis represents discount, while the Y-axis represents profit.

This visualization can be used to investigate whether different discount levels are associated with changes in profit.

---

# 🔗 Correlation Analysis

The project selects numerical columns from the dataset:

```python
numeric_df = df.select_dtypes(
    include="number"
)
```

A correlation matrix is then calculated:

```python
corr = numeric_df.corr()
```

Correlation analysis helps identify relationships between numerical variables.

---

# 🔥 Correlation Heatmap

A Seaborn heatmap is used to visualize the correlation matrix:

```python
sns.heatmap(
    corr,
    annot=True
)
```

The values are displayed directly on the heatmap using:

```python
annot=True
```

The chart is titled:

```text
Correlation Heatmap
```

The heatmap provides a visual representation of the relationships among numerical variables in the dataset.

---

# 🔬 Methodology

The overall workflow of the project is:

```text
                Start
                  │
                  ▼
          Load Superstore CSV
                  │
                  ▼
       Inspect Dataset Structure
                  │
                  ▼
        Generate Descriptive Stats
                  │
                  ▼
       Convert Date Columns
                  │
                  ▼
       Calculate Delivery Days
                  │
                  ▼
       Check Categories & Nulls
                  │
                  ▼
        Analyze Sales by Category
                  │
                  ▼
          Analyze Profit
                  │
                  ▼
         Analyze Sales Distribution
                  │
                  ▼
          Analyze Discounts
                  │
                  ▼
        Calculate Correlations
                  │
                  ▼
        Display Correlation Heatmap
                  │
                  ▼
                 End
```

---

# 📊 Visualizations Included

The project generates several visualizations:

| No. | Visualization                      | Purpose                                        |
| --: | ---------------------------------- | ---------------------------------------------- |
|   1 | Sales by Category                  | Compare total sales between categories         |
|   2 | Sales Distribution                 | Understand distribution of sales               |
|   3 | Profit by Category                 | Compare profit between categories              |
|   4 | Sales Distribution by Category     | Compare sales across categories                |
|   5 | Profit Distribution                | Study overall profit variation                 |
|   6 | Profit Variation Across Categories | Compare profit distributions                   |
|   7 | Discount vs Profit                 | Study relationship between discount and profit |
|   8 | Correlation Heatmap                | Visualize numerical correlations               |

---

# ⚙️ Installation

Make sure Python is installed on your computer.

Install the required libraries using:

```bash
pip install pandas numpy matplotlib seaborn
```

---

# ▶️ How to Run

## Option 1: Google Colab

1. Open Google Colab.
2. Upload `task_2_bda_(2).py`.
3. Upload `samplesuperstore.csv`.
4. Make sure the CSV path matches the path used in the program.
5. Run the program cells/code.

The original notebook information indicates that the work was generated using Google Colab.

---

## Option 2: Jupyter Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the Python file or convert/use the code in a notebook.

Place the dataset in the appropriate directory and update the CSV path if necessary.

---

## Option 3: Python

Run the Python program from the terminal:

```bash
python task_2_bda_(2).py
```

Make sure `samplesuperstore.csv` is available at the location specified in the program.

---

# 📁 Dataset Path

The current code uses:

```python
df = pd.read_csv("/content/samplesuperstore.csv")
```

This path is suitable for a Google Colab environment.

If running locally, change it to something such as:

```python
df = pd.read_csv("samplesuperstore.csv")
```

or provide the appropriate full file path.

---

# 🧠 Key Concepts Demonstrated

This project demonstrates practical usage of:

### Pandas

* `read_csv()`
* `head()`
* `info()`
* `describe()`
* `to_datetime()`
* `groupby()`
* `isnull()`
* `select_dtypes()`
* `corr()`

### NumPy

NumPy is imported as part of the numerical analysis environment.

### Matplotlib

Used for:

* Bar charts
* Figure sizing
* Chart titles
* Axis labels
* Displaying plots

### Seaborn

Used for:

* Histograms
* Bar plots
* Box plots
* Scatter plots
* Heatmaps

---

# 📌 Expected Outcomes

After running the project, the user can obtain:

* Basic information about the Superstore dataset
* Descriptive statistics
* Converted order and shipping dates
* Delivery duration for each record
* Available product categories
* Missing-value information
* Category-wise sales totals
* Sales distribution
* Category-wise profit analysis
* Profit distribution
* Profit variation across categories
* Discount values
* Discount-profit relationship
* Correlation matrix
* Correlation heatmap

---

# 🚀 Future Enhancements

The current project focuses on exploratory analysis. It can be extended with:

1. **Regional Analysis** – Compare sales and profit across regions.
2. **Customer Analysis** – Identify high-value customers.
3. **Time-Series Analysis** – Analyze monthly and yearly sales trends.
4. **Top Products** – Find the products generating the highest sales and profit.
5. **Loss Analysis** – Identify products or categories generating negative profit.
6. **Interactive Dashboard** – Build a dashboard using Power BI, Tableau, or Plotly.
7. **Advanced Statistical Analysis** – Perform deeper statistical testing.
8. **Predictive Analysis** – Predict future sales or profit.
9. **Machine Learning** – Develop models for sales or profit prediction.
10. **Automated Reporting** – Generate analysis reports automatically.

---

# ⚠️ Notes

* The CSV file must be available before executing the program.
* The current dataset path is configured for Google Colab.
* The code assumes that the required columns such as `Order Date`, `Ship Date`, `Category`, `Sales`, `Profit`, and `Discount` are present in the dataset.
* The analysis is primarily exploratory and visualization-based.
* The source code checks for missing values but does not perform a missing-value replacement step.

---

# 👨‍💻 Project Summary

This **Superstore Sales and Profit Analysis** project demonstrates how Python can be used for practical **Big Data Analytics and Exploratory Data Analysis**.

The project follows a complete analytical workflow:

**Data Loading → Data Inspection → Data Preprocessing → Feature Creation → Exploratory Analysis → Visualization → Correlation Analysis**

Through this analysis, the project provides a structured approach to understanding sales, profit, categories, delivery time, discounts, and numerical relationships within the Superstore dataset.

---

## 📜 License

This project is intended for educational and academic purposes.

---

## ⭐ Conclusion

The Superstore analysis demonstrates the practical application of Python libraries for data analytics. By combining Pandas for data manipulation with Matplotlib and Seaborn for visualization, the project transforms raw sales data into meaningful analytical information.

The analysis covers the complete basic EDA process, from loading and inspecting the dataset to examining sales, profit, discounts, and correlations.
