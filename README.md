# Bank Loan Performance Analysis

## Problem Statement
In today's data-driven world, understanding how borrower details and loan characteristics impact loan performance is crucial for banking institutions. This project analyzes a lending loan dataset to uncover relationships between borrower behavior (e.g., employment length, income, debt-to-income ratio) and loan characteristics (e.g., amount, term, interest rate). The goal is to derive actionable insights into loan performance metrics, optimize lending strategies, mitigate credit risks, and enhance portfolio performance.

---

## Project Steps and Objectives

### 1. Importing Data
- Import the **"LoanDetails"** and **"BorrowerDetails"** sheets from the `bank loan.xlsx` file into Power BI.

### 2. Transformation Using Power Query

#### 2.1 Data Cleaning
- Replace missing values in `emp_length` with `'0 year'`.
- Remove rows with missing values in `last_pymnt_d` and `delinq_2yrs`.
- Remove duplicate rows in the `id` column of the **LoanDetails** table.

#### 2.2 Dealing with Inconsistencies
- Replace underscores with spaces in the `purpose` column.
- Format `purpose` and `home_ownership` columns to proper case.

#### 2.3 Data Transformation
- Change data type of `total_pymnt` to **Fixed decimal number**.
- Round off `funded_amnt` to 2 decimal places.
- Rename columns:
  - `issue_d` → `issue_date`
  - `last_pymnt_d` → `last_pymnt_date`
- Create new columns:
  - `total_amount_paid` = `total_pymnt` - `out_prncp`
  - `delinquency_status` = "Delinquent" if `delinq_2yrs` > 0, otherwise "Not Delinquent".
- Remove the `sub_grade` column.

---

### 3. Data Modeling
- Establish relationships between **LoanDetails** and **BorrowerDetails** using common columns with cross-filter direction set to "Both".

#### 3.1 Creating Measures and Calculated Columns (DAX)
- `remaining_installments`: Calculate remaining installments using `CEILING()`.
- `Non-Verified Borrowers Count`: Count loans that are "Not Verified".
- `Fully Paid Loan Percentage`: Calculate the percentage of fully paid loans.

#### 3.2 Creating Comprehensive Reports
- **Report 1: Loan Performance Analysis**
- **Report 2: Borrower Profile Analysis**
- Ensure clean, professional layouts and enhance visual appeal with slicers, tooltips, and titles.

---

## Report 1: Loan Performance Analysis
### Key Visuals
- **Card**: Total Funded Amount.
- **Gauge Chart**: Fully Paid Loan Percentage.
- **Multi-row Card**: Average Interest Rate by Term.
- **Pie Chart**: Loan Status Distribution.
- **Treemap**: Loan Amount by Purpose.
- **Line Chart**: Installments Over Time.
- **Column Chart**: Maximum Total Amount Paid by Loan Status.
- **Funnel Chart**: Minimum Annual Income by Grade.
- **Slicer**: Month of Issue Date.

---

## Report 2: Borrower Profile Analysis
### Key Visuals
- **KPI Visual**: Total Payment, Trend Axis = Year of Last Payment, Target = Sum of Loan Amount.
- **Card**: Average Annual Income.
- **Card**: Non-Verified Borrowers Count.
- **Multi-row Card**: Average Debt-to-Income by Delinquency Status.
- **Table**: Sum of Loan Amount by Home Ownership.
- **Donut Chart**: Average Remaining Principal by Verification Status.
- **Bar Chart**: Sum of Delinquencies by Home Ownership.
- **Treemap**: Max Remaining Installments by Employment Length.
- **Line Chart**: Total Amount Paid & Funded Amount Over Time.
- **Slicer**: Loan Purpose.

---

## Conclusion
This project empowers banking institutions by providing actionable insights into borrower behavior and loan characteristics, optimizing strategies to enhance credit risk management and overall portfolio performance.
