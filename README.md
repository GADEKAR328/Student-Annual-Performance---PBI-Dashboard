<div align="center">

# 🏫 Student Annual Performance Dashboard

### Janseva Vidyalaya Wadzire, Maharashtra 414302

*Class 5 to 10 · Academic Performance Analytics · Power BI · By Yogesh Gadekar (YSG)*

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![DAX](https://img.shields.io/badge/DAX-15%20Formulas-1A3C5E?style=for-the-badge)](/)
[![Dataset](https://img.shields.io/badge/Dataset-720%20Rows-1A7A4A?style=for-the-badge)](/)
[![Classes](https://img.shields.io/badge/Classes-5%20to%2010-D4840A?style=for-the-badge)](/)
[![Maharashtra](https://img.shields.io/badge/Maharashtra-India-FF9933?style=for-the-badge)](/)

> A complete Power BI dashboard analyzing student academic performance across Class 5 to 10 covering 6 subjects, attendance, grades, toppers, and year-over-year improvement trends for Janseva Vidyalaya Wadzire.

</div>

---

## 📸 Dashboard Preview

<div align="center">

![Dashboard](https://raw.githubusercontent.com/GADEKAR328/Student-Annual-Performance---PBI-Dashboard/c6a9de048999b20a643692a7db5de606dd8cc012/Students%20Performance%20Analytics%20Dashboard%20.jpg)

</div>

---

## 🏫 About the School

<div align="center">

| New Building | Old Building |
|:---:|:---:|
| ![New Building](https://raw.githubusercontent.com/GADEKAR328/Student-Annual-Performance---PBI-Dashboard/6de248b91753abe09a0de19da212aa59a4bf37db/School%20Prayer%20-%20new%20building.jpg) | ![Old Building](https://raw.githubusercontent.com/GADEKAR328/Student-Annual-Performance---PBI-Dashboard/6de248b91753abe09a0de19da212aa59a4bf37db/Students%20Playground%20old%20building.jpg) |

**Janseva Vidyalaya Wadzire**
📍 Wadzire, Maharashtra 414302
🏫 Classes 5 to 10 · Divisions A & B
📅 Academic Years 2022-23 to 2024-25

</div>

---

## ⚡ Key KPIs

<div align="center">

| 👨‍🎓 Students | 📊 Avg % | ✅ Pass Rate | 📅 Attendance | 🏆 Toppers A+ | ❌ Fail Count |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **238** | **61.78%** | **93.75%** | **78.19%** | **60** | **45** |

</div>

---

## 📊 Dashboard Visuals

| Visual | Description |
|--------|-------------|
| 6 KPI Cards | Total Students, Avg Percentage, Pass Rate, Avg Attendance, Toppers A+, Fail Count |
| Avg Marks by Subject | Horizontal bar chart — Hindi leads at 62.2 |
| Grade Distribution | Donut chart — C grade highest at 23.19% |
| Avg Trend by Academic Year | Line chart — class-wise trend across 3 years |
| Pass Vs Fail by Class | Clustered bar chart |
| Top 10 Students | Table — Dinesh Shinde 96% leads |
| Attendance Band by Class | Stacked bar — Excellent, Good, Average, Poor |
| Class x Subject Avg Marks | Matrix heatmap — red to green color scale |
| 4 Slicers | Performance Band, Academic Year, Class, Division |
| Home Bookmark | Resets all filters in one click |

---

## 📁 Repository Structure

```
Student-Annual-Performance---PBI-Dashboard
├── Students Performance Analytics Dashboard.pbix
├── Students Performance Analytics Dashboard .jpg
├── School Prayer - new building.jpg
├── Students Playground old building.jpg
├── janseva_vidyalaya_performance.csv
├── School_Dashboard_YSG.pdf
└── README.md
```

---

## 🧪 Dataset Columns

| Column | Description |
|--------|-------------|
| Student_ID | Unique ID — JVW0001 format |
| Student_Name | Student full name |
| Gender | Male or Female |
| Class | 5 to 10 |
| Division | A or B |
| Academic_Year | 2022-23, 2023-24, 2024-25 |
| Marathi | Marks out of 100 |
| Hindi | Marks out of 100 |
| English | Marks out of 100 |
| Mathematics | Marks out of 100 |
| Science | Marks out of 100 |
| Social_Science | Marks out of 100 |
| Total_Marks | Sum of all 6 subjects |
| Percentage | Total divided by 600 x 100 |
| Grade | A+, A, B, C, D, F |
| Result | Pass or Fail |
| Attendance_Pct | Attendance percentage |
| Performance_Category | Topper, Above Avg, Average, Below Avg, Needs Support |
| Rank_in_Class | Rank within class division and year |

---

## 🧮 DAX Formulas

### Calculated Columns — Right-click table and select New Column

**CC-1 Pass Fail Flag**

    Pass_Fail_Flag =
    IF(janseva_vidyalaya_performance[Result] = "Pass", "Pass", "Fail")

**CC-2 Performance Band**

    Performance_Band =
    SWITCH(TRUE(),
      [Percentage] >= 85, "Topper",
      [Percentage] >= 75, "Above Avg",
      [Percentage] >= 50, "Average",
      [Percentage] >= 33, "Below Avg",
      "Needs Support")

**CC-3 Attendance Band**

    Attendance_Band =
    IF(
      ISBLANK(janseva_vidyalaya_performance[Attendance_Pct]), "Unknown",
      SWITCH(TRUE(),
        janseva_vidyalaya_performance[Attendance_Pct] >= 90, "Excellent",
        janseva_vidyalaya_performance[Attendance_Pct] >= 75, "Good",
        janseva_vidyalaya_performance[Attendance_Pct] >= 60, "Average",
        "Poor"))

**CC-4 AY Sort Key**

    AY_Sort_Key =
    SWITCH([Academic_Year],
      "2022-23", 1,
      "2023-24", 2,
      "2024-25", 3, 99)

**CC-5 Top Performer Flag**

    Top_Performer =
    IF(janseva_vidyalaya_performance[Rank_in_Class] = 1,
      "Class Topper", "Other")

---

### Measures — Home tab and select New Measure

**M-01 Total Students**

    Total Students =
    COUNTROWS(
      SUMMARIZE(
        janseva_vidyalaya_performance,
        janseva_vidyalaya_performance[Student_Name],
        janseva_vidyalaya_performance[Class],
        janseva_vidyalaya_performance[Division]
      )
    )

**M-02 Average Percentage**

    Average Percentage =
    FORMAT(
      AVERAGE(janseva_vidyalaya_performance[Percentage]),
      "0.00"
    ) & "%"

**M-03 Pass Rate**

    Pass Rate % =
    FORMAT(
      DIVIDE(
        COUNTROWS(FILTER(janseva_vidyalaya_performance, [Result]="Pass")),
        COUNTROWS(janseva_vidyalaya_performance), 0
      ) * 100, "0.00"
    ) & "%"

**M-04 Avg Attendance**

    Avg Attendance % =
    FORMAT(
      AVERAGE(janseva_vidyalaya_performance[Attendance_Pct]),
      "0.00"
    ) & "%"

**M-05 Avg Marathi**

    Avg Marathi = AVERAGE(janseva_vidyalaya_performance[Marathi])

**M-06 Avg Hindi**

    Avg Hindi = AVERAGE(janseva_vidyalaya_performance[Hindi])

**M-07 Avg English**

    Avg English = AVERAGE(janseva_vidyalaya_performance[English])

**M-08 Avg Mathematics**

    Avg Mathematics = AVERAGE(janseva_vidyalaya_performance[Mathematics])

**M-09 Avg Science**

    Avg Science = AVERAGE(janseva_vidyalaya_performance[Science])

**M-10 Avg Social Science**

    Avg Social Science = AVERAGE(janseva_vidyalaya_performance[Social_Science])

**M-11 Topper Count**

    Topper Count =
    CALCULATE(
      COUNTROWS(janseva_vidyalaya_performance),
      janseva_vidyalaya_performance[Grade] = "A+")

**M-12 Fail Count**

    Fail Count =
    CALCULATE(
      COUNTROWS(janseva_vidyalaya_performance),
      janseva_vidyalaya_performance[Result] = "Fail")

**M-13 Needs Support**

    Needs Support =
    CALCULATE(
      COUNTROWS(janseva_vidyalaya_performance),
      janseva_vidyalaya_performance[Performance_Category] = "Needs Support")

**M-14 YoY Improvement**

    YoY Improvement % =
    VAR CY = AVERAGE(janseva_vidyalaya_performance[Percentage])
    VAR PY = CALCULATE(
      AVERAGE(janseva_vidyalaya_performance[Percentage]),
      janseva_vidyalaya_performance[Academic_Year] = "2023-24")
    RETURN DIVIDE(CY - PY, PY, BLANK()) * 100

**M-15 Class Average**

    Class Average % =
    CALCULATE(
      AVERAGE(janseva_vidyalaya_performance[Percentage]),
      ALLEXCEPT(
        janseva_vidyalaya_performance,
        janseva_vidyalaya_performance[Class]))

---

## 🚀 How to Run

**Step 1** — Clone the repository

    git clone https://github.com/GADEKAR328/Student-Annual-Performance---PBI-Dashboard.git

**Step 2** — Open Power BI Desktop

**Step 3** — Home, Get Data, Excel or CSV, select janseva_vidyalaya_performance.csv

**Step 4** — Right-click table, New Column, add CC-1 to CC-5 one by one

**Step 5** — Home, New Measure, add M-01 to M-15 one by one

**Step 6** — Select Academic_Year column, Column Tools, Sort by Column, select AY_Sort_Key

---

## 🎨 Color Theme

<div align="center">

| Role | Hex Code |
|------|----------|
| Primary Navy | #1A3C5E |
| Green Accent | #1A7A4A |
| Amber Topper | #D4840A |
| Red Alert | #dc2626 |
| Background | #F5F7FA |

</div>

---

## 🛠️ Tools Used

<div align="center">

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![DAX](https://img.shields.io/badge/DAX-15%20Formulas-1A3C5E?style=for-the-badge)](/)
[![Python](https://img.shields.io/badge/Python-Dataset-3776AB?style=for-the-badge&logo=python&logoColor=white)](/)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-181717?style=for-the-badge&logo=github)](https://github.com/GADEKAR328)

</div>

---

<div align="center">

## 👤 Yogesh Gadekar (YSG)

📍 Maharashtra, India · Power BI Developer · Data Analytics

[![GitHub](https://img.shields.io/badge/GitHub-GADEKAR328-181717?style=for-the-badge&logo=github)](https://github.com/GADEKAR328)

⭐ Star this repo if you found it useful!

*Built with ❤️ from Maharashtra, India*

</div>
