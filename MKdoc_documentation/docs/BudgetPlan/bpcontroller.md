##**BpController**

- BpController.tsx

BpController is the parent component of all other components in OTB module, which returns the function BpController() and all states and manged in this parent component and passed through context hook to child components.

####**Description:**

1. Import the necessary hooks and components from React and Material-UI.

```typescript
import { createContext, useEffect, useState } from"react";

importWebSocketDatafrom"./Websocket";

import { EditableTableCell } from"./bp_table/EditableCell";

import { ExpandComponent } from"./bp_table/ExpandableComponent";

importCollapseComponentfrom"./bp_table/CollapseComponent";

import { DateRange } from"react-day-picker";

import BpTabViewfrom"./BpTabView";
``` 

2. Handling States
```typescript
  const [transformedData, setTransformedData] =useState([]);
  const [columnNames, setColumnNames] =useState([]);
  const [mainFilters, setMainFilters] =useState([]);
  const [subFilters, setSubFilters] =useState([]);
  const [mainFilterOptions, setMainFilterOptions] =useState({});
  const [mainFilterValues, setMainFilterValues] =useState({});
  const [loading, setLoading] =useState(false);
  const [webSocketData, setWebSocketData] =useState<any>({});
  const [expandHistory, setExpandHistory] =useState([]);
  const [history_date, setHistoryDate] =useState<DateRange|undefined>({

    from:newDate(),

    to:newDate(),

  });

  const [forecast_date, setForecastDate] =useState<DateRange|undefined>({

    from:newDate(),
    to:newDate(),

  });
```
This code is written in React, a popular JavaScript library for building user interfaces. It uses the useState hook to manage the state of several variables in the component.

Here's a breakdown of the code:

1. `const [transformedData, setTransformedData] = useState([]);`

This line initializes a state variable called `transformedData` with an initial value of an empty array. The `setTransformedData` function is used to update the value of `transformedData`.

2. `const [columnNames, setColumnNames] = useState([]);`

This line initializes a state variable called `columnNames` with an initial value of an empty array. The `setColumnNames` function is used to update the value of `columnNames`.

3. `const [mainFilters, setMainFilters] = useState([]);`

This line initializes a state variable called `mainFilters` with an initial value of an empty array. The `setMainFilters` function is used to update the value of `mainFilters`.

4. `const [subFilters, setSubFilters] = useState([]);`

This line initializes a state variable called `subFilters` with an initial value of an empty array. The `setSubFilters` function is used to update the value of `subFilters`.

5. `const [mainFilterOptions, setMainFilterOptions] = useState({});`

This line initializes a state variable called `mainFilterOptions` with an initial value of an empty object. The `setMainFilterOptions` function is used to update the value of `mainFilterOptions`.

6. `const [mainFilterValues, setMainFilterValues] = useState({});`

This line initializes a state variable called `mainFilterValues` with an initial value of an empty object. The `setMainFilterValues` function is used to update the value of `mainFilterValues`.

7. `const [loading, setLoading] = useState(false);`

This line initializes a state variable called `loading` with an initial value of `false`. The `setLoading` function is used to update the value of `loading`.

8. `const [webSocketData, setWebSocketData] = useState<any>({});`

The `setWebSocketData` function is used to update the value of the WebSocket state variable.

The code is a part below transforms data received from a WebSocket connection into a more readable format.
```typescript
  const [body, setBody] =useState<any>({});

  functiontransformData(_columns:any= [], _data:any) {

    letarr:any= [];

    const_transformedData=_data?.map((item:any, index:any) => {

      letobj= {};

      item?.map((subItem:any, subIndex:any) => {

        obj= { ...obj, [_columns[subIndex]]:subItem };

      });

      arr= [...arr, obj];

    });

    setColumnNames(_columns);

    setTransformedData(arr);

  }
```
1. `const [body, setBody] = useState<any>({});`

This line of code is using the `useState` hook to create a state variable called `body`. The `useState` hook is a function that takes an initial value for the state variable and returns an array with two elements: the current value of the state variable and a function to update it.

In this case, the initial value of the state variable is an empty object (`{}`). The type of the state variable is specified as `any`, which means it can hold any type of value.

The `setBody` function is used to update the value of the `body` state variable.

2. `function transformData(_columns: any = [], _data: any) { ... }`

This function takes two arguments: `_columns` and `_data`. `_columns` is an array of column names, and `_data` is an array of data received from the WebSocket connection.

Inside the function, a new empty array called `arr` is created.

3. `_data?.map((item: any, index: any) = > { ... })`

This line of code uses the `map` function to iterate over each item in the `_data` array. For each item, the following code is executed:

4. `let obj = {}`

This line of code creates a new empty object called `obj`.

5. `item?.map((subItem: any, subIndex: any) => { ... })`

This line of code uses the `map` function to iterate over each sub-item in the `item` array. For each sub-item, the following code is executed:

6. `obj = { ...obj, [_columns[subIndex]]: subItem }`

This line of code updates the `obj` object by adding a new property with a key equal to the corresponding column name from the `_columns` array and a value equal to the sub-item.

7. `arr = [...arr, obj]

This line of code adds the updated `obj` object to the `arr` array.

8. `setColumnNames(_columns);

This line of code updates the `columnNames
```typescript   
 useEffect(() => {

    if (webSocketData) {

      transformData(webSocketData?.columns, webSocketData?.data);

    }

  }, [webSocketData]);
```
this code snippet is using the `useEffect` hook to listen for changes in the `webSocketData` variable. When `webSocketData` changes, the function inside `useEffect` is executed, which in turn calls the `transformData` function to transform the data received from the WebSocket.
```typescript
  return (

    <BpContext.Provider

      value={{
        body,
        setBody,
        mainFilters,
        setMainFilters,
        subFilters,
        setSubFilters,
        mainFilterOptions,
        setMainFilterOptions,
        mainFilterValues,
        setMainFilterValues,
        setWebSocketData,
        webSocketData,
        loading,
        setLoading,
        transformedData,
        setTransformedData
        history_date,
        setHistoryDate,
        forecast_date,
        setForecastDate,
        expandHistory,
        setExpandHistory,
      }}

    >

      <WebSocketData/>

      <BpTabViewcolumns={columns}/>

    </BpContext.Provider>

  );
```
The `BpContext.Provider` is wrapped around two child components: `WebSocketData` and `BpTabView`. The `WebSocketData` component is responsible for handling the WebSocket connection and receiving data from the server. The `BpTabView` component is responsible for rendering the data in a tabular format

The `BpContext.Provider` makes the context properties available to all child components of the component that uses the `BpContext.Provider`. This allows the child components to access and modify the state of the parent component without having to pass the state down through props.

In summary, this code is a React component that uses a context to manage its state and provides this context to its child components. The child components use the context properties to render the data in a tabular format and to handle the WebSocket connection.

code link to [git repo](https://github.com/Electric-Grasshopper/bmaps_web/blob/alpha/src/app/dashboard/service/open__to__buy/components/BpController.tsx).