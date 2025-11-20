# Google Play Store Apps Data Analysis 📱
## Overview
This project is an exploratory data analysis (EDA) of the **Google Play Store Apps** dataset. The goal of this analysis is to discover trends in the Android app market, understand what makes an app successful, and identify user preferences regarding app categories, ratings, and pricing.

Using Python, I cleaned the raw data, handled missing values, performed statistical analysis, and created visualizations to answer specific business questions about the mobile app ecosystem.

## Table of Contents
* [Project Objectives](#project-objectives)
* [Dataset](#dataset)
* [Technologies Used](#technologies-used)
* [Data Cleaning & Preparation](#data-cleaning--preparation)
* [Key Analysis & Insights](#key-analysis--insights)
* [How to Run This Project](#how-to-run-this-project)
* [Conclusion](#conclusion)

## Project Objectives
1. Identify the most popular app categories.
2. Compare user ratings between Free and Paid apps.
3. Estimate revenue generation potential across different categories.
4. Analyze the relationship between the number of reviews and user ratings.
5. Determine which Android versions are most targeted by developers.
6. Perform text analysis on app names to find common keywords.

## Dataset
The dataset used is `googleplaystore.csv`. It contains details of approximately 10,000 Android applications.
* **Key Features:** App Name, Category, Rating, Reviews, Size, Installs, Type (Free/Paid), Price, Content Rating, Genres, Last Updated, and Android Version.

## Technologies Used
* **Python 3.x**
* **Pandas:** For data manipulation and cleaning.
* **NumPy:** For numerical operations.
* **Matplotlib & Seaborn:** For creating static and interactive data visualizations.

## Data Cleaning & Preparation
Real-world data is often messy. Before analyzing, I performed the following cleaning steps:

1.  **Handling Corrupted Data:** Identified and removed rows with shifted values (e.g., the row where "Installs" contained "Free").
2.  **Data Type Conversion & Standardization:**
    * Converted **Reviews** to integers.
    * Cleaned **Installs** (removed '+' and ',') and converted to integers.
    * Cleaned **Price** (removed '$') and converted to floats.
    * Converted **Last Updated** to datetime objects.
3.  **Size Standardization:** Converted app sizes from various formats (M for Megabytes, k for Kilobytes) into a standard numeric format (Bytes), handling "Varies with device" as missing data (NaN).
4.  **Missing Value Imputation:**
    * Filled missing **Ratings** with the median value (4.3).
    * Filled missing **Size** values with the median (12,000,000 bytes).
    * Filled categorical missing values (e.g., 'Type', 'Android Ver') with the mode (most frequent value).
5.  **Duplicate Removal:** Removed duplicate entries across the entire dataset and then removed duplicates based on the 'App' name, keeping the version with the highest **Reviews** count.

## Key Analysis & Insights

### 1. 📈 Category Performance & Popularity
* **Finding:** The **FAMILY** (1876 apps) and **GAME** (946 apps) categories have the highest number of apps.
* **Insight:** The market is saturated with entertainment and educational apps for families.

### 2. 💲 Monetization & Ratings
* **Finding:** Paid apps (mean rating: 4.270) have a slightly higher average rating compared to Free apps (mean rating: 4.186).
* **Insight:** Users who pay for apps may experience better quality (fewer ads, better support), leading to slightly higher satisfaction.

### 3. 🎯 Niche Market Success (Quadrant Analysis)
* **Finding:** Categories in the "Low Installs / High Rating" quadrant (Top Left) often serve specific needs.
* **Examples:** **EVENTS** (Average Rating: 4.395), **ART_AND_DESIGN** (4.357), and **EDUCATION** (4.351) are among these categories.
* **Insight:** These categories reflect high user satisfaction from a focused audience, indicating potential for niche app development that prioritizes quality over mass appeal.

### 4. 🗣️ User Feedback & Correlation
* **Correlation (Rating vs. Reviews):** The Pearson correlation is **0.0503**, indicating a very weak or negligible linear relationship.
* **Insight:** Apps with high review counts tend to stabilize around a rating of 4.0 to 4.5. This suggests that more feedback leads to a "regression to the mean" (a stable, generally good, but not perfect, score) rather than a continuously increasing rating.

### 5. 💻 Android Version Compatibility
* **Finding:** The highest median install count is found in apps labeled **"Varies with device"** (5,000,000 installs).
* **Insight:** Older, stable versions like **"4.1 and up"** and **"4.4 and up"** show higher median installs than the newest versions. This confirms that maximizing backward compatibility is a critical strategy for app success and reach.

## How to Run This Project
1.  Clone this repository.
2.  Ensure you have the required libraries installed:
    ```bash
    pip install pandas numpy matplotlib seaborn
    ```
3.  Place the `googleplaystore.csv` file in the same directory as the notebook.
4.  Open the Jupyter Notebook (`EDA_For_Playstore_DataSet.ipynb`) and run all cells.

## Conclusion
This analysis provides a comprehensive view of the Google Play Store. For developers, the data suggests that while Games are popular, "Niche" categories like Medical or Parenting offer high user satisfaction with less competition. Additionally, maintaining compatibility with older Android versions is crucial for maximizing downloads.
