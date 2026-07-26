# Absolute Reference — Unit Conversion Exercise

## Task

Convert values from one unit to another using a fixed conversion rate stored
in a single cell:

- **cm → inches**, using a conversion rate in cell `C5`
- **USD → CAD**, using a conversion rate in cell `C13`

The challenge: the value to convert changes with each row, but the
conversion rate stays fixed in one cell — so the formula needs to combine a
relative reference (for the value) with an absolute reference (for the rate).

## Why absolute references matter

A normal (relative) reference shifts automatically when a formula is copied
to other rows or columns. That works fine for the value being converted
(`A7`, `A8`, `A9`...), but breaks the conversion rate reference — copying
`=A7*C5` down would shift `C5` into `C6`, `C7`, etc., pointing at empty cells
instead of the actual rate.

An **absolute reference** (marked with `$`) locks a cell address so it stays
the same no matter where the formula is copied.

## Reference types

| Syntax | Type                 | Behavior when copied                            |
|--------|----------------------|-------------------------------------------------|
| `$C$5` | Fully absolute       | Both column and row stay locked — never changes |
| `C$5`  | Row absolute only.   | Row stays locked; column shifts                 |
| `$C5`  | Column absolute only | Column stays locked; row shifts                 |
| `C5`   | Relative             | Both column and row shift with the formula      |

## Formulas used

**cm → inches** (rate in `$C$5`):
```
=A7*$C$5
```
Copied down from `B7` to `B11`. `A7` shifts to `A8`, `A9`... while `$C$5`
stays fixed.

**USD → CAD** (rate in `$C$13`):
```
=A15*$C$13
```
Copied down from `B15` to `B19` the same way.

## How to toggle reference types

- **Mac:** place the cursor on the cell reference inside the formula and
  press **⌘ + T** to cycle through `C5` → `$C$5` → `C$5` → `$C5` → `C5`.
  If that doesn't work, use **Fn + F4** instead (F4 is Excel's standard
  shortcut for this, but on Mac the F4 key is often mapped to a system
  function by default, so Fn is needed to reach it).
- **Windows:** press **F4** to cycle through the same four reference types.

## Skills demonstrated

- Absolute vs. relative cell references (`$`)
- Copying formulas across a range while keeping a fixed reference point
- Building reusable conversion formulas

## Tools

Excel

## Where these functions are used in real work

**VLOOKUP / INDEX-MATCH**
- Pulling employee data (salary, department, manager) from an HR master list using an employee ID
- Matching product prices or SKUs across price lists and order sheets
- Looking up customer details (address, account status) from a CRM export using a customer ID
- Pulling exchange rates or tax rates from a reference table based on a country/currency code
- Matching survey responses to demographic data using a respondent ID

**COUNTIF / COUNTIFS**
- Counting how many orders are "Pending" vs "Shipped" in a sales tracker
- Counting how many employees are in a specific department AND hired after a certain date
- Counting how many students scored above a threshold in a specific subject
- Flagging duplicate entries in a customer or inventory list

**TRIM**
- Cleaning inconsistent spacing in data exported from another system (CRM, survey tool, scanned form) before merging or matching it with other data
- Preparing text fields for accurate VLOOKUP matches (extra spaces break exact matches)

**PROPER**
- Standardizing names, addresses, or company names imported in inconsistent case (ALL CAPS, all lowercase) for reports and mailing lists

**DATEVALUE**
- Fixing dates imported as text from CSV exports, forms, or other systems, so they can be sorted, filtered, or used in date calculations

**Absolute references ($)**
- Currency and unit conversion tables (fixed exchange/conversion rate applied to a changing list of values)
- Calculating percentages of a fixed total (e.g., each department's share of one company-wide budget)
- Tax or commission calculations using one fixed rate applied across many rows
- Any "one constant, many variables" calculation — discount rates, tax rates, conversion factors

---

## Keyboard shortcut to toggle reference type (relative ↔ absolute)

Cycles through: `C5` → `$C$5` → `C$5` → `$C5` → `C5`

| OS | Shortcut | How it works |
|---|---|---|
| **Windows** | `F4` | Place the cursor on the cell reference inside the formula, press F4 repeatedly to cycle through the four reference types |
| **Mac** | `⌘ + T` | Same idea — cursor on the reference, press ⌘+T to cycle |
| **Mac (alternative)** | `Fn + F4` | Needed if ⌘+T doesn't work — on Mac, F4 is often mapped to a system function (like Dashboard) by default, so Fn brings back the Excel behavior |
| **Linux** (Excel via LibreOffice Calc) | `Shift + F4` | LibreOffice Calc uses a different default shortcut than Excel; place the cursor on the reference and press Shift+F4 to cycle |

**How it works technically:** the `$` symbol locks whichever part of the reference it precedes. `$` before the column letter locks the column; `$` before the row number locks the row. So `$C$5` locks both (fully absolute), `C$5` locks only the row, `$C5` locks only the column, and `C5` with no `$` is fully relative — both shift when the formula is copied.
