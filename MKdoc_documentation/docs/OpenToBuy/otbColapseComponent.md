##**CollapseComponent**

- CollapseComponent.tsx
```typescript
export default function CollapseComponent() {
  const { dispatchBody, expandHistory, setExpandHistory } =useContext(OtbContext);
```
Inside the component, it uses the useContext hook to access specific values and functions from the OtbContext context. These values include dispatchBody, expandHistory, and setExpandHistory.
```typescript
function handleCollapse() {
    if (expandHistory?.length === 1) {
      dispatchBody({ type: "GET_INITIAL_TABLE_PAGE" });
      setExpandHistory([]); } else {
      dispatchBody({ type: "COLLAPSE", expandHistory: expandHistory });
      setExpandHistory((s: any) => {
        let _arr = [...s];
        _arr.splice(s.length - 1, 1); 
        return _arr;});}}
```

The handleCollapse function is defined and serves as the click event handler for the button.

the function first checks if the expandHistory array has a length of 1, indicating that the component is currently expanded and has no prior history of being expanded.
If the length is indeed 1, it dispatches an action to get the initial table page and resets the expandHistory array to an empty state, effectively collapsing the component.
If the expandHistory array has a length greater than 1, it dispatches a "COLLAPSE" action and updates the expandHistory array by removing the most recent entry from it. This effectively restores the component to its previous expanded state or moves it back one step in the expansion history.

In short the component helps to tracks the expansion and collapsing history of a component and allows users to toggle between different states of the component's visibility.