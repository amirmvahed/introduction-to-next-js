## Dynamic Routes

Predefined paths like `/blog/first` and `/blog/second` may not always be suitable for complex applications with hundreds
of routes. Next.js supports dynamic routes to handle such scenarios. Let’s create dynamic routes to handle a product
listing and detail page.

&nbsp;
&nbsp;
&nbsp;

To create dynamic routes, follow these steps:

+ Create a `app/users` folder.
+ Inside the `users` folder, create a `page.js` file to display a list of Users:

```js
export default function Users() {
  return (
    <>
      <h1>Users List</h1>
      <h2>user 1</h2>
      <h2>user 2</h2>
      <h2>user 3</h2>
    </>
  );
}
```

+ By navigating to <a href="http://localhost:3000/users" target="_blank">localhost:3000/users</a> in the browser, the
  list of users displays.
+ For the details page, within the `Users` folder, create a new folder named `[userId]`. The square brackets indicate
  a `dynamic route` segment.
+ Inside the `[userId]` folder, create a `page.js` file:

```js
export default function UserDetail() {
  return <h1>Details about the user</h1>;
}
```

+ Now, when you navigate to <a href="http://localhost:3000/users/1" target="_blank">localhost:3000/users/1</a>, you'll
  see the user details page. Similarly, accessing
  `/users/2`,` /users/3`, or even `/users/100` will display the same details page. `[userId]` is the dynamic route
  segment which can accommodate values like 1, 2, 3 and so on.

&nbsp;
&nbsp;
&nbsp;

To display the specific user ID, you can make use of the params object made available in each page. Modify the component
as follows:

```js
export default function UserDetail({ params }) {
  return <h1>Details about user {params.userId}</h1>;
}
```

+ Now, when you navigate to <a href="http://localhost:3000/users/1" target="_blank">localhost:3000/users/1</a>, the
  details about user 1 display. Similarly, visiting `/users/100` will display details about user 100.

&nbsp;
&nbsp;
&nbsp;

## Nested dynamic routes

we have learned about dynamic routes. Now, let's take it a step further and explore nested dynamic routes.

Complex applications often require multiple dynamic route segments. For instance, when navigating to `/users/1`, the
user expects to see the details for user 1. Similarly, visiting /users/1/todos/1 should display the first todo
for that user. Let's see how we can achieve this using the App Router.

&nbsp;
&nbsp;
&nbsp;

To create nested dynamic routes, follow these steps:

+ Create a `app/users/[userId]/todos` folder. This structure takes us to the route `
  /users/userId/todos` However, we also need a dynamic `todoId`.
+ Within the todos folder, create a new folder named `[todoId]`. Once again, the square brackets indicate a dynamic
  route segment.
+ Inside the `[todoId]` folder, create a `page.js` file where we'll define a React component to display both the
  `userId` and the `todoId`.

```js
export default function TodoDetail({ params }) {
  return (
    <h1>
      todo {params.todoId} for user {params.userId}
    </h1>
  );
}
```

Now, if we navigate to <a href="http://localhost:3000/users/1/todos/1" target="_blank">localhost:
3000/users/1/todos/1</a> in the browser, the expected text displays. Similarly, navigating to `userId` 100 and `todoId`
5 will reflect the corresponding IDs in the UI.

&nbsp;
&nbsp;
&nbsp;

The key takeaway from this section is that it is possible to create nested dynamic routes by having dynamic segments in the folder names.

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/03-dynamic-routes/app" target="_blank">Click here to watch state of project.</a>
