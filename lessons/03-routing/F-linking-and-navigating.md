## Linking and Navigating

There are two ways to navigate between routes:

+ `<Link>` Component
+ `useRouter` Hook

## `<Link>` Component

`<Link>` is a React component that extends the HTML `<a>` element to provide `prefetching` and `client-side` navigation
between routes. It is the primary way to navigate between routes in Next.js.

To use `<Link>`, import it from `next/link`, and pass a href prop to the component:

```js
import Link from 'next/link'

export default function Home() {
  return <>
    <h1>Welcome home!</h1>
    <Link href="/users">Users</Link>
  </>
}
```

> 💡 for more information about `<Link>` component
> see <a href="https://nextjs.org/docs/app/api-reference/components/link" target="_blank">this link.</a>

## Linking to Dynamic Segments

```js
import Link from 'next/link'

const users = [
  {
    id: '1',
    name: 'amir'
  },
  {
    id: '2',
    name: 'ali'
  },
  {
    id: '3',
    name: 'maryam'
  },
  {
    id: '4',
    name: 'zahra'
  },
]

export default function Users() {
  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>
          <Link href={`/users/${user.id}`}>{user.name}</Link>
        </li>
      ))}
    </ul>
  )
}
```

## `useRouter()` Hook

The useRouter hook allows you to programmatically change routes inside `Client Components`.
To use `useRouter`, import it from `next/navigation`, and call the hook inside your Client Component:

```js
'use client'

import { useRouter } from 'next/navigation'

export default function Home() {
  const router = useRouter()
  return <>
    <h1>Welcome home!</h1>
    <button type="button" onClick={() => router.push('/users')}>
      Users
    </button>
  </>
}
```

> 💡 for more information about `useRouter` component
> see <a href="https://nextjs.org/docs/app/api-reference/functions/use-router" target="_blank">this link.</a>

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/05-linking-and-navigating/app" target="_blank">Click here to watch state of project.</a>

