# 🏠 Airbnb Booking Analysis

##  Overview

This project performs an Exploratory Data Analysis (EDA) on Airbnb listing data to uncover patterns in pricing, room availability, neighborhood popularity, and customer review trends. Using Python and data visualization libraries, the project transforms raw Airbnb data into meaningful insights that can support decision-making for hosts, travelers, and investors.

---

##  Problem Statement

The Airbnb marketplace contains thousands of listings with varying prices, room types, and locations. Without proper analysis, it becomes difficult to understand:

- How listing prices are distributed.
- Which room types are most common.
- Which neighborhoods have the highest number of listings.
- How prices vary across room types.
- How customer review activity changes over time.

This project addresses these challenges through data cleaning, preprocessing, and visualization techniques.

---

##  Objectives

The main objectives of this project are:

- Clean and preprocess the Airbnb dataset.
- Handle missing and inconsistent data.
- Convert monetary values into numerical formats.
- Analyze listing price distributions.
- Examine room type popularity.
- Identify neighborhoods with the highest concentration of listings.
- Compare pricing across room categories.
- Explore review trends over time.
- Generate actionable business insights.

---

##  Dataset

### Dataset Used

**Airbnb Open Data**

The dataset contains information such as:

- Listing Name
- Host Name
- Neighborhood Group
- Room Type
- Price
- Service Fee
- Number of Reviews
- Reviews Per Month
- Availability
- Last Review Date

---

## 🛠 Technologies Used

| Technology | Purpose |
|------------|----------|
| Python | Data Analysis |
| Pandas | Data Cleaning & Manipulation |
| Matplotlib | Data Visualization |
| Seaborn | Statistical Visualization |
| Jupyter Notebook | Development Environment |

---

##  Methodology

### Step 1: Data Loading

The dataset is loaded into a Pandas DataFrame.

```python
df = pd.read_csv("Airbnb_Open_Data.csv")
```

Purpose:
- Import structured data for analysis.
- Create a DataFrame for manipulation and visualization.

---

### Step 2: Data Inspection

Initial exploration was performed using:

```python
df.head()
df.columns
df.isnull().sum()
```

Purpose:
- Understand dataset structure.
- Identify missing values.
- Verify column names and data types.

---

### Step 3: Data Cleaning

#### Handling Date Values

The `last review` column was converted to datetime format:

```python
df['last review'] = pd.to_datetime(df['last review'], errors='coerce')
```

Benefits:
- Enables time-series analysis.
- Handles invalid date formats safely.

---

#### Handling Missing Values

Missing values were replaced using:

```python
df.fillna({
    'reviews per month': 0,
    'last review': df['last review'].min()
}, inplace=True)
```

Benefits:
- Missing review counts become zero.
- Missing review dates are assigned the earliest valid date.

---

#### Removing Incomplete Records

Records missing essential information were removed:

```python
df.dropna(subset=['name', 'host name'], inplace=True)
```

Benefits:
- Improves dataset quality.
- Removes records with insufficient information.

---

#### Cleaning Monetary Data

Price and Service Fee columns contained symbols such as:

```text
$1,200
```

These were converted into numerical values:

```python
df['price'] = df['price'].replace(r'[$,]', '', regex=True).astype(float)
df['service fee'] = df['service fee'].replace(r'[$,]', '', regex=True).astype(float)
```

Benefits:
- Allows numerical calculations.
- Enables statistical analysis and visualization.

---

#### Removing Duplicates

```python
df.drop_duplicates(inplace=True)
```

Benefits:
- Prevents duplicate records from affecting analysis results.

---

## 📈 Exploratory Data Analysis

### 1. Distribution of Listing Prices

#### Visualization

Histogram with Kernel Density Estimate (KDE)

```python
sns.histplot(df['price'], bins=50, kde=True)
```

#### Purpose

- Understand price distribution.
- Identify outliers.
- Observe market pricing trends.

#### Business Value

Hosts can compare their pricing with the broader market.

---

### 2. Room Type Distribution

#### Visualization

Count Plot

```python
sns.countplot(x='room type', data=df)
```

