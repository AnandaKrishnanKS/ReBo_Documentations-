##**Secondary Filter**

-SecondaryFilter.tsx

here the code encapsulates a secondary filter component for selecting multiple values, dynamically loading options, and managing state changes through the Context API.

```typescript
export default function SecondaryFilter({ title, keyName }: any) {
  const { body, dispatchBody } = useContext(OtbContext);
  const [options, setOptions] = useState([]);

  useEffect(() => {
    getSecondaryFilters().then((response: any) => {
        console.log({ response });
        setOptions(response?.data[keyName]);})
      .catch((err) => {console.log(err);});}, []);
```

code takes two props, title and keyName. Inside the component, it uses the React Context API to access some shared context data, particularly the body and dispatchBody objects. It also utilizes React's useState and useEffect hooks.

In the useEffect, the component fetches some secondary filter options using the getSecondaryFilters function, and upon success, it updates the component's state with the received data. Any errors during the fetch operation are logged to the console.

The component renders a MultiSelectDD component, passing in the title, options, and selectedValues as props. The selectedValues are derived from the body object's secondary_filter property, specifically the keyName within it, and defaults to an empty array if it is not present.

When a user selects values in the MultiSelectDD, it triggers a change event, and the dispatchBody function is called to update the body state with the selected values for the specified keyName.