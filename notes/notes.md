# 1 
https://www.youtube.com/watch?v=9P8mASSREYM&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH:
- next js uses react for building UI's but with more features for production ready applications
- So routing, styling, authentication, bundle optimization,etc.
- full stack framework

Features:
- file based routing
- pre-rendering 
    - generates html in advance instead of by client side javascript
    - better performance and seo
- api routes
- support for css modules
- authentication
- dev and prod build system

# 2 
https://www.youtube.com/watch?v=RY6B7JSBRRg&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=2

create default project
```
npx create-next-app hello-world
```
```
npm run dev
```

# 3 
https://www.youtube.com/watch?v=e-3UPyuOCq0&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=3 
- just going over set up of next js project (e.g. package.json)
- public folder holds public resources for project
- pages folder contains routing
- index.js gets served to browser when we visit localhost on port 3000
- _app.js defines layout of application
- can have api folder
- what is the purpose of _app.js? **OPEN QUESTION**

# 4
https://www.youtube.com/watch?v=fUG8h5XopnU&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=4
- when a file is added to the pages folder in a project, it automatically becomes available as a route

# 5 
https://www.youtube.com/watch?v=hvYKrqnY8LM&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=5
- example of file-based routing

# 6
https://www.youtube.com/watch?v=f-6GAntaum4&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=6
- nested routes
- just makes folder and add files within the folder to use nested routing
- makes index.js within the new folder


# 7
https://www.youtube.com/watch?v=Ql5kyJaYbls&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=7
- dynamic routing
- use nested routeing and also square brackets e.g. [productId].js
```js
import { useRouter } from 'next/router'

function ProductDetail() {
    const router = useRouter()
    const productId = router.query.productId
    return <h1>Details about {productId}</h1>
}

export default ProductDetail
```
- explictly named routes are prioritized over dynamic/wildcard routes

# 8
https://www.youtube.com/watch?v=nfAxNTmme64&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=8
Nested dynamic routes
- [productId]
    - review
        - [reviewId].js

```js
import { useRouter } from 'next/router'

function Review () {
    const router = useRouter()

    const { productId, reviewId } = router.query

    return (
        <h1>
            Review {reviewId} for product {productId}
        </h1>
    )
}
```

# 9
https://www.youtube.com/watch?v=ZHn726VDoIY&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=9
Catch all routes
- accounting for where there's multiple parts to the route without having to worry about nesting
 e.g. /docs/featur1/concept1 

 - [..params].js
 ```js
//  here params is an array
 const {params} = router.query
 ```
- [[..params]].js (double brackets) allows catch all page for root page
- 

# 10
https://www.youtube.com/watch?v=sigcnKAPddM&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=10
Link component navigation
- Can link to routes within pages 
```js
import Link from 'next/link'
<Link href="/>
    <a>Home</a>
</Link>
```
- Link is used client-side routing i.e. routing within the routes in your application
- should not use anchor tag for client side routing, inefficient
- replace prop on link tag
    - replace current history state

# 11
https://www.youtube.com/watch?v=8jhLvnm7fmE&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=11
- navigate programatically
```js
const handleClick = () => {
    console.log('Placing your order')
    router.push('/product')
}
...
...
...
<button onClick={handleClick}>Place Order</button>
```

# 12
https://www.youtube.com/watch?v=vpSDQawRpEk&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=12
Custom 404 page
- make 404.js to have custom 404 page

# 13
https://www.youtube.com/watch?v=TaDGyvh2Ud0&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=13
Routing summary
- age based routing mechanism: Pages are associated witha  route based on their file name
- Nested routes: Nested folder structure, files will be automatically routed in the same way in the URL
- Dynamic routes: Can be created by adding square brackets to a page name
- Catch all routes: Add 3 dots inside square brackets to create a catch all route. Helpful when you want different URLs for the same page layout or even when you're working with pages where some of the route parameters are optional
- Link component to navigate on click of an element
- useRouter hook;s to router.push method to navigate programatically
- How to create a custom 404 page

# 14
https://www.youtube.com/watch?v=GOdu5C8JzL8&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=14
Pre-rendering and Data fetching

- types of pre-rendering
    - Static generation
        - without data
        - with data
        - incremental static generation
        - dynamic parameters when fetching data
    - server side rendering
        - data fetching
- Client side data fetching
- Combining pre-rendering with client-side data fetching

# 15
https://www.youtube.com/watch?v=BeXbCgRxifs&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=15
Pre-rendering

- NextJS pre-renders evert a=page in the application by default

- Pre-render means NextJS generates HTML for each page in advance instead of having it all done by client-side Javascript
    - render in advance of sending it to the browser
- With plain react:
    1: INitial Load: app is not rendered
    2: JS loads
    3: Hydration: React components are initialized and App becomes interactive
- Pre-rendering (Using next.js)
    1: Initial Load: Pre-rendered HTML is displayed
    2: JS Loads
    3: Hydration: React components are initialized and App becomes interactive
        - if app has interactive components like <Link />, they'll be active after JS loads
- pre-rendering improves performance
    - in a React app, we need to wait for JavaScript to be executed e.g. fetch data from an external API and then render the UI
    - With pre-rendered page, HTML is already generated and loads faster
- pre-rendering helps with SEO because search engine can see content in src code

# 16
https://www.youtube.com/watch?v=keP1PygtJ8c&list=PLC3y8-rFHvwgC9mj0qv972IO5DmD-H0ZH&index=16
Static generation
