##**Message Body Reducer**

- messageBodyReducer.ts

The code defines a JavaScript function called messageBodyReducer which is intended to be used as a reducer function in a Redux or similar state management system. The purpose of this reducer is to handle various actions and update the state accordingly.

```typescript
export function messageBodyReducer(state: any, action: any) {
  const { type } = action;
  if (type === "FILTER_SUBMIT") {
    return action?.data;
  } else if (type === "GET_INITIAL_TABLE_PAGE") {
    return {
      ...state,fetch_from_db: false,table_changes: {},
      expand: {
        status: false,row: {},},
      group_by: { ...state?.group_by, status: true },
      page_number: 0,page_size: 10, };
  } else if (type === "COLLAPSE") {
    const { expandHistory } = action;
    return {
      ...state,table_changes: {},fetch_from_db: false,
      expand: {status: true,
        row: { ...expandHistory[expandHistory?.length - 2] },},};
  } else if (type === "EXPAND_ROW") {
    const { row } = action;
    return {
      ...state,table_changes: {},fetch_from_db: false,
      group_by: { ...state?.group_by, status: false },
      expand: { status: true, row: { ...row?.original } },};
  } else if (type === "EDIT_FIELD_SUBMIT") {
    const { row, column, value } = action?.payload;
    return {
      ...state,fetch_from_db: false,
      table_changes: {
    row: row?.original, columnId: column.id, newValue: Number(value),},};
  } else if (type === "SORT") {
    return {
      ...state,fetch_from_db: false,table_changes: {},
      sort: action?.table?.getState()?.sorting[0] ?? {},};
  }else if (type === "PAGE_SIZE") {
    const { value } = action;
    return {
      ...state,fetch_from_db: false,table_changes: {},
      page_size: Number(value),};
  }else if (type === "PAGE_NUMBER") {
    const { value } = action;
    return {
      ...state,fetch_from_db: false,table_changes: {},
      page_number: value,};
  }else if (type === "SECONDARY_FILTER") {
    const { key, value } = action?.payload;
    return {
      ...state,fetch_from_db: false,
      secondary_filter: {
        ...state?.secondary_filter,[key]: value,},};
  }else { return state;}}
```
-here the code takes two parameters, state and action, representing the current state of the application and the action being dispatched, respectively.

-It checks the type property of the action object to determine which action is being dispatched.

-Depending on the action type, it updates the state object accordingly and returns a new state.

-The supported action types and their corresponding state updates are as follows:

"FILTER_SUBMIT": Updates the state with the data from the action.

"GET_INITIAL_TABLE_PAGE": Resets various properties of the state for initializing a table page.

"COLLAPSE": Updates the state to indicate that a row has been collapsed.

"EXPAND_ROW": Updates the state to indicate that a row has been expanded.

"EDIT_FIELD_SUBMIT": Updates the state with changes made to a specific field in a row.

"SORT": Updates the state to reflect sorting changes.

"PAGE_SIZE": Updates the state with a new page size value.

"PAGE_NUMBER": Updates the state with a new page number value.

"SECONDARY_FILTER": Updates the state with secondary filter values.

If the action type doesn't match any of the defined cases, it returns the current state unchanged.

the code defines a reducer function that handles various actions related to table data management and updates the state accordingly, ensuring that the state remains consistent with the application's requirements.