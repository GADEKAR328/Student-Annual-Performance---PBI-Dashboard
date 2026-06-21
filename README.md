<div align="center">

# 🏫 Student Annual Performance Dashboard
### Janseva Vidyalaya Wadzire, Maharashtra 414302

*Class 5 to 10 · Academic Performance Analytics · Power BI · By Yogesh Gadekar (YSG)*

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![DAX](https://img.shields.io/badge/DAX-15%20Formulas-1A3C5E?style=for-the-badge)](/)
[![Dataset](https://img.shields.io/badge/Dataset-720%20Rows%20·%2024%20Cols-1A7A4A?style=for-the-badge)](/)
[![Classes](https://img.shields.io/badge/Classes-5%20to%2010-D4840A?style=for-the-badge)](/)
[![Maharashtra](https://img.shields.io/badge/Maharashtra-🇮🇳-FF9933?style=for-the-badge)](/)

> 📊 *A complete Power BI dashboard analyzing student academic performance across Class 5–10 covering 6 subjects, attendance, grades, toppers, and year-over-year improvement trends for Janseva Vidyalaya Wadzire.*

</div>

---

## 📸 Dashboard Preview

<div align="center">

![Dashboard](https://raw.githubusercontent.com/GADEKAR328/Student-Annual-Performance---PBI-Dashboard/6de248b91753abe09a0de19da212aa59a4bf37db/Students%20Performance%20Analytics%20Dashboard.jpg)

</div>

---

## 🏫 About the School

<div align="center">

| New Building | Old Building & Playground |
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
| **12** | **61.78%** | **93.75%** | **78.19%** | **60** | **45** |

</div>

---

## 📊 Dashboard Visuals

| # | Visual | Description |
|---|--------|-------------|
| 🃏 | **6 KPI Cards** | Total Students, Avg %, Pass Rate %, Avg Attendance %, Toppers A+, Fail Count |
| 📊 | **Avg Marks by Subject** | Horizontal bar — Hindi leads at 62.2, Social Science lowest at 61.6 |
| 🍩 | **Grade Distribution** | Donut — C grade highest at 23.19%, A+ at 6.25% |
| 📉 | **Avg % Trend by Academic Year** | Line chart — class-wise trend across FY2022-25 |
| 📊 | **Pass Vs Fail by Class** | Clustered bar — Class 5 best pass rate, Class 10 needs attention |
| 📋 | **Top 10 Students** | Table — Dinesh Shinde 96%, Omkar Mane 95.17% lead |
| 📊 | **Attendance Band by Class** | Stacked bar — Excellent/Good/Average/Poor per class |
| 🔢 | **Class × Subject Avg Marks** | Matrix heatmap — red to green color scale |
| 🔽 | **4 Slicers** | Performance Band · Academic Year · Class · Division |
| 🏠 | **Home Bookmark** | Resets all filters in one click |

---

## 📁 Repository Structure

```
📦 Student-Annual-Performance---PBI-Dashboard
 ┣ 📊 Students Performance Analytics Dashboard.pbix     ← Power BI file
 ┣ 🖼️  Students Performance Analytics Dashboard.jpg     ← Dashboard screenshot
 ┣ 🏫 School Prayer - new building.jpg                  ← School new building photo
 ┣ 🏫 Students Playground old building.jpg              ← School old building photo
 ┣ 📄 janseva_vidyalaya_performance.csv                 ← Dataset (720 rows · 24 cols)
 ┣ 📋 School_Dashboard_YSG.pdf                          ← DAX + Layout guide
 ┗ 📝 README.md                                         ← You are here
```

---

## 🧪 Dataset — 24 Columns

| Column | Description |
|--------|-------------|
| `Student_ID` | Unique ID — JVW0001 format |
| `Student_Name` | Student full name (Maharashtra names) |
| `Gender` | Male / Female |
| `Class` | 5 to 10 |
| `Division` | A or B |
| `Academic_Year` | 2022-23 / 2023-24 / 2024-25 |
| `Marathi` | Marks out of 100 |
| `Hindi` | Marks out of 100 |
| `English` | Marks out of 100 |
| `Mathematics` | Marks out of 100 |
| `Science` | Marks out of 100 |
| `Social_Science` | Marks out of 100 |
| `Total_Marks` | Sum of all 6 subjects |
| `Percentage` | Total / 600 × 100 |
| `Grade` | A+ / A / B / C / D / F |
| `Result` | Pass / Fail |
| `Attendance_Pct` | Attendance percentage |
| `Performance_Category` | Topper / Above Avg / Average / Below Avg / Needs Support |
| `Rank_in_Class` | Rank within class-division-year |

---

## 🧮 DAX — All 15 Formulas

### ⚙️ Calculated Columns

```dax
-- CC-1: Pass Fail Flag
Pass_Fail_Flag =
IF(janseva_vidyalaya_performance[Result] = "Pass", "✅ Pass", "❌ Fail")
```
```dax
-- CC-2: Performance Band
Performance_Band =
SWITCH(TRUE(),
  [Percentage] >= 85, "🏆 Topper",
  [Percentage] >= 75, "⭐ Above Avg",
  [Percentage] >= 50, "📘 Average",
  [Percentage] >= 33, "⚠️ Below Avg",
  "🔴 Needs Support")
```
```dax
-- CC-3: Attendance Band
Attendance_Band =
IF(
  ISBLANK(janseva_vidyalaya_performance[Attendance_Pct]), "Unknown",
  SWITCH(TRUE(),
    janseva_vidyalaya_performance[Attendance_Pct] >= 90, "Excellent",
    janseva_vidyalaya_performance[Attendance_Pct] >= 75, "Good",
    janseva_vidyalaya_performance[Attendance_Pct] >= 60, "Average",
    "Poor"))
```
```dax
-- CC-4: AY Sort Key
AY_Sort_Key =
SWITCH([Academic_Year], "2022-23",1, "2023-24",2, "2024-25",3, 99)
```
```dax
-- CC-5: Top Performer Flag
Top_Performer =
IF(janseva_vidyalaya_performance[Rank_in_Class] = 1, "Class Topper", "Other")
```

### 📐 Measures

```dax
Total Students = DISTINCTCOUNT(janseva_vidyalaya_performance[Student_ID])
```
```dax
Average Percentage =
FORMAT(
    AVERAGE(janseva_vidyalaya_performance[Percentage]),
    "0.00"
) & "%"
```
```dax
Pass Rate % =
FORMAT(
    DIVIDE(
        COUNTROWS(FILTER(janseva_vidyalaya_performance, [Result]="Pass")),
        COUNTROWS(janseva_vidyalaya_performance), 0
    ) * 100,
    "0.00"
) & "%"
```
```dax
Avg Attendance % =
FORMAT(
    AVERAGE(janseva_vidyalaya_performance[Attendance_Pct]),
    "0.00"
) & "%"
```
```dax
Avg Marathi = AVERAGE(janseva_vidyalaya_performance[Marathi])
```
```dax
Avg Hindi = AVERAGE(janseva_vidyalaya_performance[Hindi])
```
```dax
Avg English = AVERAGE(janseva_vidyalaya_performance[English])
```
```dax
Avg Mathematics = AVERAGE(janseva_vidyalaya_performance[Mathematics])
```
```dax
Avg Science = AVERAGE(janseva_vidyalaya_performance[Science])
```
```dax
Avg Social Science = AVERAGE(janseva_vidyalaya_performance[Social_Science])
```
```dax
Topper Count =
CALCULATE(COUNTROWS(janseva_vidyalaya_performance), [Grade] = "A+")
```
```dax
Fail Count =
CALCULATE(COUNTROWS(janseva_vidyalaya_performance), [Result] = "Fail")
```
```dax
Needs Support =
CALCULATE(COUNTROWS(janseva_vidyalaya_performance),
  [Performance_Category] = "Needs Support")
```
```dax
YoY Improvement % =
VAR CY = AVERAGE(janseva_vidyalaya_performance[Percentage])
VAR PY = CALCULATE(AVERAGE(janseva_vidyalaya_performance[Percentage]),
  janseva_vidyalaya_performance[Academic_Year] = "2023-24")
RETURN DIVIDE(CY - PY, PY, BLANK()) * 100
```
```dax
Class Average % =
CALCULATE(AVERAGE(janseva_vidyalaya_performance[Percentage]),
  ALLEXCEPT(janseva_vidyalaya_performance, janseva_vidyalaya_performance[Class]))
```

---

## 🚀 How to Run

```bash
git clone https://github.com/GADEKAR328/Student-Annual-Performance---PBI-Dashboard.git
```
```
1. Open Power BI Desktop
2. Home → Get Data → Excel / CSV → janseva_vidyalaya_performance.csv
3. Right-click table → New Column → add CC-1 to CC-5
4. Home → New Measure → add all 15 measures
5. Column Tools → Sort Academic_Year by AY_Sort_Key
6. Open .pbix directly if uploaded
```

---

## 🎨 Color Theme

| Role | Hex |
|------|-----|
| Primary Navy | `#1A3C5E` |
| Green Accent | `#1A7A4A` |
| Amber (Topper) | `#D4840A` |
| Red (Alert/Fail) | `#dc2626` |
| Background | `#F5F7FA` |

---

## 🛠️ Tech Stack

<div align="center">

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-15%20Formulas-1A3C5E?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-Dataset-3776AB?style=for-the-badge&logo=python&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Portfolio-181717?style=for-the-badge&logo=github)

</div>

---

<div align="center">

## 👤 Yogesh Gadekar (YSG)
📍 Maharashtra, India · Power BI Developer · Data Analytics

[![GitHub](https://img.shields.io/badge/GitHub-GADEKAR328-181717?style=for-the-badge&logo=github)](https://github.com/GADEKAR328)

⭐ **Star this repo if you found it useful!**

*Built with ❤️ from Maharashtra, India*

</div>
