# Layouts

A layout is UI that is shared between multiple pages. On navigation, layouts preserve state, remain interactive, and `do
not re-render`. Layouts can also be nested.

You can define a layout by default exporting a React component from a `layout.js` file on `users` folder. The component should accept a
`children` prop that will be populated with a child layout (if it exists) or a child page during rendering.

![layout](./images/routing/layout.png)

```js
import styles from './users.module.css'

export default function UsersLayout({
                                      children, // will be a page or nested layout
                                    }) {
  return (
    <section>
      <nav className={styles.nav}>
        users page
      </nav>

      {children}
    </section>
  )
}
```

&nbsp;
&nbsp;
&nbsp;

## Root Layout

```js
import './global.css'

export default function RootLayout({children}) {
  return (
    <html lang="en">
      <body>
        <nav>Root layout</nav>
        {children}
      </body>
    </html>
  )
}
```

> + A `layout.js` and `page.js` file can be defined in the same folder. The layout will wrap the page.
> + The `top-most` layout is called the Root Layout. This `required` layout is shared across `all pages` in an
    application. Root
    > layouts `must contain html and body` tags.
> + Any route segment can optionally define its `own Layout`. These layouts will be shared across all pages in that
    segment.
> + Layouts in a route are `nested` by default. Each parent layout wraps child layouts below it using the React children
    prop.
> + `Passing data` between a parent layout and its children is not possible. However, you can fetch the same data in a
    route more than once, and React will automatically `dedupe` the requests without affecting performance.
> + Only the `root layout` can contain `<html>` and `<body>` tags.

## Nesting Layouts

Layouts defined inside a folder (e.g. `app/users/layout.js`) apply to specific route segments (e.g.
`mywebsite.com/users`) and render when those segments are active. By default, layouts in the file hierarchy
are `nested`,
which means they wrap child layouts via their children prop.

![nested-layout](./images/routing/nested-layout.png)



> 💡 We have a similar concept that is
> called <a href="https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#templates" target="_blank">`template`</a>
>, it has a little difference in comparison with layout.


> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/06-layouts/app" target="_blank">Click here to watch state of project.</a>

