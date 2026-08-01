# 📊 Student Performance Factors — Power BI Dashboard

An end-to-end Power BI project analyzing **6,607 student records** to identify which factors most strongly influence exam performance — covering study habits, attendance, family background, and behavioral factors.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/status-complete-brightgreen)

---

## 🎯 Project Objective

To analyze a student performance dataset and build an interactive Power BI dashboard that answers:
> **"Which factors have the biggest impact on a student's exam score?"**

---

## 🗂️ Dataset Overview

| Detail | Value |
|---|---|
| Total Records | 6,607 students |
| Total Columns | 21 |
| Source | Student Performance Factors dataset |

**Key columns include:**
- **Academic:** Hours_Studied, Attendance, Previous_Scores, Tutoring_Sessions, Exam_Score
- **Behavioral:** Sleep_Hours, Physical_Activity, Motivation_Level, Extracurricular_Activities, Peer_Influence
- **Background:** Parental_Involvement, Parental_Education_Level, Family_Income, Access_to_Resources, Distance_from_Home, School_Type, Teacher_Quality, Internet_Access, Learning_Disabilities, Gender

---

## 🧹 Data Cleaning (Power Query)

- Identified and handled **235 missing values** (~3.5% of data) stored as literal `"NA"` text across 3 columns: `Teacher_Quality`, `Parental_Education_Level`, `Distance_from_Home`
- Replaced `"NA"` text values with proper nulls / "Unknown" category
- Verified **zero duplicate Student IDs** and **zero duplicate rows**
- Checked numeric ranges for outliers (Exam_Score, Hours_Studied) and validated categorical value consistency
- Applied `Text.Trim()` for safety on all text columns
- Created calculated columns:
  - `Score_Category` — buckets Exam_Score into Fail / Average / Good / Excellent
  - `Study_Hours_Group` — buckets Hours_Studied into ranges (0–5, 6–10, 11–15, 16+)

---

## 📈 Key Insight

Correlation analysis against Exam_Score revealed:

| Factor | Correlation with Exam_Score |
|---|---|
| **Attendance** | **0.57** (strongest driver) |
| **Hours_Studied** | 0.43 |
| Previous_Scores | 0.17 |
| Tutoring_Sessions | 0.15 |
| Physical_Activity | 0.03 |
| Sleep_Hours | ~0.00 |

**Conclusion:** A student's own effort — **attendance and study hours** — is the single biggest driver of exam performance, far outweighing background/demographic factors like family income, parental education, or school type (which show only a 1–2 point average score difference between groups).

---

## 📑 Dashboard Pages

1. **Overview** — KPI summary cards (Total Students, Avg Exam Score, Avg Attendance, Avg Hours Studied), gender distribution, exam score distribution
2. **Study Habits Impact** — Hours Studied, Sleep Hours, and Tutoring Sessions vs Exam Score
3. **Background Factors** — Parental Involvement, Family Income, Parental Education, Distance from Home
4. **Behavioral Factors** — Extracurricular Activities, Learning Disabilities, Attendance, Motivation Level
5. **Deep Dive** — Decomposition tree and Key Influencers AI visual for automated root-cause analysis

---

## 🛠️ Tools Used

- **Power BI Desktop** — data modeling, DAX, visualization
- **Power Query** — data cleaning and transformation
- **DAX** — calculated columns and measures

---

## 📌 Key DAX Measures

```DAX
Avg Exam Score = AVERAGE(DataSet[Exam_Score])
Total Students = COUNTROWS(DataSet)
Avg Study Hours = AVERAGE(DataSet[Hours_Studied])
Avg Attendance % = AVERAGE(DataSet[Attendance])
Top Performers (%) = 
    DIVIDE(
        CALCULATE(COUNTROWS(DataSet), DataSet[Exam_Score] >= 80),
        [Total Students]
    )
```

---

## 📁 Repository Structure

```
├── DataSet.xlsx                  # Raw dataset
├── StudentPerformance.pbix       # Power BI project file
├── Screenshots/                  # Dashboard page screenshots
│   ├── Overview.png
│   ├── Study_Habits_Impact.png
│   ├── Background_Factors.png
│   ├── Behavioral_Factors.png
│   └── Deep_Dive.png
└── README.md
```

---

## 🚀 How to Use

1. Clone/download this repository
2. Open `StudentPerformance.pbix` in **Power BI Desktop**
3. Explore the dashboard using the navigation buttons across the top of each page

---

## 👤 Author

**Afaq** — Data Analytics enthusiast, transitioning career focus into Excel & Power BI.
Connect on [LinkedIn](www.linkedin.com/in/iamafaqali).

---

## 📝 License

This project is for portfolio and educational purposes.
