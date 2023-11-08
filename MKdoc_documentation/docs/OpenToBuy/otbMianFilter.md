##**MainFilter**

- mainFilter.tsx

mainFilter.tsx is another component created in mainFilter folder that allows users to select values for a filter. The component takes in two props: title and filter.
```typescript
exportdefaultfunctionMainFilters({ title, filter }:FilterProp) {
  const {
    mainFilterOptions,
    setMainFilterOptions,
    mainFilterValues,
    setMainFilterValues,
  } =useContext(OtbContext);
  useEffect(() => {
    if (!mainFilterOptions[filter]) {
      getMasterFilters([filter])
        .then((resp:any) => {
          setMainFilterOptions((s:any) => ({...s,
            [filter]:resp?.filter_values[filter],}));})
        .catch((err) =>console.log({ err }));}
  }, [mainFilterOptions[filter]]);
  functionhandleChange(e:any) {
    setMainFilterValues((s:any) => ({ ...s, [filter]:e }));}
```
The component state is managed using the useContext hook, which allows the component to access the mainFilterOptions, setMainFilterOptions, mainFilterValues, and setMainFilterValues state variables from the OtbContext.

The useEffect hook is used to fetch the available values for the filter if they are not already available in the mainFilterOptions state variable. The getMasterFilters function is used to fetch the available values for the filter from the server.

The handleChange function is used to handle changes to the selected values of the filter. When the user selects a value, the handleChange function updates the mainFilterValues state variable.

The component returns a MultiSelectDD component, which is used to display the available values for the filter and allow the user to select values.
