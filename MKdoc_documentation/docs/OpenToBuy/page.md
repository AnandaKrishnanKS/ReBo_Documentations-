##**Page**

- page.tsx

In Next.js, you can handle page routing by creating .tsx files for each of your pages. Here's a brief overview of how page routing works in Next.js using a page.tsx file. The name of default function in page.tsx that export is OtbPage() is given below:

```typescript
exportdefaultfunctionOtbPage() {

  return (

    <divclassName="flex-1 h-full space-y-4 p-8 pt-6">

      <OtbController/>

    </div>

  );

}
```
###**Description:**

1. Import OtbController component

2. Define OtbPage component

3. Return JSX for the component

4. JSX for the component includes a div with className "flex-1 h-full space-y-4 p-8 pt-6"

5. Inside the div, there are two elements:

- A div with className "flex items-center justify-between space-y-2" that contains an h2 element with text "Open To Buy"

- An instance of the OtbController component

6. The OtbPage component is exported as the default export

This code defines a React component called OtbPage that renders a page with a title "Open To Buy" and a controller for managing the Open To Buy functionality.

code link to [git repo](https://github.com/Electric-Grasshopper/bmaps_web/blob/alpha/src/app/dashboard/service/open__to__buy/page.tsx).