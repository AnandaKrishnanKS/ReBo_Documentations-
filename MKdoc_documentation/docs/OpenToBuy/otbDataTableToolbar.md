##**Data table toolbar**

- data-table-toolbar.tsx
```typescript
export function DataTableToolbar({ table }:any) {
  const { body, dispatchBody } =useContext(OtbContext);
  const [historicalYear, setHistoricalYear] =useState([]);
  const [budgetYear, setBudgetYear] =useState([]);
  function getYearRange(startDate:any, endDate:any){let_arr:any= [];
    if (startDate&&endDate) { for (
        leti=newDate(startDate).getFullYear();
  i<=newDate(endDate).getFullYear(); i++){_arr=[..._arr, String(i)];}}
  return_arr;}
  useEffect(() => { setHistoricalYear(
 getYearRange(body?.history_date_range?.fro,body?.history_date_range?.to));
    setBudgetYear(
      getYearRange(
        body?.forecast_date_range?.fro,
        body?.forecast_date_range?.to));}, [body]);
```
This component is responsible for rendering a toolbar that appears to be part of a data table interface. Here's a brief description of what this code does:

It imports necessary dependencies, including React hooks and context.

Inside the component function, it initializes two state variables, historicalYear and budgetYear, both of which are initially set to empty arrays.

There is a getYearRange function that takes two date parameters (startDate and endDate) and returns an array of year strings within that date range. It checks if both startDate and endDate are provided and then generates an array of years between them.

The useEffect hook is used to set the historicalYear and budgetYear state variables based on date ranges provided from the OtbContext when the body object changes. It calls the getYearRange function with appropriate date range properties from the body object and updates the state variables accordingly.

The component returns a JSX structure, which includes:

Two MultiSelectDD components for selecting "Budget Year" and "Historical Year". These dropdown components display options based on the budgetYear and historicalYear state variables and allow users to select one or more years. When a selection is made, it updates the body object in the context, specifically the budget_year and historical_year properties.

OtbSideDrawer and OtbTopDrawer components, which are not defined in this code snippet, but they seem to be components for displaying side and top drawers, possibly for additional functionality.

A DataTableViewOptions component, which is also not defined here, but it receives the table prop.
