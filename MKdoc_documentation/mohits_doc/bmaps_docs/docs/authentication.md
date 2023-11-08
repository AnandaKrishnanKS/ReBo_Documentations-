# Authentication

## Overview

Authentication service is used to authenticate the the user and provide access to the services which they can use.

### API Calls

#### Interface

```typescript
// Define interface for type safety
interface LoginPayload {
    username: string;
    password: string;
}

interface LoginResponse {
    message: string;
    access_token: string;
    refresh_token: string;
}
```

#### Actual API Calls
```typescript
export const login = async (payload: LoginPayload): Promise<LoginResponse> => {
    try {
        const response = await axios.post<LoginResponse>(
            ENDPOINTS.LOGIN, 
            payload,
            { headers: DEFAULT_HEADERS }
        );
        
        // Store tokens in session storage
        sessionStorage.setItem('access_token', response.data.access_token);
        sessionStorage.setItem('refresh_token', response.data.refresh_token);
        
        return response.data;
    } catch (error) {
        if (axios.isAxiosError(error)) {
            const axiosError = error as AxiosError<ErrorResponse>;

            if (axiosError.response) {
                throw new Error(axiosError.response.data.message || axiosError.response.data.detail || 'Error logging in');
            } else if (axiosError.request) {
                throw new Error('No response received from server. Please try again.');
            }
        }
        // Handle generic error
        throw new Error('Error fetching user details.');
    }
};
```
#### Login Page UI

![Login Page](https://www.positronx.io/wp-content/uploads/2019/09/react-login-ui-6748-01.png)

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

```
This is a small demonstration .pdf file -
```
```
just for use in the Virtual Mechanics tutorials. More text. And more
text. And more text. And more text. And more text.
```
```
And more text. And more text. And more text. And more text. And more
text. And more text. Boring, zzzzz. And more text. And more text. And
more text. And more text. And more text. And more text. And more text.
And more text. And more text.
```
```
And more text. And more text. And more text. And more text. And more
text. And more text. And more text. Even more. Continued on page 2 ...
```

# Simple PDF File 2

```
...continued from page 1. Yet more text. And more text. And more text.
And more text. And more text. And more text. And more text. And more
text. Oh, how boring typing this stuff. But not as boring as watching
paint dry. And more text. And more text. And more text. And more text.
Boring. More, a little more text. The end, and just as well.
```
