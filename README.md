# Healthcare Dataset Analysis

## 1. Introduction

This project is about analyzing a healthcare dataset using Python. The main purpose of this project is to understand patient and hospital-related information, clean the dataset, and perform basic data analysis.

The analysis was done using **Google Colab** with Python libraries such as **Pandas, Matplotlib, and Seaborn**.

## 2. Technologies Used

* Python
* Google Colab
* Pandas
* Matplotlib
* Seaborn

## 3. Dataset

The project uses a healthcare dataset named:

`healthcare_dataset (1).csv.xls`

The dataset contains information related to patients, hospital admissions, medical details, billing amounts, admission types, and admission and discharge dates.

## 4. Data Loading

First, the dataset was imported using the Pandas library.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("/content/healthcare_dataset (1).csv.xls")
```

The dataset was then displayed to understand the available records and columns.

## 5. Data Exploration

The following Pandas functions were used to understand the dataset:

* `df.head()` – displays the first few records.
* `df.info()` – shows column names, data types, and non-null values.
* `df.describe()` – provides statistical information about numerical columns.
* `df.isnull().sum()` – checks for missing values in each column.

## 6. Handling Missing Values

Missing values in object/string columns were identified and replaced with the value:

`not gather`

The following code was used:

```python
for column in df.select_dtypes(include='object').columns:
    df[column] = df[column].fillna('not gather')
```

After filling the missing values, the dataset was checked again to confirm the remaining missing values.

## 7. Date Conversion

The `Admission_Date` and `Discharge_Date` columns were converted into Pandas datetime format.

```python
df['Admission_Date'] = pd.to_datetime(df['Admission_Date'])
df['Discharge_Date'] = pd.to_datetime(df['Discharge_Date'])
```

This conversion makes it easier to perform calculations using the admission and discharge dates.

## 8. Admission Type Analysis

The different types of hospital admissions were analyzed using:

```python
print(df['Admission_Type'].value_counts())
```

The admission type values were then converted into lowercase to maintain consistency.

```python
df['Admission_Type'] = df['Admission_Type'].str.lower()
```

## 9. Hospital Stay Calculation

A new column called `Hospital_Stay_Days` was created to calculate the number of days each patient stayed in the hospital.

```python
df['Hospital_Stay_Days'] = (
    df['Discharge_Date'] - df['Admission_Date']
).dt.days
```

The statistical summary of hospital stay duration was then obtained using:

```python
df['Hospital_Stay_Days'].describe()
```

## 10. Billing Amount Analysis

The `Billing_Amount` column was analyzed using the `describe()` function.

```python
print(df['Billing_Amount'].describe())
```

This provides information such as:

* Count
* Mean
* Standard deviation
* Minimum value
* Maximum value
* Quartiles

## 11. Medical Code Check

The `Medical_Code` column was also checked for missing values using:

```python
df['Medical_Code'].isnull()
```

This helps identify whether medical code information is available for the records.

## 12. Conclusion

In this project, the healthcare dataset was loaded and explored using Python and Pandas. Missing values were handled, date columns were converted into the correct format, admission types were standardized, and hospital stay duration was calculated.

The project helped in understanding basic **data cleaning, data exploration, date processing, and statistical analysis** using
