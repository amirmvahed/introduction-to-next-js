## patterns

&nbsp;
&nbsp;
&nbsp;

**Moving Client Components to the Leaves:**
&nbsp;
&nbsp;
&nbsp;

To improve the performance of your application, we recommend moving Client Components to the leaves of your component
tree where possible.
For example, you may have a Layout that has static elements (e.g. logo, links, etc) and an interactive search bar that
uses state.

Instead of making the whole layout a Client Component, move the interactive logic to a Client Component (
e.g. <SearchBar />) and keep your layout as a Server Component. This means you don't have to send all the component
Javascript of the layout to the client.

```js
// SearchBar is a Client Component
import SearchBar from './searchbar'
// Logo is a Server Component
import Logo from './logo'

// Layout is a Server Component by default
export default function Layout({ children }: { children: React.ReactNode }) {
  return (
    <>
      <nav>
        <Logo/>
        <SearchBar/>
      </nav>
      <main>{children}</main>
    </>
  )
}
```

Server and Client Components can be **combined** in the same component tree.

&nbsp;
&nbsp;
&nbsp;

**Unsupported Pattern: Importing Server Components into Client Components:**
&nbsp;
&nbsp;
&nbsp;

The following pattern is not supported. You cannot import a Server Component into a Client Component:

```js
'use client'

// This pattern will **not** work!
// You cannot import a Server Component into a Client Component.
import ExampleServerComponent from './example-server-component'

export default function ExampleClientComponent({
                                                 children,
                                               }: {
  children: React.ReactNode
}) {
  const [count, setCount] = useState(0)

  return (
    <>
      <button onClick={() => setCount(count + 1)}>{count}</button>

      <ExampleServerComponent/>
    </>
  )
}
```

**Recommended Pattern: Passing Server Components to Client Components as Props:**
&nbsp;
&nbsp;
&nbsp;

Instead, when designing Client Components you can use React props to mark "slots" for Server Components.

The Server Component will be rendered on the server, and when the Client Component is rendered on the client, the "slot"
will be filled in with the rendered result of the Server Component.

A common pattern is to use the React children prop to create the "slot". We can refactor <ExampleClientComponent> to
accept a generic children prop and move the import and explicit nesting of <ExampleClientComponent> up to a parent
component.

```js
'use client'

import { useState } from 'react'

export default function ExampleClientComponent({
                                                 children,
                                               }: {
  children: React.ReactNode
}) {
  const [count, setCount] = useState(0)

  return (
    <>
      <button onClick={() => setCount(count + 1)}>{count}</button>

      {children}
    </>
  )
}
```

Now, <ExampleClientComponent> has no knowledge of what children is. Infact, from its perspective it doesn't even know
that children will eventually be filled in by the result of a Server Component.

The only responsibility ExampleClientComponent has is to decide where whatever children will eventually be should be
placed.

In a parent Server Component, you can import both the <ExampleClientComponent> and <ExampleServerComponent> and
pass <ExampleServerComponent> as a child of <ExampleClientComponent>:

```js
// This pattern works:
// You can pass a Server Component as a child or prop of a
// Client Component.
import ExampleClientComponent from './example-client-component'
import ExampleServerComponent from './example-server-component'

// Pages in Next.js are Server Components by default
export default function Page() {
  return (
    <ExampleClientComponent>
      <ExampleServerComponent/>
    </ExampleClientComponent>
  )
}
```

With this approach, the rendering of <ExampleClientComponent> and <ExampleServerComponent> are decoupled and can be
rendered independently - aligning with Server Components, which are rendered on the server before Client Components.

> 💡 It is useful to read about
> The <a href="https://nextjs.org/docs/getting-started/react-essentials#the-server-only-package" target="_blank">"server
> only"</a> package



