# 🎵 Spotify End-to-End Data Analysis & Skip Prediction Project

![Python](https://img.shields.io/badge/Python-3.9-blue?style=for-the-badge\&logo=python\&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge\&logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine%20Learning-F7931E?style=for-the-badge\&logo=scikit-learn)
![Power BI](https://img.shields.io/badge/Power_BI-Dashboard-F2C811?style=for-the-badge\&logo=power-bi\&logoColor=black)

![Dashboard Preview](Dashboard.png)
*Snapshot of the Final **Interactive** Power BI Dashboard*

---

## 📌 Project Overview

This project is a complete **End-to-End Data Science Project** analyzing my personal Spotify streaming history, covering more than **140,000 listening events**.

The objective goes beyond basic descriptive analytics (e.g., *Top Artists*). The project focuses on understanding **user listening behavior**, identifying **skip patterns**, and building a **Machine Learning model** capable of predicting whether a track will be skipped **at the start of playback**.

---

## 💼 Business Problem & Objectives

* **Behavioral Analysis:** Identify *when*, *how*, and *on which platforms* music is consumed.
* **Skip Definition:** Establish a clear and consistent definition of what constitutes a skip.
* **Predictive Modeling:** Predict the probability of a track being skipped using contextual and behavioral features.
* **Decision Support:** Deliver insights through an interactive dashboard to support data-driven decisions.

**Business Value:**

> The insights from this project can be used to optimize playlist sequencing, improve recommendation systems, and reduce user churn by minimizing skip probability.

---

## ⚙️ Project Pipeline (Methodology)

### 1. Data Cleaning & Preprocessing (Python / Pandas)

Raw Spotify streaming data (JSON / Excel) was cleaned and standardized:

* Converted `ts` to datetime format.
* Handled missing values in `reason_start` and `reason_end` by imputing `'Unknown'` to preserve data volume.
* Defined a robust `is_skipped_clean` flag based on:

  * Explicit `skipped = True` values.
  * **Logical Rule:** If `ms_played < 30,000 ms` and `reason_end != 'trackdone'`, the track is classified as skipped.

---

### 2. Feature Engineering

New features were engineered to enhance both analysis and model performance:

* **Time Features:** Hour of day, day name, and month.
* **Session Logic:** Identification of continuous listening sessions.
* **Platform Simplification:** Grouped platforms into high-level categories (Android, iOS, Web, Desktop).
* **Artist Handling:** Limited artist-related features to the most frequent artists to reduce dimensionality and noise.

---

### 3. Machine Learning – Skip Prediction 🤖

A **Random Forest Classifier** was trained to predict whether a track will be skipped.

* **Target Variable:** `is_skipped_clean`
* **Features Used:**

  * `reason_start` (contextual trigger)
  * `hour`
  * `day_name`
  * `shuffle_state`
  * `artist_name` (frequency-filtered)

> **Model Design Note:** The model is designed as a **near-real-time prediction system**, where contextual features such as `reason_start` are available at the beginning of track playback.

#### 📊 Model Evaluation

Due to class imbalance in skip behavior, performance was evaluated using multiple metrics:

* Accuracy: **80%**
* Precision / Recall / F1-score
* Confusion Matrix

A baseline **Logistic Regression** model was tested for comparison, with the Random Forest model achieving superior performance, particularly in F1-score.

#### 🔍 Key ML Insight

> **Context matters more than the artist.**
> Feature importance analysis revealed that `reason_start` is the strongest predictor of skips, outweighing the artist name. This indicates that *how* a song starts is more important than *who* performs it.

---

### 4. Data Visualization (Power BI) 📊

A dark-themed, Spotify-inspired Power BI dashboard was developed with a strong focus on usability and storytelling:

* **Activity Heatmap:** Listening intensity by hour and day.
* **Time-Series Drill-Down:** Listening trends across years and months.
* **Model Insights:** Random Forest feature importance integrated directly into the dashboard.
* **Dynamic Filters:** Artist, platform, and year slicers for interactive exploration.

---

## 📈 Key Insights Summary

1. **The Shuffle Effect:** Auto-played tracks (Shuffle / Radio) show a significantly higher skip rate compared to manually selected tracks (`clickrow`).
2. **Platform Dominance:** Approximately **96%** of listening occurs on Android, with a consistent skip rate of **36.8%**.
3. **Night Owl Behavior:** Peak listening activity occurs during late-night hours, indicating music consumption during personal downtime.

---

## 📂 Project Structure

```text
├── Data_Cleaning_and_ML.ipynb   # Full Python pipeline (ETL + Feature Engineering + ML)
├── Spotify_Dashboard.pbix       # Interactive Power BI dashboard
├── Dashboard.png                # Dashboard preview image
├── My_Spotify_Cleaned_Data.xlsx # Final cleaned dataset
└── README.md                    # Project documentation
```

---

## 👤 Author

**Mohamed Elkomy**
Data Analyst & Data Scientist
🔗 LinkedIn: [https://www.linkedin.com/in/mohamed-elkomy-me30](https://www.linkedin.com/in/mohamed-elkomy-me30)

---

⭐ *If you find this project useful or insightful, feel free to star the repository!*
