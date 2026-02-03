# 🎵 Spotify End-to-End Data Analysis & Skip Prediction Project

![Python](https://img.shields.io/badge/Python-3.9-blue?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine%20Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Power BI](https://img.shields.io/badge/Power_BI-Dashboard-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)

![Dashboard Preview](Dashboard.png)
*(Snapshot of the Final Power BI Dashboard)*

## 📌 Project Overview
This project is a comprehensive **End-to-End Data Science** analysis of my personal Spotify streaming history, covering over **140,000 streaming records**. 

The goal was not just to visualize "Top Artists," but to understand the **behavioral psychology** behind my listening habits and build a **Machine Learning model** to predict whether I will skip a track or not.

## 💼 Business Problem & Objectives
* **Behavioral Analysis:** Determine "When" and "How" I listen to music (Time of day, Platform, Context).
* **Skip Logic:** Define what constitutes a "Skip" (e.g., listening for less than 30 seconds vs. clicking the button).
* **Predictive Modeling:** Can we predict a skipped track before it finishes?
* **Interactive Reporting:** Build a centralized dashboard to monitor KPIs like `Skip Rate` and `Listening Hours`.

---

## ⚙️ The Pipeline (Methodology)

### 1. Data Cleaning & Preprocessing (Python/Pandas)
Raw data from Spotify (JSON/Excel) was processed to ensure data integrity:
* **Timestamp Conversion:** Converted `ts` strings to datetime objects.
* **Handling Nulls:** Imputed missing values in `reason_start` and `reason_end` with 'Unknown' to preserve data volume.
* **Logic Definition:** Created a robust `is_skipped` flag based on:
    * Explicit `skipped = True` flag.
    * **Logic Rule:** If `ms_played` < 30 seconds AND reason is not 'trackdone', count as skipped.

### 2. Feature Engineering
Created new features to enhance analysis and Model performance:
* `Time_Segments`: Extracted Hour, Day Name, and Month.
* `Session_Logic`: Identified listening sessions.
* `Platform_Simplification`: Grouped devices (Android, iOS, Web, etc.).

### 3. Machine Learning (Skip Prediction) 🤖
Built a **Random Forest Classifier** to predict user skips.
* **Target:** `is_skipped_clean`
* **Features Used:** `reason_start`, `artist_name`, `hour`, `day_name`, `shuffle_state`.
* **Model Performance:** Achieved **80% Accuracy** on the test set.
* **Key Insight:** Feature Importance analysis revealed that **`reason_start` (Context)** is the #1 predictor of a skip, outweighing the Artist Name. (i.e., *How* the song starts matters more than *Who* is singing).

### 4. Visualization (Power BI) 📊
Designed a dark-themed, Spotify-inspired dashboard focusing on User Experience (UX):
* **Matrix Heatmap:** Visualizes peak listening hours (Activity vs. Time of Day).
* **Drill-Down Line Chart:** Analyzes listening trends over Years and Months.
* **AI Insights:** Displays the Random Forest Feature Importance directly on the dashboard.
* **Dynamic Slicers:** Allows filtering by Artist, Platform, and Year.

---

## 📈 Key Insights Summary
1.  **The "Shuffle" Effect:** Auto-played songs (Shuffle/Radio) have a significantly higher skip rate compared to manually selected tracks (`clickrow`).
2.  **Platform Loyalty:** 96% of streaming occurs on **Android**, with a consistent skip rate of **36.8%**.
3.  **Night Owl:** The Heatmap reveals peak activity during late-night hours, indicating a preference for music during personal downtime.

---

## 📂 Project Structure
```text
├── Data_Cleaning_and_ML.ipynb   # The full Python Pipeline (ETL + ML Model)
├── Spotify_Dashboard.pbix       # The Interactive Power BI file
├── Dashboard.png                # Dashboard Screenshot
├── My_Spotify_Cleaned_Data.xlsx # Processed Dataset (Output)
└── README.md                    # Project Documentation

--

## 👤 Author
 Mohamed Elkomy - Data Analyst & Data Scientist [www.linkedin.com/in/mohamed-elkomy-me30] 

*Feel free to star ⭐ this repo if you find it helpful!*
