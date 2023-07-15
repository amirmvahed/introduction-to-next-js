# Data fetching patterns

&nbsp;
&nbsp;
&nbsp;

When fetching data inside components, you need to be aware of two data fetching patterns: `Parallel` and `Sequential`.

&nbsp;
&nbsp;
&nbsp;

![parallel-and-sequential-data-fetching](./images/rendering-and-data-fetching/parallel-and-sequential-data-fetching.png)

&nbsp;
&nbsp;
&nbsp;

## Parallel Data Fetching

With `parallel` data fetching, requests in a route are eagerly initiated and will load data at the `same time`. This
reduces
client-server waterfalls and the total time it takes to load data.

```js
import {getUser} from "@/requests/getUser";
import {getUserAlbums} from "@/requests/getUserAlbums";

export default async function UserDetail({params}) {
  const userRes = getUser(params['userId']) // it takes 5 sec.
  const userAlbumsRes = getUserAlbums(params['userId']) // it takes 3 sec.

  const [userData, albumsData] = await Promise.all([userRes, userAlbumsRes]) // it takes 5 sec (instead of 8 sec)

  const [user] = userData


  return <>
    <h1>User Page</h1>
    <div>
      <h2>User details: </h2>
      <h3>{user.name}</h3>
      <p>{user.email}</p>
    </div>
    <hr/>
    <div>
      <h2>User albums: </h2>
      {albumsData.map(album => {
        return (
          <div>
            <h3>{album.title}</h3>
          </div>
        )
      })}
    </div>
  </>
}
```

By starting the fetch prior to calling `await` in the Server Component, each request can eagerly start to fetch requests
at the `same time`. This sets the components up, so you can avoid waterfalls.

We can save time by initiating both requests in parallel, however, `the user won't see the rendered result until both promises are resolved`.

To improve the user experience, you can add a `suspense boundary` to break up the rendering work and show part of the result as soon as possible:

```js
import {Suspense} from 'react'
import {getUser} from "@/requests/getUser";
import {getUserTodos} from "@/requests/getUserTodos";

export default async function UserTodos({params}) {
    const userRes = getUser(params['userId'])
    const todosRes = getUserTodos(params['userId'])

    const [user] = await userRes

    return (
        <>
            <h1>User Todos page</h1>
            <h2>{user.name}</h2>
            <h3>{user.email}</h3>
            <hr/>
            <div>
                <h2>User todos</h2>
                {/* Send the todos information first, and wrap todos in a suspense boundary */}
                <Suspense fallback={<h1>Loading...</h1>}>
                    <Todos promise={todosRes}/>
                </Suspense>
            </div>
        </>
    );
}


async function Todos({promise}) {
    // Wait for the todos promise to resolve
    const todos = await promise

    return (
        <ul>
            {todos.map((todo) => (
                <li style={{backgroundColor: todo['completed'] ? 'lightgreen' : 'red'}} key={todo.id}>{todo.title}</li>
            ))}
        </ul>
    )
}
```

&nbsp;
&nbsp;
&nbsp;

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/09-data-fetching-patterns-parallel/app" target="_blank">Click here to watch state of project.</a>    

&nbsp;
&nbsp;
&nbsp;

## Sequential Data Fetching

With `sequential` data fetching, `requests in a route are dependent on each other` and create `waterfalls`. There may be
cases
where you want this pattern because one fetch `depends on the result of the other`, or you want a condition to be
satisfied before the next fetch to save resources. However, this behavior can also be unintentional and lead to longer
loading times.

```js
import {Suspense} from 'react'
import {getUserPosts} from "@/requests/getUserPosts";
import {getPostComments} from "@/requests/getPostComments";

export default async function UserPost({params}) {
    const userFirstPost = await getUserPosts(params['userId'])
    const postData = userFirstPost[0]

    return (
        <>
            <h1>{postData.title}</h1>
            <p>{postData.body}</p>
            <hr/>
            <Suspense fallback={<div>Loading...</div>}>
                <Comments postId={postData.id} />
            </Suspense>
        </>

    );
}
async function Comments({ postId }) {
    // Wait for the comments
    const postComments = await getPostComments(postId)

    return (
        <ul>
            {postComments.map((comment) => (
                <li key={comment.id}>{comment.body}</li>
            ))}
        </ul>
    )
}
```

&nbsp;
&nbsp;
&nbsp;

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/10-data-fetching-patterns-sequential/app" target="_blank">Click here to watch state of project.</a>    
