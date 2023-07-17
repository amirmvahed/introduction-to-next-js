# Metadata Files

File-based metadata can be defined by adding special `metadata files` to route segments.

Once a file is defined, Next.js will automatically serve the file (with hashes in production for caching)
and `update the
relevant head` elements with the correct metadata, such as the asset's URL, file type, and image size.

## favicon

Add a `favicon.ico` image file to the root `/app` route segment. The favicon image can only be located in the top level
of `app/`.

&nbsp;
&nbsp;
&nbsp;

Output(head):

```html
<link rel="icon" href="/favicon.ico" sizes="any"/>
```

&nbsp;
&nbsp;
&nbsp;

## opengraph-image

Add an `opengraph-image.(jpg|jpeg|png|gif)` image file to any route segment.

&nbsp;
&nbsp;
&nbsp;

Output(head):

```html
<meta property="og:image" content="<generated>"/>
<meta property="og:image:type" content="<generated>"/>
<meta property="og:image:width" content="<generated>"/>
<meta property="og:image:height" content="<generated>"/>
```

&nbsp;
&nbsp;
&nbsp;

## robots.txt

Add or generate a `robots.txt` file that matches the Robots Exclusion Standard in the root of `app` directory to tell
search engine crawlers which URLs they can access on your site.

&nbsp;
&nbsp;
&nbsp;

### **Static `robots.txt`**

```text
User-Agent: *
Allow: /
Disallow: /private/

Sitemap: https://acme.com/sitemap.xml
```

&nbsp;
&nbsp;
&nbsp;

### **Generate a Robots file**

Add a `robots.js` or `robots.ts` file that returns a Robots object.

```js
export default function robots() {
  return {
    rules: {
      userAgent: '*',
      allow: '/',
      disallow: '/private/',
    },
    sitemap: 'https://acme.com/sitemap.xml',
  }
}
```

&nbsp;
&nbsp;
&nbsp;

Output:

```text
User-Agent: *
Allow: /
Disallow: /private/

Sitemap: https://acme.com/sitemap.xml
```

## sitemap.xml

Add or generate a `sitemap.xml` file that matches the Sitemaps XML format in the root of `app` directory to help search
engine crawlers crawl your site more efficiently.

&nbsp;
&nbsp;
&nbsp;

### **Static `sitemap.xml`**

```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>https://acme.com</loc>
        <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    </url>
    <url>
        <loc>https://acme.com/about</loc>
        <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    </url>
    <url>
        <loc>https://acme.com/blog</loc>
        <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    </url>
</urlset>
```

### **Generate a Sitemap**

Add a `sitemap.js` or `sitemap.ts` file that returns Sitemap.

&nbsp;
&nbsp;
&nbsp;

```js
export default function sitemap() {
  return [
    {
      url: 'https://acme.com',
      lastModified: new Date(),
    },
    {
      url: 'https://acme.com/about',
      lastModified: new Date(),
    },
    {
      url: 'https://acme.com/blog',
      lastModified: new Date(),
    },
  ]
}
```

&nbsp;
&nbsp;
&nbsp;

Output:

```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>https://acme.com</loc>
        <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    </url>
    <url>
        <loc>https://acme.com/about</loc>
        <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    </url>
    <url>
        <loc>https://acme.com/blog</loc>
        <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    </url>
</urlset>
```


