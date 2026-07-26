# Course Grades — Formatting, Tables & Conditional Formatting

## Task

A weekly grades tracker for 9 courses across 5 weeks. The exercise combines
cell formatting, table structuring, conditional formatting, and both simple
and reference-based calculations.

## Steps

### 1. Formatting the header
- Merged and centered the title cells, applied the **Heading 1** cell style
- Set the background fill to **Blue, Accent 1, Darker 25%**
- Set the font color to **white** for contrast
- Renamed the active sheet to reflect the student's name (other sheets left
  at default)

### 2. Table setup
- Converted the weekly grades range into an Excel **Table**
- Removed the table's filter buttons for a cleaner look
- Corrected two cells that were stored as percentages instead of plain
  numbers, so they'd calculate consistently with the rest of the table
- Removed decimal places across the grades range

### 3. Conditional formatting
- **Weeks 1–3:** highlighted any score greater than 80 (`Highlight Cells
  Rules → Greater Than`)
- **Week 4:** highlighted the single highest score (`Top/Bottom Rules → Top
  1 Item`)
- **Week 5:** highlighted the single lowest score (`Top/Bottom Rules →
  Bottom 1 Item`)

### 4. Summary calculations
For each course, calculated in the summary table:
- **Total:** `=SUM(B8:F8)`
- **Average:** `=AVERAGE(B8:F8)`
- **Highest score:** `=MAX(B8:F8)`
- **Lowest score:** `=MIN(B8:F8)`

Each formula was written once and copied across for the remaining courses.

### 5. Relative vs. absolute reference
Recalculated the average manually (total ÷ number of weeks) instead of using
`AVERAGE`, to practice combining a relative and an absolute reference in one
formula:

```
=B23/$I$22
```

- `B23` (the course total) is a **relative** reference — it shifts to `C23`,
  `D23`... when copied across to the next course
- `$I$22` (the fixed number of weeks) is an **absolute** reference — it stays
  locked on `I22` no matter where the formula is copied

## Skills demonstrated

- Cell styles, merge & center, fill and font color
- Excel Tables (formatting, filter toggle)
- Number formatting (percentage vs. plain number, decimal control)
- Conditional formatting: fixed threshold rules vs. dynamic top/bottom rules
- SUM, AVERAGE, MAX, MIN
- Combining relative and absolute references in a single formula

## Tools

Excel
