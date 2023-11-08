##**Websocket**

- Websocket.tsx

This code is a React component that uses the `react-use-websocket` library to establish a WebSocket connection to a server. The component is responsible for sending messages to the server and receiving messages from the server.

1. Import necessary libraries and components:

- `React`, `useEffect`, and `useContext` are imported from the "react" library.

- `useWebSocket` is imported from the "react-use-websocket" library.

- `BpContext` is imported from the "./BpController" file.

- `useToast` is imported from the "@/components/shared/use-toast" file.

2. Define the `WebSocketData` component:

 constsocketUrl=`${process.env.NEXT_PUBLIC_BP_WEBSOCKET_BASE_URL}/bp/get_data_ws`;

- The `socketUrl` variable is set to the WebSocket server URL. And its actual url is fetched form .env file.
```typescript
const {
    sendMessage,
    lastMessage,
    readyState,
  } =useWebSocket(socketUrl, {

    shouldReconnect: (closeEvent) => {
      return true; },});
```
- The `useWebSocket` hook is used to establish a WebSocket connection to the server. The hook returns an object with several properties, including `sendMessage`, `lastMessage`, and `readyState`.

- The `useContext` hook is used to access the `BpContext`, which provides access to the state and methods of the BP application.
```typescript
const { body, setWebSocketData, setLoading } =

    useContext(BpContext);

  constdata=lastMessage?JSON?.parse(lastMessage?.data) :null;

  const { toast } =useToast();
```
- The `useToast` hook is used to display toast notifications to the user.
```typescript
useEffect(() => {

    if (data) {

      setWebSocketData(data); }

    setLoading(false);

  }, [JSON?.stringify(data)]);
```
this code is a React component that uses the `useEffect` hook to listen for changes in the `data` object and update its state accordingly.
```typescript
  functiongetBpDataFromWebSocketApi(body:any) {

    sendMessage(JSON.stringify({...body,}));}
```
The `getBpDataFromWebSocketApi` function is used to send a request to a WebSocket API and receive data in response. The `body` object is used to specify the details of the request, such as the type of data being requested or any filters that should be applied to the data.
```typescript
 useEffect(() => {

    if (Object?.keys(body).length) {

      getBpDataFromWebSocketApi(body);}}, [body]);
```
In this case, the useEffect function is an arrow function that checks if the `body` object has any keys. If it does, the function calls the `getBpDataFromWebSocketApi` function and passes the `body` object as an argument.
```typescript
 constconnectionStatus= {
    [ReadyState.CONNECTING]:"Connecting",
    [ReadyState.OPEN]:"Open",
    [ReadyState.CLOSING]:"Closing",
    [ReadyState.CLOSED]:"Closed",
    [ReadyState.UNINSTANTIATED]:"Uninstantiated",}[readyState];

  useEffect(() => {
    window.addEventListener("offline", function () {
      toast({
        variant:"destructive",
        title:"Warning",
        description:"No Internet Connection.",});});});
  useEffect(() => {
    if (connectionStatus==="Closed") {
      toast({variant:"destructive",
        description:"Error, Please wait...",});}},
[connectionStatus]);
```
The first `useEffect` hook listens for the "offline" event, which is triggered when the browser loses its connection to the internet. When this event is triggered, the code creates a toast notification with a "destructive" variant, a "Warning" title, and a "No Internet Connection" description.

The second `useEffect` hook runs when the `connectionStatus` value changes. If the `connectionStatus` value is "Closed", the code creates a toast notification with a "destructive" variant and a "Error, Please wait..." description.
```typescript
useEffect(() => { setModuleConnectionStatus(readyState);}, [readyState]);
```
The `const connectionStatus` line is an object that maps the values of the `ReadyState` enumeration to human-readable strings. The code then uses the current value of the `readyState` variable to look up the corresponding human-readable string in the `connectionStatus` object.
```typescript
useEffect(() => { return () =>setModuleConnectionStatus(6);}, []);
```
this code is a React component returns the current connection status of a WebSocket.

code link to [git repo](https://github.com/Electric-Grasshopper/bmaps_web/blob/alpha/src/app/dashboard/service/budget__plan/components/Websocket.tsx).