---
created:
  "{ date }": 
tags:
  - job/tracking
updated: 2025-04-25T15:17
---

# High-Scoring Job Opportunities

## Opportunities Scored Above 5

```dataview
TABLE
  position as "Position",
  company as "Company",
  location as "Location",
  ai-score as "Score",
  status as "Status"
FROM "원티드"
WHERE ai-score >= 5
SORT ai-score DESC
```

## Score Distribution

```dataview
TABLE
  length(rows) as "Count",
  round(avg(ai-score), 1) as "Avg Score"
FROM "원티드"
GROUP BY status
SORT length(rows) DESC
```

## Recent High-Scoring Opportunities

```dataview
TABLE
  position as "Position",
  company as "Company",
  ai-score as "Score",
  created as "Date Added"
FROM "원티드"
WHERE ai-score >= 5
SORT created DESC
LIMIT 5
```

## Technical Match Analysis

```dataview
TABLE
  position as "Position",
  tech-match as "Tech Match",
  growth-potential as "Growth",
  ai-score as "Overall Score"
FROM "원티드"
WHERE ai-score >= 5
SORT tech-match DESC
```

## High-Scoring 사람인 Opportunities

```dataview
TABLE
  position as "Position",
  company as "Company",
  location as "Location",
  ai-score as "Score",
  status as "Status"
FROM "사람인"
WHERE ai-score >= 8
SORT ai-score DESC
```
