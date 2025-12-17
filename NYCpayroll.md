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

## Step 2: Explore and Clen the Data
For starters, we use these three to see the data information overview:
<img width="934" height="332" alt="image" src="https://github.com/user-attachments/assets/c3f58cb0-96c3-49e2-ad90-7948715fe203" />

- `head()` previews the first few rows
- `info()` shows column types and missing values
- `describe()` provides summary statistics for numeric columns

And after you run the code it will return this:
<img width="1251" height="330" alt="image" src="https://github.com/user-attachments/assets/3e1aa438-571e-4981-9b5b-628858267a1d" />
<img width="546" height="639" alt="image" src="https://github.com/user-attachments/assets/ccfae0de-b30f-4173-8909-062a7dc8fc28" />
<img width="614" height="311" alt="image" src="https://github.com/user-attachments/assets/fa019c22-b78b-4602-979a-857a0f9d1e00" />

Now, pay attention to the columns that should be numbers but are NOT:
- `Base salary` : object
- `Regular gross paid` : object
- `Total OT paid` : object
- `Total other pay` : object

These are salary-related columns that are still in a text form and we cant do any analysis on these yet.

Why did this happened?
Cause if you see at the raw data, you can see that the values still have the $ sign in them

<img width="246" height="430" alt="image" src="https://github.com/user-attachments/assets/82549c29-c0bc-4c5b-9a12-dd48978612ad" />

This explain how it's a string not a number.

So what are we supposed to do?

We clean and convert those column to turn this
`$47166.03 -> object`

to this

`47166 -> float64`

<img width="1125" height="577" alt="image" src="https://github.com/user-attachments/assets/74a5239b-8884-4776-a28a-d826dbe5948f" />

So, what this code do is basically removes `$` and `,`

And how would you know if it worked?

<img width="500" height="663" alt="image" src="https://github.com/user-attachments/assets/e6560083-e59e-413f-a911-26656eb68423" />

Is by returning this after you run the code, as you can see the base salary, regular gross paid, total ot paid, and total other pay are already in `float64`.

Now were ready for some analysis.

## Step 2: Analyze the Data

### Analysis 1: Average salary by agency

<img width="759" height="316" alt="image" src="https://github.com/user-attachments/assets/ecbd5afd-385c-4e0a-a03f-da2bb8daea2f" />

What it does: 
- Groups employees by agency
- Calculates average base salary
- Sorts from highest to lowest
- Shows the top 10 agencies

<img width="713" height="341" alt="image" src="https://github.com/user-attachments/assets/c02fd111-f1ea-4e44-81d6-976f1777d92f" />

This tells us which agency pay the highest base salary on average, which is the **DISTRICTING COMMISSION**

### Analysis 2: Top job titles by average salary

<img width="868" height="282" alt="image" src="https://github.com/user-attachments/assets/cfe9ec38-f137-4ca4-aa1f-7901c396256e" />

What it does:
- Groups by job title
- Finds which roles are paid the most
- Very useful for career + compensation insights

<img width="963" height="341" alt="image" src="https://github.com/user-attachments/assets/95b87e74-8f21-450e-9025-2f2741d016e2" />

This tells us that **PENSION INVESTMENT ADVISOR** receieves the highest salary by average.

### Analysis 3: Overtime analysis

<img width="838" height="285" alt="image" src="https://github.com/user-attachments/assets/f852d7f9-55c6-402f-9639-c2986ab52783" />

What it shows:
- Agencies that rely heavily on overtime
- Potential staffing or budget issues

<img width="563" height="359" alt="image" src="https://github.com/user-attachments/assets/d220c5e6-f4b0-49e5-99dd-f9969cfcc192" />

And as you can see the **POLICE DEPARTMENT** is the top agency that has the most overtime which shows a problem in staffing.

## Analysis 4: Regular pay bs overtime pay

<img width="882" height="334" alt="image" src="https://github.com/user-attachments/assets/97a76eff-7892-4ab8-994b-30d2c47307e5" />

What it does:
- Creates a new calculated metric
- Shows which agencies depend most on OT relative to regular pay

<img width="623" height="377" alt="image" src="https://github.com/user-attachments/assets/802122c6-d637-452b-9c50-400242f13d19" />

This shows that the **BRONX DISTRICT ATTORNEY** receives most of their pay in OT rather than their regular pay.

## Analysis 5: Payroll trends by year

<img width="797" height="246" alt="image" src="https://github.com/user-attachments/assets/f96e5cbf-fd7d-42ce-b894-7bcae74378a6" />

What it shows:
- How NYC payroll changes over time
- Great for public finance analysis

<img width="537" height="776" alt="image" src="https://github.com/user-attachments/assets/d15dc622-797a-44b7-a022-98e385bfb315" />

