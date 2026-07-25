# Singapore Schools — Data Cleaning Exercise in Excel 

## Task

The dataset contains general information about schools in Singapore: school name,
area, address, level (Primary / Secondary / Junior College / Mixed Level), bus
routes serving the school, and the last date of admission.

The raw dataset contained several common data quality issues that needed to be
fixed before analysis.

**Business question:** How many primary schools are located in the West area?

## Dataset overview

| Column | Description |
|---|---|
| `school_name` | Name of the school |
| `area` | Area where the school is located |
| `address` | Address of the school |
| `level` | School type (Primary / Secondary / Junior College / Mixed Level) |
| `bus` | Bus routes serving the school |
| `AddmissionLastDate` | Last date of admission |

## Data issues identified

- Blank rows scattered throughout the dataset
- Extra leading/trailing spaces in school names
- Duplicate rows
- Spelling mistakes in school names (e.g., inconsistent spellings)
- Inconsistent date formats (`09-09-2021`, `2021-08-08`, `2023-14-05` — including
  clearly invalid dates)
- School level embedded in the name field for some rows (e.g., names with
  `(Junior)` or `(Primary)` in parentheses)
- Inconsistent letter casing in school names (e.g., `GAN ENG SENG PRIMARY SCHOOL`
  instead of `Gan Eng Seng Primary School`)

## Cleaning steps

1. **Remove blank rows**
   `Go To Special → Blanks` → `Delete → Shift cells up`

2. **Trim extra spaces from school names**
   `=TRIM(A2)` → Paste Special (Values Only) over the `school_name` column

3. **Find and remove duplicate rows**
   `=COUNTIF($A$2:A2,A2)` — flags repeated rows (result > 1), then filter and
   delete manually

4. **Spell check**
   Manual review of school names, cross-checked by sorting alphabetically

5. **Standardize dates**
   `=DATEVALUE(F2)` → format to a single consistent date format (DD/MM/YYYY)

6. **Split school name and level**
   Flash Fill (`Ctrl+E`) to separate the school level (Junior/Primary/Secondary)
   where it was embedded in the name

7. **Standardize name casing**
   `=PROPER(A2)` → Paste Special (Values Only)

## Answer formula

```
=COUNTIFS(area_range, "West", level_range, "Primary")
```

## Tools

Excel / WPS Office — `TRIM`, `COUNTIF`, `COUNTIFS`, `DATEVALUE`, `PROPER`, `Conditional Formatting rules`, `Paste Special (Values Only)`, `Flash Fill`, `Ctrl+E`, `Spell Check`, `Filter`, `Sort`, `Delete`, `Go To Special Blanks`, `Shift cells up`, `Paste Special`