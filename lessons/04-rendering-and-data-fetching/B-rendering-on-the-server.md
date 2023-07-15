# Rendering on the server

In addition to client-side and server-side rendering with React components, Next.js gives you the option to optimize
rendering on the server with Static and Dynamic Rendering.

## Static Rendering

With Static Rendering, both Server and Client Components can be pre-rendered on the server at `build time`. The result
of
the work is `cached` and reused on subsequent requests. The cached result `can also be revalidated`.

> 💡 This is equivalent to Static Site Generation `(SSG)` and Incremental Static Regeneration `(ISR)` in
> the <a href="https://nextjs.org/docs/pages/building-your-application/routing" target="_blank">Pages Router.</a>

## Dynamic Rendering
With Dynamic Rendering, both Server and Client Components are rendered on the server at `request time`. The result of the work `is not cached`.

> 💡 This is equivalent to Server-Side Rendering `(getServerSideProps())` in the <a href="https://nextjs.org/docs/pages/building-your-application/routing" target="_blank">Pages Router.</a>



