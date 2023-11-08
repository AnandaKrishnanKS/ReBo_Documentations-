##**OtbForm**

- OtbForm.tsx

The component returns form includes filters for sales channel, product family, product sub-family, brand/supplier, product category, product sub-category, item code, top items, and store class. The filters are implemented using the MainFilters and HierarchyFilter components, which are custom components that render the appropriate filter options based on the provided filter type.
```typescript
constformSchema=z.object({
  history_dates:z.string(),
  forecast_dates:z.string(),
});
```
This code defines a form schema using the Zod library. The form schema is an object with two properties: history_dates and forecast_dates. Both properties are strings.

The Zod library is a schema validation library for JavaScript and TypeScript. It allows you to define the shape of your data and validate it against that shape.

In this code, the form schema is defined as an object with two properties: history_dates and forecast_dates. Both properties are strings, which means that they can only contain text.

The form schema is then assigned to the variable formSchema. This variable can be used to validate form data against the schema.
```typescript
 constform=useForm<z.infer<typeofformSchema>>({
    resolver:zodResolver(formSchema),
    defaultValues: {
      history_dates:"",
      forecast_dates:"",},});
```
This code is using the React Hook Form library to create a form with validation using the Zod library.

1. `const form = useForm<z.infer<typeof formSchema>>({...})`: This line is using the `useForm` hook from React Hook Form to create a form with a specific type. The type is inferred from the `formSchema` variable, which is a Zod schema.

2. `resolver: zodResolver(formSchema)`: This line is setting the resolver for the form to a Zod resolver. The Zod resolver is a function that takes a Zod schema and returns a resolver function that can be used to validate form data against that schema.

3. `defaultValues: {...}`: This line is setting the default values for the form. In this case, the default values are an empty string for both the `history_dates` and `forecast_dates` fields.
```typescript
function handleSubmit() {
    setExpandHistory([]);
  consthistoryAndForecastData= {
    history_date_range: {
      fro:history_date?.from? format(history_date?.from, "yyyy-MM-dd"):"",
      to:history_date?.to?format(history_date?.to, "yyyy-MM-dd") :"",},
    forecast_date_range: {
      fro:forecast_date?.from
        ?format(forecast_date?.from, "yyyy-MM-dd"):"",
   to:forecast_date?.to?format(forecast_date?.to, "yyyy-MM-dd") :"",},};
    constotherFilters:any= {
      sales_channel:mainFilterValues?.channel?? [],
      product_family:mainFilterValues?.family?? [],
      sub_families:mainFilterValues?.sub_family?? [],
      category:mainFilterValues?.category?? [],
      sub_category:mainFilterValues?.sub_category?? [],
      suppliers:mainFilterValues?.suppliers?? [],
      sku:mainFilterValues?.sku?? [],
      top_items:mainFilterValues?.top_items?? [],
      store_class:mainFilterValues?.class?? [],};
    constgroup_by=Object?.keys(otherFilters)?.filter((item, index) => {
      returnotherFilters[item]?.length>0;});
    constadditionalData= {
      page_number:0,
      page_size:10,
      fetch_from_db:true,
      group_by: { status:true, columns:group_by?? [] },
      expand: { status:false, row: {} },
      sort: {},
      table_changes: {}, };
    constdata= {
      ...historyAndForecastData,
      ...otherFilters,
      ...additionalData, };
    if (JSON?.stringify(body) !==JSON?.stringify(data)) {
      setBody(data);
      setLoading(true);}
    toast({
      title:"You submitted the following values:",
      description: (
        <preclassName="mt-2 w-[340px] rounded-md bg-slate-950 p-4">
          <codeclassName="text-white">
            {JSON.stringify(
              { ...historyAndForecastData, ...otherFilters },null,2)}
          </code>
        </pre>),});}
```
1. The `handleSubmit()` function is called when the form is submitted.

2. The function first sets the `expandHistory` state to an empty array.

3. The function then creates an object called `historyAndForecastData` that contains the `history_date_range` and `forecast_date_range` properties. These properties are objects that contain the `fro` and `to` properties, which are the formatted dates from the `history_date` and `forecast_date` objects.

4. The function then creates an object called `otherFilters` that contains the properties for the main filter values.

5. The function then creates an array called `group_by` that contains the keys of the `otherFilters` object that have a length greater than 0.

6. The function then creates an object called `additionalData` that contains the properties for the page number, page size, fetch from database, group by, expand, sort, and table changes.

7. The function then creates an object called `data` that is a combination of the `historyAndForecastData`, `otherFilters`, and `additionalData` objects.

8. The function then checks if the `body` state is not equal to the `data` object. If it is not equal, the function sets the `body` state to the `data` object and sets the `loading` state to true.

9. Finally, the function creates a toast notification that displays the submitted values. The toast notification contains a title and a description that displays the submitted values in a formatted JSON object.

code link to [git repo](https://github.com/Electric-Grasshopper/bmaps_web/blob/alpha/src/app/dashboard/service/open__to__buy/components/OtbForm.tsx).
