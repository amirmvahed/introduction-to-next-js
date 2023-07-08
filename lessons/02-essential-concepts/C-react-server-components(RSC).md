## React Server Components (RSC)

RSC resolves these issues by `incrementally streaming the content` of the app from the server to the browser. Let’s see
how this happens. When the user loads the app, the browser is going to send a request to the server. Just like what
happens with SSR, the server is going to fetch the data from the backend.
But `we don’t need to wait till we get the data
from the backend`. There are parts of the app like the header and the side panel that we can render without the data.
So,
the server renders these components and streams them to the browser.

![rsc](./images/essentials/rsc.png)

## Why Server Components?

Server Components allow developers to better leverage server infrastructure. Server Components allow you to render
components on the server, and `reduce the amount of JavaScript` sent to the client, leading to improved
`performance`. With
Server Components, the initial page load is faster, and the client-side JavaScript bundle size is reduced. The base
client-side runtime is `cacheable` and predictable in size, and does not increase as your application grows.
Additional JavaScript is
`only added as client-side interactivity` is used in your application through Client Components.

&nbsp;
&nbsp;
&nbsp;

To make the transition to Server Components easier, all components inside the App Router are **`Server Component by
default.`**



