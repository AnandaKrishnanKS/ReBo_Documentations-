##**CollapseComponent**

- CollapseComponent.tsx
```typescript
exportdefaultfunctionCollapseComponent() {
  const { setBody, expandHistory, setExpandHistory } =useContext(BpContext);
```
Inside the component, it uses the useContext hook to access specific values and functions from the BpContext context. These values/functions include setBody, expandHistory, and setExpandHistory.
```typescript
functionhandleCollapse() {
    if (expandHistory?.length===1) {
      setBody((s:any) => ({ ...s,
        fetch_from_db:false, table_changes: {},
        expand: { status:false, row: {},},
        group_by: { ...s?.group_by, status:true },
        page_number:0,
        page_size:10,})); setExpandHistory([]); } else {
      setBody((s:any) => ({ ...s,
        table_changes: {}, fetch_from_db:false,
        expand: { status:true,
          row: { ...expandHistory[expandHistory?.length-2] },},}));
      setExpandHistory((s:any) => {
        let_arr= [...s]; _arr.splice(s.length-1, 1);
        return_arr;});}}
```
The handleCollapse function is defined and serves as the click event handler for the button.

If expandHistory has a length of 1 (meaning there's only one history item), it sets the setBody and setExpandHistory functions to update the state as follows:

-fetch_from_db is set to false.

-table_changes is reset to an empty object.

-expand status is set to false, and row is an empty object.

-group_by status is set to true.

-page_number is set to 0.

-age_size is set to 10.

-setExpandHistory is called with an empty array to clear the expand history.

If expandHistory has a length greater than 1, it sets the setBody and setExpandHistory functions to update the state as follows:

-table_changes is reset to an empty object.

-fetch_from_db is set to false.

-expand status is set to true, and row is populated with the previous history item.

-The last item from expandHistory is removed by splicing the array.

This component allows you to collapse or expand content and manage the history of those actions using the provided context and state management functions.