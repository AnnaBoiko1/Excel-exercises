# Property Portfolio — Pivot Table Analysis

## What pivot tables are for

A pivot table lets you summarize and explore a large dataset from different
angles without writing any formulas. Instead of manually counting or
averaging rows that match certain conditions, you drag fields into a few
zones (Rows, Columns, Values, Filters) and Excel calculates the summary
instantly — and lets you rearrange it just as fast.

They're one of the most common tools in real data analysis work because
they answer "how does X break down by Y?" questions on the fly — e.g. how
many properties of each type are in each location, or what's the average
price by postcode — without building a single SUMIF or COUNTIF formula, and
without touching the original data.

## Task

A property portfolio dataset (postcode, type, location, bedrooms,
bathrooms, reception rooms, garden size, dates, asking price, sale price)
was summarized using pivot tables built two different ways.

## Steps

### 1. First pivot table — count of properties by type and location
- **Values:** Asking Price (aggregation changed from Sum to **Count**)
- **Rows:** Type
- **Columns:** Location
- **Filters:** all remaining fields

Applied three filters to narrow the count down to properties with:
- 3 bedrooms
- A medium garden
- 2 bathrooms

### 2. Drill down
Double-clicked the cell showing a count of 1 (Detached / Town) to generate
a new sheet with the full underlying record for that single matching
property — a quick way to inspect exactly which row(s) feed into any
summarized number.

### 3. Second pivot table — average asking price by postcode and type
Rebuilt the same pivot table with a different layout:
- **Rows:** PostCode
- **Columns:** Type
- **Values:** Asking Price (aggregation changed to **Average**)
- **Filters:** all remaining fields (filters from the previous step carried
  over, since only the layout was changed)

### 4. Drill down again
Double-clicked an average price cell to confirm which properties fed into
that average.

## Skills demonstrated

- Building and restructuring pivot tables (Rows / Columns / Values /
  Filters)
- Changing the aggregation function (Sum → Count → Average)
- Applying multiple filters to a pivot table
- Drilling down into a pivot table cell to inspect source records

## Tools

Excel