#### Purpose

- Identify the most common accommodation type.
- Understand listing supply distribution.

#### Business Value

Provides insights into customer preferences and market demand.

---

### 3. Listings by Neighborhood Group

#### Visualization

Horizontal Count Plot

```python
sns.countplot(y='neighbourhood group', data=df)
```

#### Purpose

- Identify areas with the highest listing density.
- Understand geographical concentration of listings.

#### Business Value

Highlights neighborhoods with strong tourism and rental activity.

---

### 4. Price Comparison by Room Type

#### Visualization

Box Plot

```python
sns.boxplot(x='room type', y='price', data=df)
```

#### Purpose

- Compare price distributions across room categories.
- Identify pricing trends and outliers.

#### Business Value

Helps hosts determine competitive pricing strategies.

---

### 5. Review Trends Over Time

#### Visualization

Line Chart

```python
reviews_over_time.plot(kind='line')
```

#### Purpose

- Analyze customer engagement trends.
- Observe review activity over time.

#### Business Value

Provides insights into market growth and seasonal demand patterns.

---

## 📊 Key Findings

### Price Distribution

- Most Airbnb listings fall within a moderate price range.
- A smaller number of luxury properties contribute to higher-priced outliers.

### Room Types

- Private Rooms and Entire Homes represent the majority of listings.
- Shared Rooms typically form the smallest category.

### Neighborhood Popularity

- Certain neighborhoods contain significantly more listings than others.
- These areas often indicate higher tourism demand and investment potential.

### Price Differences

- Entire Homes generally command higher prices.
- Shared Rooms tend to be the most affordable option.

### Customer Reviews

- Review activity varies over time.
- Trends may reflect seasonal tourism patterns and market growth.

---

## 💼 Business Impact

### For Airbnb Hosts

- Understand market pricing.
- Benchmark listings against competitors.
- Optimize pricing strategies.

### For Travelers

- Gain realistic pricing expectations.
- Identify accommodation options that fit their budget.

### For Investors

- Discover high-demand neighborhoods.
- Identify potential opportunities in the short-term rental market.

---

## ⚠ Challenges Encountered

### Missing Data

Several columns contained missing values that required cleaning and imputation.

### Inconsistent Formatting

Price-related columns contained currency symbols and commas that prevented numerical analysis.

### Date Conversion

Review dates required conversion to datetime format for trend analysis.

### Duplicate Records

Duplicate listings had to be removed to ensure accurate results.

---

## 🚀 Future Improvements

Potential enhancements include:

- Machine Learning-based price prediction.
- Interactive dashboards using Power BI or Tableau.
- Geographical mapping using Folium.
- Sentiment analysis on customer reviews.
- Seasonal demand forecasting.
- Recommendation systems for hosts and guests.

---

## 📁 Project Structure

```text
Airbnb-Booking-Analysis/
│
├── Airbnb_Open_Data.csv
├── File1.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

---

## ▶️ How to Run the Project

### Clone the Repository

```bash
git clone https://github.com/your-username/Airbnb-Booking-Analysis.git
```

### Install Dependencies

```bash
pip install pandas matplotlib seaborn
```

### Launch Jupyter Notebook

```bash
jupyter notebook
```

### Open

```text
File1.ipynb
```

Run all cells to reproduce the analysis.

---

##  Learning Outcomes

This project demonstrates practical applications of:

- Data Cleaning
- Data Preprocessing
- Exploratory Data Analysis (EDA)
- Data Visualization
- Time Series Analysis
- Business Intelligence
- Statistical Analysis
- Python for Data Analytics

---

##  Conclusion

This project demonstrates how Exploratory Data Analysis can transform raw Airbnb data into valuable business insights. By cleaning, processing, and visualizing listing information, the analysis reveals patterns in pricing, room type preferences, neighborhood popularity, and customer review activity.

The findings can help hosts optimize pricing, assist travelers in making informed booking decisions, and support investors in identifying attractive markets. Overall, the project showcases the power of data analytics in solving real-world business problems within the short-term rental industry.

---

### 👩‍💻 Author

**Priti Ranabhat**
