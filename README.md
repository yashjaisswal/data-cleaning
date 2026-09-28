# Amazon Electronics Data Cleaning

A practical data-cleaning and preprocessing project based on a scraped Amazon electronics products dataset. The project focuses on transforming messy raw product data into a structured and analysis-ready format using Python and Pandas.

---

## 📌 Project Overview

The original dataset contains **42,675 Amazon product records** and **16 raw columns**.

The dataset contains information related to:

- Product ratings
- Number of reviews
- Product prices
- Recent purchases
- Sponsored products
- Coupons
- Buy Box availability
- Delivery information
- Sustainability badges
- Product URLs
- Collection dates

### Objectives

The main objectives of this project are:

- Inspect the raw dataset
- Identify missing and inconsistent values
- Clean numerical and categorical columns
- Convert text-based values into appropriate data types
- Clean price and purchase-related information
- Handle missing values
- Remove unnecessary columns
- Prepare the dataset for further analysis and machine learning

---

## 📊 Dataset

### Original Dataset

| Property | Value |
|---|---:|
| Rows | 42,675 |
| Columns | 16 |

### Important Columns

| Column | Description |
|---|---|
| `title` | Amazon product title |
| `rating` | Product rating |
| `number_of_reviews` | Number of customer reviews |
| `bought_in_last_month` | Approximate number of recent purchases |
| `current/discounted_price` | Current discounted product price |
| `price_on_variant` | Price associated with a product variant |
| `listed_price` | Original/listed product price |
| `is_best_seller` | Best Seller badge information |
| `is_sponsored` | Sponsored/organic product information |
| `is_couponed` | Coupon information |
| `buy_box_availability` | Buy Box/Add to Cart availability |
| `delivery_details` | Delivery information |
| `sustainability_badges` | Sustainability-related information |
| `image_url` | Product image URL |
| `product_url` | Product page URL |
| `collected_at` | Date and time of data collection |

---

## 🧹 Data Cleaning Process

### 1. Rating Cleaning

The `rating` column initially contained text values.

The following operations were performed:

- Extracted numeric ratings
- Converted the column to `float`
- Replaced zero values with missing values
- Filled missing ratings using the mean
- Converted the final column to `float32`

---

### 2. Review Count Cleaning

The `number_of_reviews` column contained comma-separated values.
