# iPhone-Project
This project focuses on analyzing an iPhone product dataset using Python to understand product pricing, discounts, customer ratings, reviews, storage configurations, colors, and iPhone model performance.  The analysis was performed using NumPy, Pandas, Matplotlib, and Seaborn to clean the data.

The main objective of this project is to understand **which iPhone models perform better, how pricing and discounts vary, and how customer engagement differs across products**.

---

## 2. Project Description

The dataset contains information about different iPhone models, including:

* Product Name
* MRP
* Sale Price
* RAM / Storage Configuration
* Star Rating
* Number of Ratings
* Number of Reviews
* Product Color

### Key Tasks Performed

1. Cleaned and standardized column names.
2. Handled missing values in the Star Rating column.
3. Filled missing ratings using overall and RAM-wise average ratings.
4. Calculated discount percentage for each product.
5. Identified the iPhone model with the highest discount.
6. Analyzed the number of models available for each storage configuration.
7. Extracted product colors from product names.
8. Analyzed the number of models for each iPhone version.
9. Identified the top 5 models based on number of reviews.
10. Calculated the difference between the highest and lowest MRP.
11. Compared total reviews for iPhone 11 and iPhone 12.
12. Identified the iPhone with the 3rd highest MRP.
13. Calculated the average MRP of iPhones priced above ₹100,000.
14. Analyzed the Ratings-to-Reviews ratio for 128 GB iPhones.

---

## 3. Tools & Technologies

### Programming Language

* Python

### Libraries

* Pandas
* NumPy

### Skills Demonstrated

* Data Cleaning
* Data Preprocessing
* Exploratory Data Analysis (EDA)
* Missing Value Treatment
* Feature Engineering
* Data Aggregation
* Data Filtering
* String Manipulation
* Statistical Analysis
* Data Visualization
* Business Insights Generation

---

## 4. Data Cleaning & Preparation

The first step was to clean and prepare the dataset for analysis.

### Column Name Standardization

Spaces in column names were replaced with underscores to make them easier to work with in Python.

```python
df.columns = df.columns.str.replace(' ', '_', regex=False)
```

### Missing Value Treatment

Missing Star Ratings were identified and handled using average ratings.

For a more accurate approach, missing ratings were also filled using the average rating within the corresponding RAM/storage group.

```python
df['Star_Rating'] = df['Star_Rating'].fillna(
    df.groupby('RAM')['Star_Rating'].transform('mean')
)
```

This approach preserves differences in customer ratings across different storage configurations.

---

## 5. Feature Engineering

A new feature called `Discount_Percentage` was created to understand the discount offered on each product.

```python
df['Discount_Percentage'] = (
    (df['MRP'] - df['Sale_Price']) / df['MRP']
) * 100
```

This metric helps compare discounts across products regardless of their original price.

Another derived metric, `Ratings_to_Reviews`, was created to understand the relationship between customer ratings and reviews.

```python
df['Ratings_to_Reviews'] = (
    df['Number_Of_Ratings'] /
    df['Number_Of_Reviews']
)
```

---

## 6. Exploratory Data Analysis

The analysis focused on the following business questions:

### Pricing Analysis

* Which iPhone has the highest MRP?
* Which iPhone has the lowest MRP?
* What is the price difference between the highest and lowest priced models?
* What is the average MRP of iPhones priced above ₹100,000?

### Discount Analysis

* Which model offers the highest discount?
* How does the discount percentage vary across products?

### Product Configuration Analysis

* How many models are available for each storage configuration?
* Which storage configuration has the highest number of models?

### Customer Engagement Analysis

* Which models have the highest number of reviews?
* Which iPhone versions receive more customer engagement?
* What is the Ratings-to-Reviews ratio?

### Model Analysis

* How many models exist for each iPhone version?
* What are the most common iPhone versions in the dataset?

---

## 7. Business Insights

### 💰 Pricing Insights

The analysis helps identify the premium and budget segments of the iPhone product range.

High-MRP products indicate the presence of a premium segment, while lower-MRP models provide relatively affordable options for price-sensitive customers.

The price gap between the highest and lowest MRP highlights the wide pricing range within the product portfolio.

---

### 🏷️ Discount Insights

The discount analysis identifies products receiving the highest percentage discounts.

A higher discount can potentially increase customer interest and improve sales conversion, especially for older models.

Discount percentage is more useful than absolute discount because it allows fair comparison between expensive and relatively cheaper products.

---

### ⭐ Rating Insights

Missing ratings were handled using RAM-wise average ratings.

This approach is more meaningful than using a single overall average because customer ratings can vary across different product configurations.

---

### 📦 Storage Configuration Insights

The analysis shows the distribution of products across different storage configurations such as:

* 64 GB
* 128 GB
* 256 GB
* 512 GB

This can help understand which storage configurations are most commonly offered in the dataset.

---

### 👥 Customer Engagement Insights

The top 5 products based on review count indicate which models have generated higher customer engagement.

A high number of reviews can indicate:

* Higher customer interest
* Higher product visibility
* Greater sales volume
* Longer market presence

However, review count should not be treated as a direct measure of product quality.

---

### 📱 iPhone Version Insights

The analysis groups products by iPhone version, such as:

* iPhone 8
* iPhone XR
* iPhone XS
* iPhone 11
* iPhone 12
* iPhone SE

This helps identify which generations have the highest representation in the dataset.

---

## 8. Key Business Questions Answered

| Business Question                                | Analysis                         |
| ------------------------------------------------ | -------------------------------- |
| Which model has the highest discount?            | Discount percentage analysis     |
| Which storage configuration has the most models? | `value_counts()`                 |
| Which color is most common?                      | Color extraction + aggregation   |
| Which iPhone version has the most models?        | Version extraction + aggregation |
| Which models have the most reviews?              | Sorting by review count          |
| What is the price range?                         | Maximum MRP − Minimum MRP        |
| How do iPhone 11 and 12 compare?                 | Total review comparison          |
| Which iPhone has the 3rd highest MRP?            | Sorting + `iloc`                 |
| What is the average MRP above ₹100K?             | Filtering + `mean()`             |
| Which 128 GB iPhone has the highest ratio?       | Ratio + `idxmax()`               |

---

## 9. Conclusion

This project demonstrates how Python can be used to transform raw product data into meaningful business insights.

The analysis covered the complete data analytics workflow, including **data cleaning, missing value treatment, feature engineering, exploratory data analysis, aggregation, filtering, and business insight generation**.

The findings provide a better understanding of **iPhone pricing, discounts, storage configurations, customer engagement, ratings, reviews, and model-level performance**.

Overall, this project demonstrates practical Data Analyst skills using **Python, Pandas, NumPy **, and shows how data-driven analysis can support product and business decision-making.

---


