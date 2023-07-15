## Static and Dynamic data rendering

&nbsp;
&nbsp;
&nbsp;

During static rendering, if a `dynamic function` or a `dynamic fetch()` request `(no caching)` is discovered, Next.js
will
switch to `dynamically rendering` the whole route at request time.

&nbsp;
&nbsp;
&nbsp;

![static-and-dynamic-rendering](./images/rendering-and-data-fetching/static-and-dynamic-rendering.png)

&nbsp;
&nbsp;
&nbsp;

Note how dynamic functions always opt the route into dynamic rendering, regardless of whether the data fetching is
cached or not. In other words, static rendering is dependent not only on the data fetching behavior, but also on the
dynamic functions used in the route.

> + Static render = `SSG` (Static Site Generation)
> + Revalidate fetch = `ISR` (Incremental Static Regeneration)
> + Dynamic render = `SSR` (Server Side Rendering)