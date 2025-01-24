# python-week-7-analyzing-data

Task 1: Load and Explore the Dataset
Load the Dataset: First, you need to load the dataset. You can use a CSV file of your choice or a public dataset such as the Iris dataset.

python
Copy
import pandas as pd

# Load the dataset from a CSV file (replace 'your_dataset.csv' with the file path)
df = pd.read_csv('your_dataset.csv')

# Display the first few rows of the dataset
print(df.head())
Explore the Structure: Check the data types and look for missing values.

python
Copy
# Display basic info about the dataset (data types, non-null counts)
print(df.info())

# Check for missing values
print(df.isnull().sum())
Clean the Dataset: If there are missing values, you can either fill them with a value (e.g., the mean or median) or drop the rows or columns containing missing values.

python
Copy
# Filling missing values with the mean (for numerical columns)
df.fillna(df.mean(), inplace=True)

# Alternatively, you can drop rows with missing values:
# df.dropna(inplace=True)
Task 2: Basic Data Analysis
Compute Basic Statistics: Use .describe() to get a summary of statistics for numerical columns (mean, median, standard deviation, etc.).

python
Copy
# Display basic statistics for numerical columns
print(df.describe())
Group by a Categorical Column: Group the data by a categorical column (e.g., "species" in the Iris dataset) and calculate the mean for numerical columns.

python
Copy
# Group by the 'species' column and compute the mean of numerical columns
print(df.groupby('species').mean())
Identify Patterns: Look for interesting findings in the grouped data, such as differences in the mean values for different categories. For example, in the Iris dataset, the petal length might vary significantly across species.

Task 3: Data Visualization
For this part, we will use matplotlib and seaborn to create various plots.

Line Chart (Trends Over Time): If your dataset includes a time series (e.g., sales data), you can create a line chart to visualize trends over time.

python
Copy
import matplotlib.pyplot as plt

# Assuming the dataset has a 'date' and 'sales' column
df['date'] = pd.to_datetime(df['date'])  # Convert the 'date' column to datetime if it's not already

# Plotting the line chart for sales over time
plt.figure(figsize=(10, 6))
plt.plot(df['date'], df['sales'], label='Sales')
plt.title('Sales Trend Over Time')
plt.xlabel('Date')
plt.ylabel('Sales')
plt.legend()
plt.xticks(rotation=45)
plt.show()
Bar Chart (Comparison of Numerical Value Across Categories): Create a bar chart comparing the average value of a numerical column across different categories (e.g., average petal length per species in the Iris dataset).

python
Copy
import seaborn as sns

# Bar chart for average petal length per species
plt.figure(figsize=(8, 5))
sns.barplot(x='species', y='petal_length', data=df)
plt.title('Average Petal Length per Species')
plt.xlabel('Species')
plt.ylabel('Average Petal Length')
plt.show()
Histogram (Distribution of a Numerical Column): A histogram can help you understand the distribution of a numerical column.

python
Copy
# Histogram of petal length distribution
plt.figure(figsize=(8, 5))
sns.histplot(df['petal_length'], bins=20, kde=True)
plt.title('Distribution of Petal Length')
plt.xlabel('Petal Length')
plt.ylabel('Frequency')
plt.show()
Scatter Plot (Relationship Between Two Numerical Columns): A scatter plot can be used to visualize the relationship between two numerical variables (e.g., sepal length vs. petal length).

python
Copy
# Scatter plot to visualize relationship between sepal length and petal length
plt.figure(figsize=(8, 5))
sns.scatterplot(x='sepal_length', y='petal_length', data=df)
plt.title('Sepal Length vs Petal Length')
plt.xlabel('Sepal Length')
plt.ylabel('Petal Length')
plt.show()
Additional Customization
You can improve the visuals by adding grid lines, changing the colors, or using a more customized style. For example:

python
Copy
# Change plot style
sns.set(style="whitegrid")
Error Handling
Make sure to handle errors like file not found, missing columns, or incorrect data types. For example:

python
Copy
try:
    df = pd.read_csv('your_dataset.csv')
    print(df.head())
except FileNotFoundError:
    print("The specified file was not found.")
except pd.errors.EmptyDataError:
    print("The file is empty.")
