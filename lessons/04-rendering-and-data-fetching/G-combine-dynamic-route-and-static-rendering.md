# Combine dynamic route and static rendering

As you can see our `users` pages are dynamic`(will render at request time)`. how we can make it `static`?

## generateStaticParams()

The `generateStaticParams` function can be used in combination with `dynamic route segments` to `statically generate`
routes
at build time instead of on-demand at request time.

&nbsp;
&nbsp;
&nbsp;

add this to `/app/users/[userId]/page`:

```js
// Return a list of `params` to populate the [userId] dynamic segment
export async function generateStaticParams() {
  const users = await getUsers()

  return users.map((user) => ({
    userId: String(user.id)
  }))
}
```

> 💡 for more information about `generateStaticParams`
> visit <a href="https://nextjs.org/docs/app/api-reference/functions/generate-static-params" target="_blank">this
> link.</a>

&nbsp;
&nbsp;
&nbsp;

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/11-combine-dynamic-route-and-static-rendering/app" target="_blank">
> Click here to watch state of project.</a>    
