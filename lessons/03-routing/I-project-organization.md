## Project organization

Next.js provides several features to help you organize your project while following routing conventions.

&nbsp;
&nbsp;
&nbsp;

**File colocation**

Each folder in Next.js represents a route segment, but a route is only publicly accessible when a `page.js`
or `page.tsx` file is added to the respective segment.

For example, accessing `localhost:3000/users` with the following folder structure `/app/users/line-chart.js`
will
result in a `404 error` until a `page.js` file is defined. Only the content returned by `page.js` is sent to the client.
Files colocated inside route segments within the app directory won't accidentally become routable.

&nbsp;
&nbsp;
&nbsp;

**Route groups**

Route groups allow logical grouping of routes and files without affecting the URL structure. They can be created by
wrapping a folder in parentheses: `(folderName)`

For example, `(auth)/register` , `(auth)/login` and `(auth)/forgot-password` can be accessed at `/register`, `/login`, and
`/forgot-password`. The auth route group helps organize routes more efficiently.

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/07-project-organization/app" target="_blank">Click here to watch state of project.</a>