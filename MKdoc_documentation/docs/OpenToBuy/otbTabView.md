##**OtbTabView**

– OtbTabView.tsx

The code in OtbTabView.tsx is defining a React functional component called `OtbTabView` and exporting it as the default export.

Editable columns:
```typescript
consteditableColumns= [

    "Budget%",
    "BudgetvsACT_FCT",
    "BudgetvsLY%",
    "BudgetvsLLY%",
    "BudgetQTY",
    "Logistic%",
    "ProposedSellThru%",
    "DisplayItem",
    "COR_valueENDOfLifeStock",

  ];
```
This code defines a constant variable called `editableColumns`. The variable is an array that contains a list of strings. Each string represents the name of a column that can be edited in a table or data grid.
```typescript
const getColumns= (tabName:string) => {
    functioncommonColumns():any {
      let_commonColumn:any= [];
      webSocketData?.tabs[tabName]?.map((item:any, index:any) => {
        if (webSocketData?.columns?.includes(item)) {
          _commonColumn= [..._commonColumn, item];}});
      return_commonColumn;}
    if (Object?.keys(webSocketData)?.length) {
      if (tabName==="BudgetValue") {return [{
            id:"Expandable",
    header:expandHistory?.length?<CollapseComponent/>:null,
    cell:ExpandComponent,enableSorting:false,enableHiding:false,
    footer:"Total", },...(webSocketData?.tabs[tabName]?.length>0
            ?commonColumns()?.map((item:any, index:any) => {
                if (editableColumns?.includes(item)) {
          return { header:modifyHeaders(item),
                    accessorKey:item,
                    cell:EditableTableCell,
                    enableHiding:!mandatoryColumns?.includes(item),
                    footer:webSocketData?.total[item]
                      ?Number(webSocketData?.total[item])?.toLocaleString(
                          "en-US",{}):null,};
            } else { return {
                    header:modifyHeaders(item),
                    accessorKey:item,
                    cell:NormalCell,
                    enableHiding:!mandatoryColumns?.includes(item),
                    footer:webSocketData?.total[item]
                      ?Number(webSocketData?.total[item])?.toLocaleString(
                          "en-US", {} ) :null,
                    filterFn: (row:any, id:any, value:any) => {
             returnvalue.includes(String(row.getValue(id)))},}}}) : []),];
 } else {returncommonColumns()?.map((item:any, index:any) => {return {
            header:modifyHeaders(item),
            accessorKey:item,
            cell:NormalCell,footer:webSocketData?.total[item]?Number (webSocketData?.total[item])?.toLocaleString("en-US", {}) :null,
    filterFn: (row:any, id:any, value:any) => {
 returnvalue.includes(String(row.getValue(id)));},};});}} elsereturn [];};
```
####commonColumns() Function:

This inner function is defined to extract common columns from the webSocketData associated with the given tabName. It iterates through the items in the webSocketData and checks if each item is included in the webSocketData.columns array. If it is, the item is added to the _commonColumn array.

####Main Function Logic:

The main getColumns function begins by checking if the webSocketData object has keys (i.e., if it's not empty). If it is empty, an empty array is returned.

If the tabName is "BudgetValue," it returns a specific array of column configurations:

It includes an expandable column with an optional header based on the expandHistory length.

It then processes the common columns obtained using the commonColumns function.

For each common column, it checks if it's in the editableColumns. If yes, it creates a configuration for an editable cell (EditableTableCell) with specific headers, accessor keys, and footers.

If the column is not in editableColumns, it configures it for a normal cell (NormalCell) with headers, accessor keys, and footers.

Additionally, it sets up a filter function for each column to filter rows based on the provided value.

If the tabName is not "BudgetValue," it simply returns an array of column configurations for the common columns, following a similar structure as described above.

Overall, this code is used to dynamically generate an array of column configurations based on the specified tabName and the data stored in the webSocketData object. The resulting array can then be used in a data table or grid component to define how data is displayed and interacted with in the user interface.

check the code in [git repo](https://github.com/Electric-Grasshopper/bmaps_web/blob/alpha/src/app/dashboard/service/open__to__buy/components/OtbTabView.tsx).
