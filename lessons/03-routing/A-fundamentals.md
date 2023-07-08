## Terminology

we have some definitions:
![tree](./images/routing/tree.png)
+ **Tree**: A convention for visualizing a hierarchical structure. For example, a component tree with parent and children components, a folder structure, etc.
+ **Subtree**: Part of a tree, starting at a new root (first) and ending at the leaves (last).
+ **Root**: The first node in a tree or subtree, such as a root layout.
+ **Leaf**: Nodes in a subtree that have no children, such as the last segment in a URL path.

&nbsp;
&nbsp;
&nbsp;

![tree](./images/routing/url.png)
+ **URL Segment**:  Part of the URL path delimited by slashes.
+ **URL Path**: Part of the URL that comes after the domain (composed of segments).


## File based routing

Next.js uses file-based routing. This means, instead of configuring a router yourself like you would with react-router
, you follow a set of folder and file naming conventions and Next.js will configure the router for
you. It's really magical.

&nbsp;
&nbsp;
&nbsp;

## The `app` Router

The App Router works in a new directory named `app`. The `app` directory works alongside the pages directory to allow for
incremental adoption. This allows you to opt some routes of your application into the new behavior while keeping other
routes in the `pages` directory for previous behavior.

> 💡 for more information about `pages` folder see <a href="https://nextjs.org/docs/pages/building-your-application/routing" target="_blank">this link.</a>

