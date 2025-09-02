Q.What is NextJs?
Next.js is a React framework that enables server-side rendering, static site generation, and client-side rendering, providing features like automatic routing, API routes, image optimization, and performance enhancements out of the box

Q.What is the advantage of NextJs?
Advantages of Next.js

1.Server-Side Rendering (SSR) & Static Site Generation (SSG): Improves SEO and initial load performance.
2.File-Based Routing: Easy to create routes with pages or app folder structure.
3.API Routes: Can create backend endpoints without a separate server.
4.Performance Optimizations: Automatic code splitting, image optimization, and caching.
5.Incremental Static Regeneration (ISR): Lets static pages update after deployment without a full rebuild.

Q.What is the disadvantage of NextJS?
Disadvantages of Next.js

1.Learning Curve: Advanced features like SSR, SSG, ISR, and API routes can be tricky for beginners.
2.Server Costs for SSR: SSR requires a server environment, which may increase hosting costs.
3.Build Time for Large Sites: Static generation of many pages can take longer in big projects.
4.Opinionated Structure: File-based routing may feel restrictive for some complex projects.
5.Limited Control Over Some Optimizations: Some automatic optimizations may require workarounds to customize.

Q.What is the difference between React and Next.js?
React is a JavaScript library for building user interfaces. It only handles the view layer, so for routing, data fetching, and server-side rendering, we need to use additional libraries like React Router or custom setups.

Next.js, on the other hand, is a full-stack React framework. It is built on top of React but provides many features out of the box such as file-based routing, server-side rendering (SSR), static site generation (SSG), incremental static regeneration (ISR), API routes, image optimization, and built-in performance optimizations.

React is just the UI library, while Next.js is a framework built on top of React that adds routing, data fetching, SSR, SSG, ISR, and optimizations for building full-stack, production-ready applications.

Q.What is SSR?
SSR stands for Server-Side Rendering. In this approach, the HTML of the page is generated on the server at request time. So, whenever a user requests a page, the server fetches the required data, prepares the HTML with content, and then sends it back to the client.

The advantage of SSR is that the user and search engines get a fully rendered page immediately, which improves SEO and first page load performance. It’s very useful when the data changes frequently or the page needs to be personalized, for example in dashboards, user profiles, or e-commerce product pages.

But the downside is that it’s slower than static generation, because the server has to process every request, and it also puts more load on the backend. That’s why we usually use caching or CDN to optimize SSR.

Q.What is SSG (Static Site Generation)?
SSG stands for Static Site Generation. In this approach, the HTML pages are generated at build time instead of at request time. That means when I build my Next.js application, the server fetches all the required data once, pre-renders the HTML files, and then those static pages are deployed on a CDN.

Because the pages are static, they are extremely fast to load and also SEO-friendly, since search engines can crawl the pre-rendered HTML directly. This makes SSG ideal for content that doesn’t change often, like blogs, documentation sites, landing pages, or marketing websites.

The main drawback is that if the data changes frequently, the page won’t automatically update until I rebuild the project. To solve that, Next.js provides ISR (Incremental Static Regeneration), which allows us to update static pages after deployment without rebuilding the entire app.

Q.What is CSR (Client-Side Rendering)?
CSR stands for Client-Side Rendering. In this approach, the browser first loads a very minimal HTML file with a JavaScript bundle. Then React takes over on the client side, fetches the required data through APIs, and renders the UI dynamically in the browser.

The advantage of CSR is that it provides a smooth single-page application experience, with fast client-side navigation after the first load. It also reduces load on the server because most of the rendering happens in the browser.

However, the drawback is that the initial page load can be slower, since the user sees a blank page until JavaScript is downloaded and executed. It also impacts SEO negatively, because search engines may not see the content immediately.

CSR is a good choice for applications where SEO is not a priority, like dashboards, admin panels, or internal tools. In Next.js, CSR is usually implemented by using hooks like useEffect to fetch data on the client side, instead of using getStaticProps or getServerSideProps.

