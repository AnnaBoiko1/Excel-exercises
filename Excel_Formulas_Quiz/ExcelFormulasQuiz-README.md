# Excel Formulas Quiz — COUNTIF, SUMIF, IF, ROUND

## Task

A 10-question multiple-choice quiz testing knowledge of common Excel
formulas (COUNTIF, COUNTIFS, SUMIF, SUMIFS, IF, IFS, ROUND, ROUNDUP) using
a small employee performance dataset (department, sales, target, bonus
eligibility, and score).

## Sample data

| Employee | Department | Sales | Target | Bonus Eligible | Score |
|---|---|---|---|---|---|
| Alice | Sales | 12000 | 10000 | Yes | 89 |
| Bob | Marketing | 8500 | 9000 | No | 76 |
| Carol | Sales | 15000 | 12000 | Yes | 93 |
| David | IT | 5000 | 7000 | No | 67 |
| Eva | Marketing | 9200 | 8500 | Yes | 81 |
| Frank | Sales | 9500 | 10000 | No | 72 |
| Grace | IT | 7200 | 7000 | Yes | 90 |

## Answers

| # | Question | Answer | Formula |
|---|---|---|---|
| 1 | Count of Sales department employees | A | `=COUNTIF(B2:B8, "Sales")` |
| 2 | Total sales by Marketing department | B | `=SUMIF(B2:B8, "Marketing", C2:C8)` |
| 3 | Employees who met Target and are in Sales | D | `=COUNTIFS(B2:B8, "Sales", C2:C8, ">=10000")` |
| 4 | Score band (High/Medium/Low) | A | `=IF(F2>=90, "High", IF(F2>=80, "Medium", "Low"))` |
| 5 | Round scores up to the nearest 10 | B | `=ROUNDUP(F2, -1)` |
| 6 | Total sales of bonus-eligible employees | A | `=SUMIF(E2:E8, "Yes", C2:C8)` |
| 7 | "Achieved" / "Not Achieved" based on Sales vs Target | A | `=IF(C2>=D2, "Achieved", "Not Achieved")` |
| 8 | Total of all sales | C | `=SUM(C2:C8)` |
| 9 | Count of Bonus-Eligible IT employees | B | `=COUNTIFS(B2:B8, "IT", E2:E8, "Yes")` |
| 10 | Rounded-up difference between Sales and Target | A | `=ROUNDUP(C2-D2, 0)` |

## Key takeaways

- **COUNTIFS / SUMIFS** cannot compare two ranges cell-by-cell as a single
  condition (e.g. `C2:C8>D2:D8` is not valid syntax inside these
  functions) — each condition needs a range paired with a fixed criterion.
- Text criteria in Excel formulas use double quotes (`"Sales"`), not single
  quotes.
- `SUMIF`/`COUNTIF` (single condition) and `SUMIFS`/`COUNTIFS` (multiple
  conditions) return the same result when only one condition is used —
  `SUMIFS`/`COUNTIFS` is simply the more flexible, multi-condition version.
- Nested `IF` and `IFS` produce the same result for tiered logic; `IFS` is
  more concise but requires Excel 2019+ or Microsoft 365.

## Tools

Excel
