##**ExpandableComponent**

- ExpandableComponent.tsx

The component used for expanding rows in a table or grid view. When the button is clicked, it updates the context state to keep track of expanded rows and makes changes to the dispatchBody state to enable row expansion. The conditional rendering of the "plus" icon suggests that row expansion might be optional for some rows based on the presence of the "ItemLookupCode" property in the data.
```typescript
export const ExpandComponent= ({ getValue, row, column, table }:any) => {
  const { dispatchBody, expandHistory, setExpandHistory } =useContext(OtbContext);
  functionhandleExpand() {
    setExpandHistory((s:any) => [...s, { ...row?.original }]);
    dispatchBody({ type: "EXPAND_ROW", row: row });

  return (

    <button
      className="  pl-4 w-full flex items-center justify-center"
      onClick={handleExpand}>
      {Object?.keys(row?.original).includes("ItemLookupCode") ? null : (
        <PlusCircledIconclassName="mr-2 h-4 w-4"/>)}
    </button>); };
```
component receives some props as parameters: getValue, row, column, and table. These props are likely used to access data and context within the component.

It uses the useContext hook to access values from a context called OtbContext. This context likely contains some shared state or functions that are used within this component.

Inside the handleExpand function, it updates the state stored in the OtbContext. Specifically, it adds the current row.original to the expandHistory array and updates the dispatchBody state with some changes.

It adds a new item to the expandHistory array, containing a copy of the row.original data.

The dispatchBody is a function that handles state and takes an object as its argument. The argument passed to dispatchBody is an object with two properties:
type: This property is set to the string "EXPAND_ROW".
row: This property appears to reference a variable named row.

It renders a button with a click event handler that calls the handleExpand function when clicked.

Within the button's content, it conditionally renders an icon (likely a "plus" icon) using the PlusCircledIcon component. The icon is displayed if the row.original object does not have a property named "ItemLookupCode."
