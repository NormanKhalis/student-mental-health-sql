# 🎓 Student Mental Health Analysis

A SQL-based data analysis project exploring how the **length of stay** impacts the mental health of international students at a Japanese university.

## 📖 Background

A Japanese international university surveyed its students in 2018 and found that international students have a higher risk of mental health difficulties than the general population. Social connectedness and acculturative stress are key predictors of depression.

This project explores whether length of stay is a contributing factor to mental health outcomes among international students.

## 📊 Dataset

The `students` table contains survey responses with the following key columns:

| Column | Description |
|--------|-------------|
| `inter_dom` | Student type (International or Domestic) |
| `stay` | Length of stay in years |
| `todep` | Depression score (PHQ-9 test) |
| `tosc` | Social connectedness score (SCS test) |
| `toas` | Acculturative stress score (ASISS test) |

## 🔍 Analysis

The query filters for international students and groups them by length of stay, computing average mental health scores for each group.

```sql
SELECT stay,
    COUNT(*) AS count_int,
    ROUND(AVG(todep), 2) AS average_phq,
    ROUND(AVG(tosc), 2) AS average_scs,
    ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC
```

## 📈 Results

| Stay (years) | # Students | Avg PHQ-9 | Avg SCS | Avg ASISS |
|:---:|:---:|:---:|:---:|:---:|
| 10 | 1 | 13.00 | 32.00 | 50.00 |
| 8 | 1 | 10.00 | 44.00 | 65.00 |
| 7 | 1 | 4.00 | 48.00 | 45.00 |
| 6 | 3 | 6.00 | 38.00 | 58.67 |
| 5 | 1 | 0.00 | 34.00 | 91.00 |
| 4 | 14 | 8.57 | 33.93 | 87.71 |
| 3 | 46 | 9.09 | 37.13 | 78.00 |
| 2 | 39 | 8.28 | 37.08 | 77.67 |
| 1 | 95 | 7.48 | 38.11 | 72.80 |

## 🛠️ Tools Used

- PostgreSQL

## 📁 Files

- `Student_Guided.sql` — Final SQL query
