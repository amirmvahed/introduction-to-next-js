## React Server Components (RSC)

RSC resolves these issues by incrementally streaming the content of the app from the server to the browser. Let’s see
how this happens. When the user loads the app, the browser is going to send a request to the server. Just like what
happens with SSR, the server is going to fetch the data from the backend. But we don’t need to wait till we get the data
from the backend. There are parts of the app like the header and the side panel that we can render without the data. So,
the server renders these components and streams them to the browser.

![rsc](./images/essentials/rsc.png)

So, There are two environments where your application code can be rendered: the **client** and the **server**.

+ The **client** refers to the browser on a user's device that sends a request to a server for your application code. It
  then turns the response from the server into an interface the user can interact with.
+ The **server** refers to the computer in a data center that stores your application code, receives requests from a
  client, does some computation, and sends back an appropriate response.

Instead of React rendering your whole application client-side (such as in the case of Single-Page Applications), React
now gives you the flexibility to choose where to render your components based on their purpose.
![combination of server components and client components](./images/essentials/client-server-components.png)

**why Server Components?**
Server Components allow developers to better leverage server infrastructure. Server Components allow you to render
components on the server, and **reduce the amount of JavaScript** sent to the client, leading to improved **
performance**.With
Server Components, the initial page load is faster, and the client-side JavaScript bundle size is reduced. The base
client-side runtime is **cacheable** and predictable in size, and does not increase as your application grows.
Additional JavaScript is
**only added as client-side interactivity** is used in your application through Client Components.

&nbsp;
&nbsp;
&nbsp;

To make the transition to Server Components easier, all components inside the App Router are **Server Component** by
default.