Q.What is ISR?
ISR stands for Incremental Static Regeneration. It’s a feature in Next.js that combines the benefits of SSG and SSR. Normally in SSG, pages are generated only at build time, which means if the data changes, I have to rebuild the whole app. With ISR, we can regenerate static pages after the site is deployed, without doing a full rebuild.

Basically, I can set a revalidate time inside getStaticProps. This tells Next.js to serve the existing static page immediately, but also regenerate it in the background after the revalidate interval has passed. That way, the user always sees fast, cached content, and the page automatically updates with fresh data when needed.

The big advantage of ISR is that it gives the performance of static pages with the freshness of server-rendered pages. It’s very useful for e-commerce sites, blogs, or news portals where data changes but not every second.

So, I’d say ISR helps us scale easily with CDN delivery, while still keeping the content up to date.


Q.What is App Routing?
In Next.js 13 and above, App Routing is the new routing system introduced with the App Router. It is built on top of the React Server Components architecture. Instead of using the pages directory, we now create routes inside the app directory.

Each folder inside the app directory becomes a route, and the special file page.js (or page.tsx) inside that folder defines the UI for that route. For example, if I have app/dashboard/page.js, it will be available at /dashboard

App Routing also introduces powerful conventions like:

layout.js → for persistent layouts across routes,
loading.js → for built-in loading states,
error.js → for error handling per route,
not-found.js → for 404 handling.

The big advantage of App Routing is that it gives us nested layouts, server and client components, streaming, and better data fetching with React Suspense.

Q.What is Page routing?
n Next.js, Page Routing is the older routing system that uses the pages directory. Every file inside the pages folder automatically becomes a route based on its file name. For example, pages/index.js becomes /, and pages/about.js becomes /about.

It also supports dynamic routes using square brackets. For example, if I create pages/blog/[id].js, it can handle routes like /blog/1 or /blog/2.

With Page Routing, data fetching is done using functions like getStaticProps, getServerSideProps, and getStaticPaths.

The advantage of Page Routing is that it’s simple and easy to understand, but the limitation is that it doesn’t support advanced features like nested layouts, React Server Components, streaming, or fine-grained loading states, which are available in the new App Routing system.

Q.What is the difference between app vs page route?
Next.js provides two types of routing systems: Page Routing and App Routing.

Page Routing is the older system that uses the pages directory. Each file becomes a route, and we use data-fetching methods like getStaticProps, getServerSideProps, and getStaticPaths. It’s very simple and easy to use, but has limited flexibility.

App Routing is the newer system introduced in Next.js 13. It uses the app directory, where folders define routes and special files like page.js, layout.js, loading.js, and error.js provide advanced features. It’s built on top of React Server Components and supports nested layouts, streaming, partial rendering, and better data-fetching patterns.

Q.What is File based routing
File-based routing means that the file and folder structure inside the project directly maps to the routes of the application. Instead of manually configuring routes, the framework automatically creates them based on the file names.
For example, in Next.js, if I create a file pages/about.js, it automatically becomes the /about route. If I create pages/blog/[id].js, it becomes a dynamic route that can handle /blog/1, /blog/2, and so on.
This makes routing very intuitive because the developer can simply look at the folder structure and understand the routes of the application.

Q.What is the purpose of the pages directory vs the app directory?
The purpose of the pages directory is to provide a simple, file-based routing system. Every file becomes a route automatically, and it allows us to implement SSR, SSG, and CSR with functions like getServerSideProps and getStaticProps. It was designed to make routing easy without extra configuration.

The purpose of the app directory is to introduce a more powerful and flexible routing system. It’s built on React Server Components and gives us advanced features like nested layouts, loading and error states, streaming, and better data-fetching patterns. The idea is to solve the limitations of the old pages system and make applications more scalable and optimized.

Q. How do you create dynamic routes in Next.js?

In Next.js, dynamic routes are created by using square brackets in the file name inside the pages or app directory. For example, creating a file called pages/blog/[id].js allows handling routes like /blog/1, /blog/2, etc. In the pages directory, we also use getStaticPaths along with getStaticProps to generate static pages for dynamic routes.

