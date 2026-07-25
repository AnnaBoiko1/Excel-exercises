# Exact Match VLOOKUP — Library Database

## Task

The dataset is a community library database containing book ISBNs, status
(in/out), category, purchase cost, purchase date, expiry date, and days to
expiry. The goal is to build a search panel that returns full details for any
book, given its ISBN, using an **exact match** VLOOKUP formula.

## Approach

1. **Named ranges** — created a named range for the full lookup table
   (`LibraryTable` → `A4:G15`) and for the search input cell
   (`SearchISBN` → `B18`), to keep formulas readable and avoid broken
   references when copying.

2. **Exact match lookup** — used `VLOOKUP` with `FALSE` as the last argument
   to force an exact match on the ISBN, since an approximate match would be
   unreliable and incorrect for unique identifiers like ISBNs.

   ```
   =VLOOKUP(SearchISBN, LibraryTable, 2, FALSE)
   ```

3. **Column mapping** — copied the formula across four output cells,
   changing only the column index argument to pull the correct field from
   the lookup table:

   | Output cell | Field | Column index in table |
   |---|---|---|
   | Status | Status | 2 |
   | Category | Category | 3 |
   | Expiry Date | Expiry Date | 6 |
   | No Days to Expiry | Days to Expiry | 7 |

4. **Validation** — changed the search ISBN to a different book in the table
   and confirmed all four output fields updated correctly.

## Key formula

```
=VLOOKUP(SearchISBN, LibraryTable, column_index, FALSE)
```

## Skills demonstrated

- Named ranges (Name Manager)
- VLOOKUP with exact match (`FALSE` argument)
- Structuring a reusable search/lookup panel
- Formula validation against known data

## Tools

Excel
