## Nested routes

In addition to basic routes, Next.js offers support for `nested routes`, so you can establish a hierarchical structure
within your application. Let’s aim to render a page when the user navigates to the URL `localhost:3000/blog`.
Furthermore,
we need to render pages for `localhost:3000/blog/first` and `localhost:3000/blog/second`.

&nbsp;
&nbsp;
&nbsp;

To implement nested routes, follow these steps:

+ Create a `app/blog` folder.
+ Inside the `blog` folder, create a `page.js` file for the main blog page:

```js
export default function Blog() {
  return <h1>My blog</h1>;
}
```

+ Navigate to <a href="http://localhost:3000/blog" target="_blank">localhost:3000/blog</a> to see the My blog page.
+ To implement `/blog/first` and `/blog/second` routes, create `page.js` files in the `app/blog/first` and
  `app/blog/second` folders:

```js
export default function FirstBlog() {
  return <h1>First blog post</h1>;
}
```

```js
export default function SecondBlog() {
  return <h1>Second blog post</h1>;
}
```

+ Now, navigating to <a href="http://localhost:3000/blog/first" target="_blank">localhost:3000/blog/first</a> displays
  the first blog post, and `/blog/second` shows the second blog post.

&nbsp;
&nbsp;
&nbsp;

By creating a nested folder structure, Next.js automatically routes the files accordingly. This simplifies the process of creating nested routes and enhances the organization and structure of your application.

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/02-nested-routes/app" target="_blank">Click here to watch state of project.</a>