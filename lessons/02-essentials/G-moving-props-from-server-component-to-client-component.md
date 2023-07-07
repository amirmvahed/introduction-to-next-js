## Moving props from server component to client component

&nbsp;
&nbsp;
&nbsp;

Props passed from the Server to Client Components need to
be <a href="https://developer.mozilla.org/en-US/docs/Glossary/Serialization" target="_blank">"serializable"</a>. This
means that values such as functions,
Dates, etc, cannot be passed directly to Client Components.

&nbsp;
&nbsp;
&nbsp;

when you are moving data from the server component to the client component, you have to pay attention to your
performance.

&nbsp;
&nbsp;
&nbsp;

when you pass props to your client component from the server component, this data has been created on the server and
will send as a data with your page.

&nbsp;
&nbsp;
&nbsp;

so if your data is too big, your bundle will increase.

&nbsp;
&nbsp;
&nbsp;

```js
// Profile is a Client Component
import Profile from './Profile'

// Layout is a Server Component by default
export default async function Layout({ children }) {
  const res = await fetc('/user')
  const firstName = await res.json().firsName // If this is 1mb, the data sent to the client will also be 1mb.

  return (
    <>
      <nav>
        <Profile firstName={firstName}/>
      </nav>
      <main>{children}</main>
    </>
  )
}
```




