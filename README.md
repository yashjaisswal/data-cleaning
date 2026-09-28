# Amazon Electronics Data Cleaning

A data-cleaning and preprocessing project based on a scraped Amazon electronics products dataset. The notebook focuses on converting messy raw product information into a structured dataset suitable for further analysis and machine learning.

## Project Overview

The original dataset contains **42,675 Amazon product records** and **16 raw columns**. The data includes product ratings, review counts, prices, recent purchases, sponsorship information, coupon information, Buy Box availability, delivery details, sustainability badges, URLs, and collection dates.

The main goal of this project is to:

* Inspect the raw dataset
* Identify missing and inconsistent values
* Clean numerical and categorical columns
* Convert text-based values into usable numeric/date formats
* Handle messy price and purchase-count formats
* Remove columns that are not required for the cleaned dataset
* Export the processed data as `amazon\\\_cleaned.csv`

## Dataset

### Original dataset

* Rows: **42,675**
* Columns: **16**

Important raw columns include:

|Column|Description|
|-|-|
|`title`|Amazon product title|
|`rating`|Product rating|
|`number\\\_of\\\_reviews`|Number of customer reviews|
|`bought\\\_in\\\_last\\\_month`|Approximate number of units purchased recently|
|`current/discounted\\\_price`|Current discounted product price|
|`price\\\_on\\\_variant`|Price information associated with a product variant|
|`listed\\\_price`|Listed/original product price|
|`is\\\_best\\\_seller`|Best Seller badge information|
|`is\\\_sponsored`|Sponsored/organic product information|
|`is\\\_couponed`|Coupon information|
|`buy\\\_box\\\_availability`|Whether the Buy Box/Add to Cart option is available|
|`delivery\\\_details`|Delivery information|
|`sustainability\\\_badges`|Sustainability-related information|
|`image\\\_url`|Product image URL|
|`product\\\_url`|Product page URL|
|`collected\\\_at`|Date/time when the data was collected|

## Data Cleaning Performed

### 1\. Rating cleaning

The `rating` column initially contained text values.

Steps performed:

* Extracted the numeric rating from the text
* Converted the column to `float`
* Replaced zero values with missing values
* Filled missing ratings using the mean
* Converted the final column to `float32`

### 2\. Review-count cleaning

`number\\\_of\\\_reviews` contained values with commas.

Example:

```text
12,345
```

was converted into:

```text
12345
```

The column was then converted to numeric format and missing values were filled using the mean.

### 3\. Recent purchase cleaning

The `bought\\\_in\\\_last\\\_month` column contained values such as:

```text
1K
5K
10K
```

A custom conversion function was created to convert `K` values into numbers.

For example:

```text
5K → 5000
```

### 4\. Price cleaning

Several price columns contained:

* `$` symbols
* commas
* missing values
* non-numeric text
* `"No Discount"`
* coupon-related text

These values were cleaned and converted into numeric representations.

The following price-related columns were processed:


### 6\. Best Seller information
The `is\\\_best\\\_seller` column contained values such as:

* `No Badge`
* other text such as promotional information

The notebook converts the Best Seller indicator and removes the column later when it is no longer required.


Missing values in `buy\\\_box\\\_availability` were treated as unavailable.

The values were converted into a binary representation:

Add to cart → 1
Missing → 0
```

The final column was converted to integer type.


The `collected\\\_at` column was cleaned and converted to a pandas datetime column.

```python
df\\\['collected\\\_at'] = pd.to\\\_datetime(df\\\['collected\\\_at'])

### 9\. Text cleaning

The `title` column was cleaned by:

* Removing leading/trailing whitespace
* Fixing some incorrectly encoded characters
* Checking for duplicate product titles
### 10\. Removing unnecessary columns

The notebook removes columns that were not required for the final cleaned dataset, including:

* `delivery\\\_details`
* `sustainability\\\_badges`
* `product\\\_url`
* `is\\\_best\\\_seller`
* `is\\\_couponed`

## Final Dataset

The final dataset contains:

* **42,675 rows**
* **10 columns**
Final columns:

|Column|Type|
|-|-|
|`title`|string|
|`rating`|float32|
|`number\\\_of\\\_reviews`|float|
|`bought\\\_in\\\_last\\\_month`|float|
|`current\\\_price`|float|
|`price\\\_on\\\_variant`|float|
|`listed\\\_price`|object|
|`is\\\_sponsored`|string|
|`buy\\\_box\\\_availability`|int|
|`collected\\\_at`|datetime|

The cleaned dataset is exported using:

```python
df.to\\\_csv('amazon\\\_cleaned.csv', index=False)
```

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

## Project Structure

```text
amazon-data-cleaning/
│
├── amazon\\\_data\\\_cln (1).ipynb
├── amazon.csv
├── amazon\\\_cleaned.csv
└── README.md
```

## How to Run

### 1\. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2\. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3\. Open the notebook

```bash
jupyter notebook
```

Then open:

```text
amazon\\\_data\\\_cln (1).ipynb
```

### 4\. Run the notebook

Make sure `amazon.csv` is available in the same directory as the notebook.

Running the notebook will perform the cleaning operations and generate:

```text
amazon\\\_cleaned.csv
```

## Key Learning Outcomes

This project demonstrates practical experience with:

* Data inspection
* Missing-value analysis
* String manipulation
* Type conversion
* Numeric data cleaning
* Date parsing
* Feature/column cleanup
* Handling inconsistent scraped data
* Custom data-conversion functions
* Pandas indexing and conditional updates
* Exporting cleaned datasets to CSV

## Important Note

This notebook is primarily a **data cleaning and preprocessing project**. It does not represent a complete machine-learning project or a full exploratory data analysis pipeline. The cleaned dataset can be used as the starting point for EDA, visualization, statistical analysis, recommendation systems, or machine-learning experiments.


* `image\\\_url`

```
### 8\. Date conversion
```text
### 7\. Buy Box availability
* `Best Seller`

The notebook identifies rows containing coupon-related text and moves the relevant information into the coupon field before cleaning the price column.
### 5\. Coupon-related data


Some coupon information was mixed into the `price\\\_on\\\_variant` column.
* `listed\\\_price`

* `current/discounted\\\_price` → renamed to `current\\\_price`













 
