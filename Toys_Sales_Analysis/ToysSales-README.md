# Toys Sales Analysis — Formulas, SUMIF, Conditional Formatting & References

## Task

A toy sales report with 14 items across 6 categories. The exercise combines
formatting, nested IF logic, category-level aggregation with SUMIF,
conditional formatting, and a relative/absolute reference challenge for a
time-limited discount offer.

## Steps

### 1. Formatting the report
- Inserted a title row, merged and centered it, applied the **Heading 1**
  cell style
- Set the title background to **Blue, Accent 1, Darker 25%** with white font
- Renamed the sheet, adjusted row height and vertical alignment for the
  header row
- Formatted all price columns (except Quantity Ordered) as currency (£, 2
  decimal places)

### 2. Simple functions
- **Cost:** `=C3*D3` (Price Each × Quantity Ordered)
- **Discount (nested IF):**
  ```
  =IF(D3>7,10%,IF(D3>4,5%,0))
  ```
  Checks the stricter condition first (quantity > 7) before the looser one
  (quantity > 4) — checking in the opposite order would misclassify every
  quantity above 7 as only qualifying for the 5% tier.
- **Final Cost:** `=E3*(1-F3)` (Cost minus the discount percentage)

### 3. Category summary with SUMIF
Built a summary table listing each unique category, then calculated:
```
=SUMIF($A$3:$A$16,I2,$G$3:$G$16)   → Total Price
=SUMIF($A$3:$A$16,I2,$D$3:$D$16)   → Total Quantity
```
- The data ranges (`$A$3:$A$16`, `$G$3:$G$16`, `$D$3:$D$16`) use **absolute**
  references, since they must stay pointed at the same source table no
  matter which row of the summary the formula is copied to.
- The category cell (`I2`) uses a **relative** reference, since it needs to
  shift to the next category (I3, I4...) as the formula is copied down.

### 4. Conditional formatting
- Highlighted category totals where **Total Price > 80**
- Highlighted category totals where **Total Quantity > 10**

### 5. Relative & absolute reference — time-limited offer
- Added a cell above the table holding a one-time discount rate
  (`Today's offer`, e.g. 50%)
- Added an **Offer** column applying that extra discount only to items
  ordered in quantity greater than 10:
  ```
  =IF(D4>10,G4*(1-$C$2),G4)
  ```
  `D4` and `G4` are relative (they shift per row); `$C$2` is absolute,
  always pointing at the single offer-rate cell regardless of which row the
  formula is copied to.

## Skills demonstrated

- Cell styles, merge & center, currency formatting
- Nested IF logic
- SUMIF for category-level aggregation
- Conditional formatting with fixed thresholds
- Combining relative and absolute references in a single formula

## Tools

Excel
