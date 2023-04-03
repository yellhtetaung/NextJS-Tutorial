# Next.js Tutorial

## How to create porject using next.js

```bash
npx create-next-app projectname
cd projectname
npm run dev
```

---

## What is Next.js?

The React Framework for Production.

## The React Framework for Production

**React**

- Not quite possible to build a full feature rich application ready to be deployed for production
- React is a library for building user interfaces
- You have to make decisions on other features of the app like routing, styling, authentication etc.

**Next.js**

- A package that uses React for building user interfaces
- Loaded with a lot more features that enable you build full fledged production ready applications. Features exactly like routing, styling, authentication, bundle optimization etc.
- There is not need to install additional packages. Next.js provides everythings for you
- Opinions and conventions need to be followed to implement the above said features

---

## Why Learn Next.js?

Next.js simplifies the process of building a react application for production

1. File based routing
2. Pre-rendering
3. API routes
4. Support CSS modules
5. Authentication
6. Dev and Prod build system

---

## Pre-requisites

1. HTML, CSS and JavaScript Fundamentals
2. ES6 + Features
3. React Fundamentals

---

## Routing Section Intro

**Routing in a React app**

- Install a third party package
- routes.js file to configure the routes
- For each route, create a component file, export the component, import it in routes.js and configure the new route with a _path_ property

**\*\***\*\*\*\***\*\***\*\*\*\***\*\***\*\*\*\***\*\***Routing in Next.js app**\*\***\*\*\*\***\*\***\*\*\*\***\*\***\*\*\*\***\*\***

- File-system based routing mechanism
- When a file is added to the pages folder in a project, it automatically becomes available as a route
- By mixing and matching file names with a nested folder structure, it is possible to pretty much define the most common routing patterns

**Routes**

1. Route with Pages
2. Nested routes
3. Dynamic routes
4. Catch-all routes
5. Navigate from the UI
6. Programmatically navigate b/w Pages

---

## Routing With Pages

### Routing With Pages

| Pages      | URL or Routing            |
| ---------- | ------------------------- |
| index.js   | localhost:3000/           |
| about.js   | localhost:3000/about      |
| profile.js | localhost:3000/profile.js |

---

### Nested Routes

| Pages           | URL or Routing        |
| --------------- | --------------------- |
| /blog/index.js  | localhost:3000/blog   |
| /blog/first.js  | localhost:3000/first  |
| /blog/second.js | localhost:3000/second |

---

### Dynamic Routes

| Pages                   | URL or Routing           |
| ----------------------- | ------------------------ |
| /product/index.js       | localhost:3000/product   |
| /product/[productId].js | localhost:3000/product/1 |
| /product/[productId].js | localhost:3000/product/2 |

How to get id

```jsx
import { useRouter } from "next/route";

function ProductDetails() {
  const router = useRouter();
  const productId = router.query.productId;

  return (
    <>
      <h2>Details about product {productId}</h2>
    </>
  );
}

export default ProductDetails;
```

---

### Nested Dynamic Routes

| Pages                                  | URL or Routing                    |
| -------------------------------------- | --------------------------------- |
| /product/[productId]/index.js          | localhost:3000/product/1          |
| /product/[productId]/review/[reviewId] | localhost:3000/product/1/review/2 |
| /product/[productId]/review/[reviewId] | localhost:3000/product/1/review/3 |

How to get Id

```jsx
import { useRouter } from "next/router";

function Review() {
  const router = useRouter();
  const { productId, reviewId } = router.query;

  return (
    <h1>
      Review {reviewId} for product {productId}
    </h1>
  );
}
export default Review;
```

---

### Catch All Routes

| Pages                | URL or Routing                        |
| -------------------- | ------------------------------------- |
| /docs/[[…prarms.js]] | localhost:3000/docs/                  |
|                      | localhost:3000/docs/feature1/concept1 |
|                      | localhost:3000/docs/feature2/concept2 |

```jsx
import { useRouter } from "next/router";

function Doc() {
  const router = useRouter();
  const { params = [] } = router.query;

  if (params.length === 2) {
    return (
      <h1>
        Viewing docs for feature {params[0]} and concept {params[1]}
      </h1>
    );
  } else if (params.length === 1) {
    return <h1>Viewing doc for feature {params[0]}</h1>;
  }

  return <h2>Docs Home Page</h2>;
}

export default Doc;
```
