# Conditional Formatting Exercises

Two related exercises practicing formula-based and rule-based conditional
formatting in Excel.

## 1. Accountancy Exam Results

A dataset of 23 exam candidates (ID, area, gender, age, result). Applied
five conditional formatting rules, one per column:

| Column | Rule | How |
|---|---|---|
| Candidate ID | Less than 300000 | `Highlight Cells Rules → Less Than` |
| Area | Contains "South" (South-East, South-West) | Formula: `=ISNUMBER(SEARCH("South",$C4))` |
| Gender | Equals "F" | `Highlight Cells Rules → Equal To` |
| Age | Greater than 40 **and** data bars (two rules stacked on the same range) | `Highlight Cells Rules → Greater Than` + `Data Bars` |
| Result | Top 5% | `Top/Bottom Rules → Top 10%`, changed to 5 |

## 2. Pesko Part-Time Workers Weekly Pay

A payroll sheet for 12 part-time staff, with pay, National Insurance, tax,
pension, and final pay calculated from named ranges (`Hourly_Pay_Rate`,
`Nat_Ins_Rate`, `Tax_Rate`, `Pension_Cont`). Applied eight conditional
formatting rules across the sheet:

| Column | Rule | How |
|---|---|---|
| Staff ID | Female staff (ID starts with "F") | Formula: `=LEFT($B4,1)="F"` |
| Surname | Contains letter "l" | Formula: `=ISNUMBER(SEARCH("l",$C4))` |
| Initial | Equals "H" | `Highlight Cells Rules → Equal To` |
| Hours Worked | ≥ 18 | Formula: `=$E4>=18` |
| Pay | Top 10% | `Top/Bottom Rules → Top 10%` |
| National Insurance | Above average | `Top/Bottom Rules → Above Average` |
| Tax | Data bars | `Data Bars` |
| Pension | Mixed — multiple rules stacked (e.g. color scale + above average) | `Color Scales` + a second rule on the same range |
| Final Pay | Icon set | `Icon Sets` |

## Key lessons on formula-based conditional formatting

- The formula must reference **one row of the applied range**, not the
  whole range — e.g. `$C4`, not `$C$4:$C$15`. A fully absolute range
  returns the same TRUE/FALSE for every cell instead of evaluating each
  row individually.
- Lock the **column** with `$` (so the formula always checks the intended
  column) but leave the **row** relative (so each row evaluates itself).
- "Formula or value in conditional formatting is invalid" is most often
  caused by curly/smart quotes instead of straight quotes (common when
  text is pasted from another app), or by regional settings that expect
  `;` instead of `,` as the argument separator.
- Multiple conditional formatting rules can be stacked on the same range —
  useful for combining a fixed-threshold highlight with a data
  visualization like data bars or an icon set.

## Tools

Excel
