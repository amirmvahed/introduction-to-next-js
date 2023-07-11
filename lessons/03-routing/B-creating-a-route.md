## Creating a route

+ Inside the `app` folder, create a `page.js` file. This file represents the route.
+ Define a simple React component in the `page.js` file, to represent the “Home” page:

```js
export default function Home() {
  return <h1>Welcome home!</h1>;
}
```

By following these conventions, we've successfully created our first route. Open your browser and navigate to <a
href="http://localhost:
3000" target="_blank">localhost:3000</a> to see the "Welcome home!" message.

## Adding additional routes

Let's now proceed to create one more routes: About page.

+ Create an `app/about` folder.
+ Inside the `about` folder, create a `page.js` file. This file represents the route.
+ Define a minimal React component in the page.js file to represent the "About" page:

```js
export default function About() {
  return <h1>About Page</h1>;
}
```

> When you visit the root URL, <a href="http://localhost:3000" target="_blank">localhost:3000</a>, the home page will
> still
> be displayed. However, if you navigate to
> <a href="http://localhost:3000/about" target="_blank">localhost:3000/about</a>, you will see the About page.

This demonstrates that routes are associated with a file based on the containing folder's name within the `app` folder.
The `page.js` file within the `app` folder corresponds to `/`, while the `page.js` file within the `about` folder
corresponds to `/about`.

## Handling non-matching routes

What happens if you enter a URL that cannot map to a file within the app folder? For
example, <a href="http://localhost:3000/dashboard" target="_blank">localhost:3000/dashboard</a>. Next.js will
automatically respond with a `404 Not Found` response. You don't have to explicitly handle non-matching routes, as
Next.js takes care of this for you.

> 💡 You can create your custom not-found page and give more information
> with <a href="https://nextjs.org/docs/app/api-reference/file-conventions/not-found" target="_blank">this link</a>


> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/01-creating-a-route/app" target="_blank">Click here to watch state of project.</a>