Q. What is the role of the Link component in Next.js?

The Link component in Next.js is used for client-side navigation between routes. It prevents full page reloads and makes the navigation faster by prefetching the page content in the background. This improves performance and gives a smoother single-page application experience.

Q.How is navigation different in Next.js compared to React Router?

In React Router, we have to manually configure routes and use components like Route and Switch, while in Next.js routing is file-based, meaning the folder and file structure defines the routes automatically. For navigation, Next.js uses the Link component with prefetching, while React Router uses Link or NavLink without automatic prefetching. This makes Next.js navigation faster and more SEO-friendly.

Q. How do you implement SSR in Next.js?

In Next.js, SSR is implemented using the getServerSideProps function. This function runs on the server at request time, fetches the data, and passes it as props to the page. Every time a user visits the page, the server generates the HTML with fresh data and sends it to the browser.

Q. How do you implement SSG in Next.js?

In Next.js, SSG is implemented using the getStaticProps function. This function runs at build time, fetches the data, and pre-renders the HTML as a static file. The page is then served from the CDN, making it very fast. For dynamic routes, getStaticPaths is also used to define which paths should be generated at build time.

Q. How do you implement ISR in Next.js?

In Next.js, ISR is implemented by using getStaticProps with a revalidate property. The page is first generated at build time, and then after the revalidate time has passed, Next.js regenerates the page in the background with fresh data. This way, the page stays fast like SSG but also updates periodically like SSR.

Q. What is hydration in Next.js?

Hydration in Next.js is the process where the server-rendered HTML is sent to the browser and then React attaches event listeners and makes the page interactive. Initially, the user sees the static HTML, and once JavaScript loads, React hydrates the page so that it behaves like a React app.

Q. What are getStaticProps, getServerSideProps, and getStaticPaths?

getStaticProps is used for static site generation where data is fetched at build time. getServerSideProps is used for server-side rendering where data is fetched at request time for every user request. getStaticPaths is used along with getStaticProps for dynamic routes, where it defines which paths should be pre-rendered at build time.


Q. What are server components vs client components?

Server components are components that run only on the server and never get sent as JavaScript to the client. They are faster, smaller, and more secure since sensitive logic stays on the server. Client components run in the browser and include interactivity like event handling, state management, or hooks such as useState and useEffect. In Next.js, by default, components are server components, and if we need client-side behavior, we mark them with "use client" at the top.

Q. What is the role of layout.js in App Routing?

The layout.js file is used to define a layout for a specific route in the app directory. It allows us to create nested layouts where the layout is shared across multiple pages. For example, a dashboard layout with a sidebar and header can wrap multiple dashboard pages without repeating the same code. Layouts persist across navigation, which improves performance and user experience.

Q. What is the role of loading.js, error.js, and not-found.js?

The loading.js file is used to show a loading state while a page or data is being fetched. The error.js file is used to handle errors for a specific route and display a custom error UI. The not-found.js file is used to show a custom 404 page when a route or resource is not found. These files provide better user experience by handling different states gracefully.

Q. What are parallel routes and intercepting routes?

Parallel routes allow us to render multiple pages or UI segments in parallel within the same layout. This is useful for cases like dashboards where we want different sections to load independently. Intercepting routes allow us to load a different version of a route depending on the context. For example, opening a chat in a modal instead of a full page without breaking navigation.

Q. How does data fetching work in the app directory?

In the app directory, data fetching is built on React Server Components. We can fetch data directly inside server components using async/await without extra hooks. Next.js also supports streaming and Suspense, so pages can render progressively as data loads. This provides faster performance compared to the pages directory data fetching methods.

Q. What are React Server Components and why are they used in Next.js?

React Server Components are components that render on the server and send only the rendered HTML to the client. They do not include JavaScript in the client bundle, which makes the app faster and reduces bundle size. They are used in Next.js to improve performance, enable better caching, and keep sensitive logic on the server. By combining server and client components, Next.js gives both speed and interactivity.

