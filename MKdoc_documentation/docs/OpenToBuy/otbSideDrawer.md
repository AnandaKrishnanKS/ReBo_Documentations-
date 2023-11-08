##**OtbSideDrawer**

- OtbSideDrawer.tsx

React component called `OtbSideDrawer`. The component uses the `Sheet`, `SheetContent`, `SheetFooter`, `SheetHeader`, `SheetTitle`, and `SheetTrigger` components from the `@/src/components/shared/sheet` module to create a side drawer that can be opened and closed.
```typescript
export function OtbSideDrawer() {

  return (<>
<Sheet>
        <SheetTriggerasChild>
          <ButtonclassName={"whitespace-nowrap m-2"}value={"OTB"}>
            Filters
          </Button>
        </SheetTrigger>
        <SheetContentside={"left"}>
          <SheetHeaderclassName="mb-2">
            <SheetTitle>OTB Filters</SheetTitle>
          </SheetHeader>
          <OtbFilterForm/>
          <SheetFooterclassName="justify-start">
            <small>
              After submitting this form, OTB Table will be populated.
            </small>
          </SheetFooter>
        </SheetContent>
      </Sheet> </>);}
```
The `SheetTrigger` component is used to define the button that opens the side drawer. The `Button` component is used to create the button, and its `value` prop is set to the string `"OTB"`.

The `SheetContent` component is used to define the content of the side drawer. The `side` prop of the `SheetContent` component is set to the string `"left"`, which indicates that the side drawer will open from the left side of the screen.

The `SheetHeader` component is used to define the header of the side drawer. The `SheetTitle` component is used to set the title of the side drawer to the string `"OTB Filters"`.

The `OtbFilterForm` component is used to define the content of the side drawer. This component is responsible for rendering the form that allows users to filter the OTB table.

The `SheetFooter` component is used to define the footer of the side drawer. The `justify-start` class is added to the `SheetFooter` component to align the text in the footer to the left side of the container.

The `small` element is used to display a small piece of text in the footer of the side drawer. This text informs the user that after submitting the form, the OTB table will be populated.