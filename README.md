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

The following operations were performed:

- Removed commas from review counts
- Converted the column to numeric format
- Handled missing values where required

---

### 3. Bought in Last Month Cleaning

The `bought_in_last_month` column contained values such as `1K`, `5K`, etc.

The following operations were performed:

- Removed the `K` suffix
- Converted values into numeric format
- Converted the column to `float`
- Handled missing values

---

### 4. Price Cleaning

Several price-related columns contained currency symbols, commas, text, and missing values.

The following operations were performed:

- Removed currency symbols such as `₹`
- Removed commas from price values
- Extracted numeric price values
- Converted price columns to numeric format
- Handled missing values

Price-related columns included:

- `current_price`
- `price_on_variant`
- `listed_price`

---

### 5. Coupon Cleaning

The `is_couponed` column contained coupon-related text information.

The following operations were performed:

- Identified whether a product had a coupon
- Converted the information into a suitable format
- Handled missing values

---

### 6. Best Seller Cleaning

The `is_best_seller` column contained information about whether a product was marked as a Best Seller.

The values were cleaned and converted into a suitable format for analysis.

---

### 7. Buy Box Availability Cleaning

The `buy_box_availability` column contained information about product availability.

The following operations were performed:

- Converted availability information into a binary representation
- `1` represents availability
- `0` represents unavailability

---

### 8. Sponsored Product Cleaning

The `is_sponsored` column was cleaned to identify whether a product was sponsored.

The values were converted into a suitable binary format for analysis.

---

### 9. Date and Time Cleaning

The `collected_at` column contained date and time information.

The following operations were performed:

- Converted the column to datetime format
- Ensured consistent date and time representation
- Handled invalid or missing datetime values

---

### 10. Title Cleaning

The `title` column contained product names with unnecessary text and formatting.

The following operations were performed:

- Cleaned unnecessary characters
- Removed unwanted text where required
- Standardized product title values
- Handled missing titles

---

### 11. Removing Unnecessary Columns

Columns that were not required for the final analysis were removed.

The final dataset retained the following columns:

- `title`
- `rating`
- `number_of_reviews`
- `bought_in_last_month`
- `current_price`
- `price_on_variant`
- `listed_price`
- `is_sponsored`
- `buy_box_availability`
- `collected_at`