Q. How does Next.js optimize performance compared to React?

Next.js optimizes performance by providing server-side rendering, static site generation, and incremental static regeneration out of the box. It also automatically code-splits pages, optimizes images and fonts, supports caching, and uses React Server Components for smaller bundles. These features reduce load time and improve SEO compared to plain React apps, which rely only on client-side rendering.

Q. What is image optimization in Next.js and how does next/image work?

Image optimization in Next.js ensures images load faster and are responsive across devices. The next/image component automatically optimizes images by resizing, compressing, and serving them in modern formats like WebP. It also supports lazy loading, meaning images load only when they are in the viewport, which improves page speed.

Q. What is font optimization in Next.js?

Font optimization in Next.js helps reduce layout shifts and improves performance by automatically downloading and serving only the fonts actually used on the page. With next/font, Google Fonts and local fonts can be optimized at build time, and the fonts are served with the app instead of fetching them from external servers.

Q. What is code splitting and how does Next.js handle it?

Code splitting is the process of breaking the JavaScript bundle into smaller chunks so that the browser only loads what is needed. Next.js automatically performs code splitting at the page level, meaning each page loads only the code it needs instead of the entire app. This makes the initial load much faster.

Q. How does Next.js support lazy loading and dynamic imports?

Next.js supports lazy loading with dynamic imports. By using the dynamic() function, we can import components only when they are needed instead of including them in the initial bundle. This reduces page size and improves performance, especially for heavy components like charts or modals.

Q. What is static optimization in Next.js?

Static optimization means that Next.js automatically pre-renders pages as static HTML at build time when no server-side data is required. If a page does not use getServerSideProps, it is automatically considered static and optimized for performance. These static pages can be cached on a CDN for very fast loading.

Q. What is middleware in Next.js and how do you use it?

Middleware in Next.js is code that runs before a request is completed. It allows us to intercept requests and perform actions like authentication, redirects, logging, or feature flags. Middleware is placed in a middleware.js file at the root or inside specific folders, and it runs on the Edge, making it very fast.

Q. What is server-side streaming in Next.js?
Server-side streaming in Next.js allows the server to send parts of the HTML to the browser as soon as they are ready instead of waiting for the full page to render. This makes the page load faster and gives the user a better experience because they see content sooner while the rest of the page continues to load.

Q. What are React Suspense and streaming in Next.js?
React Suspense lets us pause rendering while waiting for data or components to load, and then show a fallback like a loader. Streaming in Next.js works with Suspense to progressively send UI chunks from the server to the client. Together, they make apps faster by avoiding long blank screens and showing parts of the page as they are ready.

Q. What are middlewares in Next.js and when would you use them?
Middlewares in Next.js are functions that run before a request is completed. They are useful for authentication, redirects, logging, feature flags, and request modification. For example, you can check if a user is logged in before allowing them to access a protected page.

Q. How does Next.js handle authentication and authorization?
Next.js handles authentication by combining API routes, middleware, and libraries like NextAuth.js or JWT. Authentication verifies the user’s identity, while authorization checks their permissions. Middleware can protect routes, and API routes can validate tokens before sending sensitive data.

Q. What is Edge Rendering in Next.js?
Edge Rendering means running parts of the app on servers that are closer to the user, called edge servers. This reduces latency and speeds up response times. Next.js supports Edge Rendering with middleware and edge functions, making it great for things like personalization and A/B testing.

Q. How do you secure API routes in Next.js?
API routes in Next.js can be secured by validating authentication tokens, using middleware for checks, setting proper CORS policies, and limiting sensitive operations to authorized users only. Often, JWT or session-based authentication is used to ensure only valid users can access protected APIs.

Q. What are some advantages and disadvantages of using Next.js in production?
Advantages of Next.js include built-in support for SSR, SSG, ISR, API routes, image optimization, file-based routing, and great performance for SEO and user experience. It also supports edge rendering and React Server Components.
Disadvantages include a learning curve for beginners, more complex setup compared to plain React, larger bundle sizes if not optimized, and reliance on Node.js for server features.

