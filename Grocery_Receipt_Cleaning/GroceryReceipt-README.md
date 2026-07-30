# Grocery Receipt — Data Cleaning & Tax Calculation

## Task

A grocery receipt dataset containing item names, unit prices, quantities,
and purchase dates. The dataset required cleaning before calculating sales
tax and totals per item, plus a grand total for the whole receipt.

## Data issues identified

- **Missing unit price** for one item (Milk) — filled in with a valid price
- **Duplicate row** — one item appeared twice with identical price,
  quantity, and date, indicating an accidental duplicate entry rather than
  a separate purchase

## Cleaning approach

Used a multi-column `COUNTIFS` check to flag true duplicates — rows where
item, price, quantity, **and** date all matched a previous row — rather than
just checking the item name alone (which would have incorrectly flagged
legitimate repeat purchases of the same item on different dates):

```
=COUNTIFS($A$4:A4,A4,$B$4:B4,B4,$C$4:C4,C4,$F$4:F4,F4)
```

The range on the left side of each pair (e.g. `$A$4:A4`) grows by one row
each time the formula is copied down, so it always looks back from the top
of the table to the current row. The first occurrence of a row always
returns `1`; any repeat of the exact same combination returns `2` or more,
flagging it for removal.

## Calculations

**Sales tax per item:**
```
=B4*C4*$E$2
```
`B4` (unit price) and `C4` (quantity) are relative references, since they
change with each item. `$E$2` (the tax rate) is an absolute reference, since
it's a single fixed rate applied to every item on the receipt.

**Total per item (price + tax):**
```
=B4*C4+D4
```

**Grand total for the receipt:**
```
=SUM(E4:E12)
```

## Skills demonstrated

- Multi-column duplicate detection with COUNTIFS
- Handling missing values
- Combining relative and absolute references in tax/total calculations
- SUM for a running total

## Tools

Excel
