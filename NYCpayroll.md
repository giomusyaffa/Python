# Step-by-Step Analysis on the NYC Citywide Payroll Data 💸
## Project Overview
This project analyzes the NYC Citywide Payroll dataset from Kaggle using Python. The analysis focuses on understanding payroll distribution, job roles, overtime patterns, and salary trends across fiscal years.
## Dataset Description
- **Source**: Kaggle - NYC Citywide Payroll Data
- **Key Features**:
  - Fiscal Year
  - Agency Name
  - Title Description
  - Work Location Borough
  - Base Salary
  - Pay Basis
  - Regular Hours
  - Regular Gross Paid
  - OT Hours
  - Total OT Paid
  - Total Other Pay
 ## Step 1: Import the Data
 Just like Excel and SQL, the first step we gotta do is import the data by downloading the CSV file from Kaggle and place it in your project folder. Then write this to the code editor.

<img width="760" height="252" alt="image" src="https://github.com/user-attachments/assets/b61e88fa-b083-4429-9e7f-cda018457b1b" />
 
 The dataset is loaded into a pandas DataFrame, which works like a table in SQL or a worksheet in Excel. 

- `import pandas as pd` basically imports the pandas library into the Python script. `pd` is just a short alias so we don’t have to type `pandas` every time.

- `df = pd.read_csv(
    "Citywide_Payroll_Data__Fiscal_Year_.csv"` reads the CSV file and loads it into a pandas DataFrame. `df` is just a variable name (short for dataframe)

- `low_memory=False` because the NYC Payroll dataset is very large (2+ million rows) so some columns contain mixed data types (numbers + text), using this reduces data type warnings and improves accuracy when loading large datasets.

## Step 2: Explore the Data
For starters, we use these three to see the data information overview:
<img width="934" height="332" alt="image" src="https://github.com/user-attachments/assets/c3f58cb0-96c3-49e2-ad90-7948715fe203" />

- `head()` previews the first few rows
- `info()` shows column types and missing values
- `describe()` provides summary statistics for numeric columns

And after you run the code it will return this:
<img width="1251" height="330" alt="image" src="https://github.com/user-attachments/assets/3e1aa438-571e-4981-9b5b-628858267a1d" />
<img width="546" height="639" alt="image" src="https://github.com/user-attachments/assets/ccfae0de-b30f-4173-8909-062a7dc8fc28" />
<img width="614" height="311" alt="image" src="https://github.com/user-attachments/assets/fa019c22-b78b-4602-979a-857a0f9d1e00" />



