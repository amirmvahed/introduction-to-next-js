# Dynamic functions

&nbsp;
&nbsp;
&nbsp;

Dynamic functions rely on information that can only be known at `request time` such as a user's `cookies`, current
requests
headers, or the URL's search params. In Next.js, these dynamic functions are:

> + Using `cookies()` or `headers()` in a **`Server Component`** will opt the whole route into dynamic rendering at
    request time.
> + Using `useSearchParams()` in **`Client Components`** will skip static rendering and instead render all Client
    Components up
    to the nearest parent Suspense boundary on the client.

## cookies()

The cookies function allows you to read the HTTP incoming request cookies from a Server Component or write outgoing
request cookies in a Server Action.

```js
import { cookies } from 'next/headers'

export default function Page() {
  const cookieStore = cookies()
  const isDark = cookieStore.get('isDark')
  console.log(isDark)
}
```

> 💡 for read more information about
> `cookies()` <a href="https://nextjs.org/docs/app/api-reference/functions/cookies" target="_blank">visit this link.</a>

## headers()

The headers function allows you to read the HTTP incoming request headers from a Server Component.

This API extends the Web Headers API. It is `read-only`, meaning you cannot set / delete the outgoing request headers.

```js
import { headers } from 'next/headers'

export default function Page() {
  const headersList = headers()
  const referer = headersList.get('referer')
  console.log(referer)
}
```

> 💡 for read more information about
> `headers()` <a href="https://nextjs.org/docs/app/api-reference/functions/headers" target="_blank">visit this link.</a>

## useSearchParams()

`useSearchParams` is a `Client Component` hook that lets you read the current URL's `query` string.
`useSearchParams` does not take any parameters.

```js
'use client'

import { useSearchParams } from 'next/navigation'

export default function Docs() {
  const searchParams = useSearchParams()

  const search = searchParams.get('search')

  // URL -> `/docs?search=project`
  // `search` -> 'project'
  console.log(search)
}
```

> 💡 for read more information about
> `useSearchParams()` <a href="https://nextjs.org/docs/app/api-reference/functions/use-search-params" target="_blank">
> visit this link.</a>

## searchParams (page.js)

An object containing the `search parameters` of the current URL. For example:

```js
export default function Users({ params, searchParams }) {
  // URL -> `/users?search=project`
  // searchParams = {search: project}
  console.log(searchParams)
}
```