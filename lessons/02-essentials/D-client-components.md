## Client Components

Client Components enable you to add client-side interactivity to your application. In Next.js, they are pre-rendered on
the server and hydrated on the client. You can think of Client Components as how components in the Pages Router have
always worked.

&nbsp;
&nbsp;
&nbsp;

write 'use client' for creating client components:

```js
'use client'

import { useState } from 'react'

export default function Counter() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  )
}
```

Once "use client" is defined in a file, all other modules imported into it, including child components, are considered
part of the client bundle.

Since Server Components are the default, all components are part of the Server Component module graph unless defined or
imported in a module that starts with the "use client" directive.



