## When to use Server and Client Components?

So, There are two environments where your application code can be rendered: the **client** and the **server**.

+ The `client` refers to the browser on a user's device that sends a request to a server for your application code. It
  then turns the response from the server into an interface the user can interact with.
+ The `server` refers to the computer in a data center that stores your application code, receives requests from a
  client, does some computation, and sends back an appropriate response.

Instead of React rendering your whole application client-side (such as in the case of Single-Page Applications), React
now gives you the flexibility to choose where to render your components based on their purpose.
![combination of server components and client components](./images/essentials/client-server-components.png)

To simplify the decision between Server and Client Components, we recommend using Server Components (default in the app
directory) until you have a use case for a Client Component.

This table summarizes the different use cases for Server and Client Components:

&nbsp;
&nbsp;
&nbsp;

![combination of server components and client components](./images/essentials/server-client-use.png)


