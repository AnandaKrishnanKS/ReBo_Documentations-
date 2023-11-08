##**OtbTopDrawer**

- OtbTopDrawer.tsx

This is another component in otb_graph folder which has path to OTB graph, given below is the sample code;
```typescript
exportfunctionOtbTopDrawer() {

  return (
    <>
      <Sheet>
        <SheetTriggerasChild>
          <ButtonclassName=" border-2 mr-2 bg-white">
            <svgwidth="15"height="15"viewBox="0 0 15 15"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"  >
                <pathd="M11.5 1C11.7761 1 12 1.22386 12 1.5V13.5C12 13.7761 ..."
                fill="#000000"
                fill-rule="evenodd"
                clip-rule="evenodd"></path>
            </svg>
          </Button>
        </SheetTrigger>
        <SheetContentside={"top"}>
          <SheetHeaderclassName="mb-2">
            <SheetTitle>OTB Chart</SheetTitle>
          </SheetHeader>
          <divclassName=" w-96 h-96 ">
            <OtbGraph/>
          </div>
        </SheetContent>
      </Sheet> 
    </>);}
```
The component has three main parts:

- The `Sheet` component, which is used to create the container for the chart.

- The `SheetTrigger` component, which is used to display the button that triggers the opening of the chart.

- The `SheetContent` component, which is used to display the chart itself.

The `Sheet` component has a `side` prop, which is used to specify the side of the screen on which the chart will be displayed. In this case, the chart will be displayed on the top of the screen.

The `SheetTrigger` component has a `className` prop, which is used to specify the CSS class that will be applied to the button. In this case, the button will have the `border-2 mr-2 bg-white` CSS class applied to it.

The `SheetContent` component has a `className` prop, which is used to specify the CSS class that will be applied to the chart. In this case, the chart will have the `w-96 h-96` CSS class applied to it.

The `OtbGraph` component is used to display the chart itself. This component is not included in the code you provided, but it is likely that it is a custom component that is used to display the chart data.
