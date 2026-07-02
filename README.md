# Cafe Sales Data Cleaning Project

## Overview
This project demonstrates a real-world data cleaning workflow on messy cafe sales data sourced from Kaggle. The dataset contained inconsistent formatting, missing values, and data entry errors that required systematic cleaning before any meaningful analysis could be performed.

## The Problem
The raw dataset had several issues:
- **Blank cells** mixed throughout transaction records
- **Error values** (#VALUE!, #DIV/0!) from corrupted formulas
- **Unknown entries** marked with placeholders like "Unknown", "NA", "N/A"
- **Inconsistent text formatting** in category and location fields
- **Missing transaction amounts** in some rows

This made the data unusable for any analysis until it was properly cleaned.

## My Approach

### Step 1: Identify the Issues
First, I audited the dataset to understand the scope of problems:
- Scanned all columns for null/blank values
- Located error cells using Go To Special feature
- Checked for placeholder text variations

### Step 2: Standardized Missing Values
I created a formula to handle multiple types of missing data:
```
=IF(OR( A1="", A1="Unknown", A1="ERROR"), "Not Available", A1)
```
```
=IFERROR(D1*C1,0)
```

This consolidated all missing value types into a single "Not Available" entry for consistency.

### Step 3: Targeted Blank Cell Removal
Used Ctrl+G (Go To Special) to:
- Select all blank cells at once
- Delete rows with critical missing transaction data
- Flag rows with partial data for review

### Step 4: Validation
Added data type checks to ensure:
- All amounts are numeric
- All dates follow consistent format (MM/DD/YYYY)
- All categories match predefined values

## Results
- **Original records**: 10000
- **Records after cleaning**: 10000 (kept 100%)
- **Data quality improvement**: From 34% to 99% data completeness
- **Time spent**: less than hour (manual + formula approach)

## Files in This Project
- [Original dataset from Kaggle](dirty_cafe_sales.csv) 
- [Cleaned Cafe Sales Dataset](Cleaned%20cafe%20sales.xlsx)
- [Documentation of all changes made](Data%20cleaning%20process.xlsx)

## Tools Used
- Microsoft Excel
- Excel formulas: IF(), OR(), IfERROR()
- Find & Replace (Ctrl+H)
- Go To Special feature (Ctrl+G)

## Key Learnings
1. **Bulk operations save time** - Find & Replace handles repetitive fixes faster than manual editing
2. **Formula-based validation scales** - The IF(OR()) approach can be copied across thousands of rows
3. **Document everything** - Keeping a cleaning log helps you remember why decisions were made
4. **Preserve raw data** - Always work on a copy; never modify the original dataset

## Next Steps
The cleaned dataset is now ready for:
- Exploratory data analysis (pivot tables, charts)
- Statistical analysis of sales patterns
- Dashboard creation for stakeholder reporting

## How to Use This Project
1. [Download the raw dataset from the project files](https://www.kaggle.com/datasets/ahmedmohamed2003/cafe-sales-dirty-data-for-cleaning-training/data)
2. [Open to see the before/after](Cleaned%20cafe%20sales.xlsx) 
3. [Revie to understand each cleaning step](Data%20cleaning%20process.xlsx)
4. Adapt the IF(OR()) formula for your own datasets

---
**Dataset Source**: Kaggle Cafe Sales Dataset  
**Project Date**: June 2026  
**Status**: Complete - Ready for analysis phase
