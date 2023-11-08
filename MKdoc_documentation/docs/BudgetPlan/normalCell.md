##**Normal Cell**

- NormalCell.tsx

the code is a JavaScript function which default export named NormalCell. This function takes an object with two properties, getValue and column, as its argument. The purpose of this function is to format and display a value based on certain conditions.

```typescript
export default function NormalCell({ getValue, column }:any) {  const columnsToFormat = [
    "BudgetAmount","Price","BudgetCost",
    "BudgetCostofGoods","SupplyCost",
    "Budget_SKU",];
  let value = getValue();
  if (column?.id?.includes("%")) {
    value = value === null ? "" : value + "%";
  } else if (columnsToFormat.includes(column.id)) {
    value = Number(value)?.toLocaleString("en-US", {});
  } else if (column?.id === "BudgetYear" || column?.id === "HistoricalYear") {
    value =
      String(value)?.toLowerCase() === "none" ||
      String(value)?.toLowerCase() === "nan"
        ? ""
        : Math.trunc(Number(value));}
  return <>{value === null ? "" : value}</>;}
```
-the code initializes an array called columnsToFormat containing the names of specific columns that need formatting.

-It retrieves the value by calling the getValue function and stores it in the value variable.

-It checks various conditions to determine how to format the value:

If the column.id contains a "%" symbol, it appends a "%" to the value if it's not null.

If the column.id matches any of the values in the columnsToFormat array, it attempts to format the value as a number with US locale formatting.

If the column.id is "BudgetYear" or "HistoricalYear," it checks if the value is "none" or "nan" (case-insensitive) and replaces it with an empty string. Otherwise, it converts the value to an integer using Math.trunc.

-Finally, it returns the formatted value, or an empty string if the value is null.

This code is designed for rendering values in a tabular or grid-like user interface, applying specific formatting rules to different columns based on their identifiers (column.id).