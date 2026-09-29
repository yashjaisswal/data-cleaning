# Surat Real Estate Data Cleaning

## Project Overview

This project focuses on cleaning and preprocessing a real-estate dataset containing property listings from Surat.

The raw dataset contains inconsistent values, mixed units, incorrect entries, missing values, and information stored in the wrong columns.

The objective of this project is to clean the dataset and convert it into a structured format suitable for further analysis.

---

## Dataset

The original dataset contains **4,525 records and 11 columns**.

The original columns are:

- `property_name`
- `areaWithType`
- `square_feet`
- `transaction`
- `status`
- `floor`
- `furnishing`
- `facing`
- `description`
- `price_per_sqft`
- `price`

---

## Data Cleaning Process

### 1. Standardizing Column Names

The column names were converted to lowercase to maintain consistency.

For example:

```text
areaWithType → areawithtype
