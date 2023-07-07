## Single Page Application

Before we look at what RSC is and how it relates to SSR, it helps to understand how Single-Page Applications (SPA) work.
To that end, let’s use the example of a simple application, which I have named Personal Assistant. This
app has two pages, namely tasks, and reminders. The tasks page shows you a list of tasks and has a button. The button
when clicked shows you a modal that you can use to add a task. The reminders page shows you a list of reminders and has
a button with similar functionality. The tasks page is the default page, so when you open the app, that is the first
page you see.

![my-app](./images/essentials/my-example.png)
&nbsp;
&nbsp;
&nbsp;

**Single-Page Application (SPA)**
&nbsp;
&nbsp;

Now, let’s see how this application works when it is a SPA. First, a user would enter the URL of this application into
the address bar of a browser and hit enter. Then, the browser would send a request to the server that serves this
application. The server would respond with an HTML file and a JavaScript bundle. The HTML file is just a scaffolding
with the html, head, and body tags with a root div tag to render the application. The JavaScript bundle contains the
code to render the application and add interactivity.

The browser would then render the tasks page and dispatch an API request to fetch the list of tasks. Once the browser
gets the list of tasks, it renders the list on the screen as per the JavaScript code. If the user navigates to the
reminders page, then the browser renders the reminders page and sends an API request to fetch the list of reminders.
Once the browser receives the response, it renders the list of reminders.

![SPA](./images/essentials/spa-1.png)
![client-side-rendering](./images/essentials/client-side-rendering.png)
&nbsp;
&nbsp;
&nbsp;

**The drawbacks of SPA**
&nbsp;
&nbsp;

As you can see, both rendering and data fetching take place in the browser itself. Since the rendering takes place in
the browser entirely, the server has to send the JavaScript code for the entire app to the browser. This means the
**JavaScript bundle is going to be huge** and downloading it is going to take longer. This results in the First Contentful
Paint (FCP) taking longer affecting the user experience. In other words, **the user will have to wait for some time before
they see any content on their screen**. Besides, when the browser fetches data, the user’s internet connection is going to
decide how fast the data is going to be painted on the screen. In addition, the API requests from the browser go through
public networks and hence, are going to be comparatively **slower**.

