## Data fetching

The Next.js App Router allows you to fetch data directly in your `React components` by marking the function as `async`
and
using `await` for the Promise.

```js
async function getUsers() {
  const res = await fetch('https://jsonplaceholder.typicode.com/users')

  if (!res.ok) {
    // This will activate the closest `error.js` Error Boundary
    throw new Error('Failed to fetch users')
  }

  return res.json()
}

export default async function Users() {
  const users = await getUsers()

  return (
    <ul>
      {users?.map((user) => (
        <li key={user.id}>
          <Link href={`/users/${user.id}`}>{user.name}</Link>
        </li>
      ))}
    </ul>
  )
}
```

> 💡 for read more information about
> `error.js` <a href="https://nextjs.org/docs/app/api-reference/file-conventions/error" target="_blank">
> visit this link.</a>


> By default, fetch will automatically fetch and `cache` data indefinitely.

```js
fetch('https://...') // cache: 'force-cache' is the default
```

## Revalidating data

> To revalidate cached data at a timed interval, you can use the `next.revalidate` option in `fetch()` to set
> the `cache`
> lifetime of a resource (in seconds).

```js
fetch('https://...', { next: { revalidate: 10 } })
```

If you want to revalidate data that `does not use fetch` (i.e. using an external package or query builder), you can use
the route segment config.

```js
export const revalidate = 60 // revalidate this page every 60 seconds
```

#### **How it works**

+ When a request is made to the route that was statically rendered at build time, it will initially show the cached
  data.
+ Any requests to the route after the initial request and before 60 seconds are also cached and instantaneous.
+ After the 60-second window, the next request will still show the cached (stale) data.
+ Next.js will trigger a regeneration of the data in the background.
+ Once the route generates successfully, Next.js will invalidate the cache and show the updated route. If the background
  regeneration fails, the old data would still be unaltered.

> Do you know about <a href="https://nextjs.org/docs/app/building-your-application/data-fetching/revalidating#on-demand-revalidation" target="_blank">
> `on-demand revalidation`</a>?

## Dynamic Data Fetching

To fetch fresh data on every fetch request, use the `cache: 'no-store'` option.

```js
fetch('https://...', { cache: 'no-store' })
```
> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/08-data-fetching/app" target="_blank">Click here to watch state of project.</a>

