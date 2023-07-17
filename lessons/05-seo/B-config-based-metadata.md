# Metadata Object and generateMetadata Options

## The metadata object

To define static `metadata`, export a Metadata object from a `layout.js` or `page.js` file.

```js
export const metadata = {
  title: '...',
  description: '...',
}

export default function Page() {
}
```

&nbsp;
&nbsp;
&nbsp;

### Basic Fields

```js
export const metadata = {
  generator: 'Next.js',
  applicationName: 'Next.js',
  referrer: 'origin-when-cross-origin',
  keywords: ['Next.js', 'React', 'JavaScript'],
  authors: [{ name: 'Seb' }, { name: 'Josh', url: 'https://nextjs.org' }],
  colorScheme: 'dark',
  creator: 'Jiachi Liu',
  publisher: 'Sebastian Markbåge',
  formatDetection: {
    email: false,
    address: false,
    telephone: false,
  },
}
```

&nbsp;
&nbsp;
&nbsp;

Output(head):

```html

<meta name="application-name" content="Next.js" />
<meta name="author" content="Seb" />
<link rel="author" href="https://nextjs.org" />
<meta name="author" content="Josh" />
<meta name="generator" content="Next.js" />
<meta name="keywords" content="Next.js,React,JavaScript" />
<meta name="referrer" content="origin-when-cross-origin" />
<meta name="color-scheme" content="dark" />
<meta name="creator" content="Jiachi Liu" />
<meta name="publisher" content="Sebastian Markbåge" />
<meta name="format-detection" content="telephone=no, address=no, email=no" />
```

> 💡 for more information about `Metadata Fields`
> visit <a href="https://nextjs.org/docs/app/api-reference/functions/generate-metadata#metadata-fields" target="_blank">
> this
> link.</a>

&nbsp;
&nbsp;
&nbsp;

## `generateMetadata` function

Dynamic metadata depends on **dynamic information**, such as the current route parameters, external data, or `metadata`
in parent segments, can be set by exporting a `generateMetadata` function that returns a `Metadata object`.

&nbsp;
&nbsp;
&nbsp;

in user page:

```js
export async function generateMetadata({ params }) {
  const userData = await getUser(params['userId']) //deduped!
  const user = userData.pop()
  return {
    title: user.name
  }
}
```

&nbsp;
&nbsp;
&nbsp;

> + The `metadata` object and `generateMetadata` function exports are only supported in `Server Components`.
> + You cannot export both the `metadata` object and `generateMetadata` function from the same route segment.

&nbsp;
&nbsp;
&nbsp;

> 💻 <a href="https://github.com/amirmvahed/next-dk-code/tree/12-seo/app" target="_blank">
> Click here to watch state of project.</a>    