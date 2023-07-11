## Catch all segments

Next.js provides the catch-all segments feature which allows for flexible routing. Let's say we want to create a
documentation site with multiple features and concepts, where each concept has its own unique route. Instead of creating
separate files for each route, we can use the catch-all segments route.

&nbsp;
&nbsp;
&nbsp;

To implement catch-all segments, follow these steps:

+ Create a `app/docs` folder.
+ Inside the `docs` folder, create a folder with a special name recognized by Next.js. Use square brackets and three
  dots (for example, `[...slug]`) to enclose a name of your choice.
+ Inside the `docs` folder, create a `page.js` file with a basic React component representing the documentation home
  page.

```js
export default function Docs() {
  return <h1>Docs home page</h1>;
}
```

+ create `page.js` file on `[...slug]` folder and use below code for that.
+ To access the different segments in the URL, utilize the params object provided by Next.js. For
  example: `localhost:3000/docs/routing/catch-all-segments` can render the following component:

```js
export default function Doc({ params }) {
  if (params.slug.length === 2) {
    return (
      <h1>
        Viewing docs for feature {params.slug[0]} and concept {params.slug[1]}
      </h1>
    );
  } else if (params.slug.length === 1) {
    return <h1>Viewing docs for feature {params.slug[0]}</h1>;
  }
  return <h1>Doc page</h1>;
}
```

With catch-all segments, you can create a hierarchical structure for your routes, allowing better organization and SEO,
while reusing a single file for different variations of the URL. This approach is particularly useful for documentation
websites.

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/04-catch-all-segments/app" target="_blank">Click here to watch state of project.</a>




