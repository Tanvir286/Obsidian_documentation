###  1. Defining Route and next route
![[next014.png]]

###  2.Nesting layouts
![[next010.png]]

Layout ভিতর যা থাকবে তা শুধু ঐ layout অধীনে সকল বিষয়  support পাবে।বাকি গুলো পাবে না।

### 3.Linking and navigation
#### 3.1
```js
import Link from 'next/link';

export default function Home() {
  return (
    <div>
      <h1>Welcome to the Homepage</h1>
      <Link href="/about">
        <a>Go to About Page</a>
      </Link>
    </div>
  );
}
```

#### 3.2 Passing Query Parameters in Links
```js
import Link from 'next/link';

export default function Home() {
  const userId = 42; 
  return (
    <div>
      <h1>Homepage</h1>
      <Link href={`/post/${post.id}`}>
        <a>View Profile</a>
      </Link>
    </div>
  );
}
```

```js
import { useRouter } from 'next/router';

export default function Profile() {
  const router = useRouter();
  const { id } = router.query;

  return (
    <div>
      <h1>User Profile</h1>
      <p>User ID: {id}</p>
    </div>
  );
}
```

#### 3.3 Navigation Using `useRouter`
```js
import { useRouter } from 'next/router';

export default function Home() {
  const router = useRouter();

  const navigateToAbout = () => {
    router.push('/about');
  };

  return (
    <div>
      <h1>Homepage</h1>
      <button onClick={navigateToAbout}>Go to About Page</button>
    </div>
  );
}
```

####  3.4 Params and Search params
```js 
const ProductDetail = ({ params, searchParams }) => {
  const { id } = params; // Dynamic route segment
  const { color, size } = searchParams; // Query parameters

  return (
    <div>
      <h1>Product Details</h1>
      <p>Product ID: {id}</p>
      <p>Color: {color}</p>
      <p>Size: {size}</p>
    </div>
  );
};
export default ProductDetail;
```

```
http://localhost:3000/product/123?color=blue&size=large

{
  "color": "blue",
  "size": "large"
}

```

### 4. Router Group
A route group can be created by wrapping a folder's name in parenthesis: ==(folderName)==
To organize routes without affecting the URL, create a group to keep related routes together. The folders in parenthesis will be omitted from the URL (e.g. `(marketing)` or `(shop)`.
 বন্ধনীর ফোল্ডারগুলি URL থেকে বাদ দেওয়া হবে (যেমন (বিপণন) বা (দোকান)।

![[next008.png]]

###  5.Dynamic Routes
A Dynamic Segment can be created by wrapping a folder's name in square brackets: `[folderName]`. For example, `[id]` or `[slug]`.

```js
// pages/products/[id].js
import { useRouter } from 'next/router';

const ProductDetail = () => {
  const router = useRouter();
  const { id } = router.query;  // Access dynamic route parameter

  return (
    <div>
      <h1>Product ID: {id}</h1>
    </div>
  );
};
export default ProductDetail;
```

#### 5.1 catch-all segments
 Dynamic Segments can be extended to **catch-all** subsequent segments by adding an ellipsis inside the brackets `[...folderName]`.

```js
pages/blog/[...slug].js

import { useRouter } from 'next/router';

const BlogPost = () => {
  const router = useRouter();
  const { category, slug } = router.query;

  return (
    <div>
      <h1>Category: {category}</h1>
      <h2>Slug: {slug?.join(' / ')}</h2>
      <p>Full path: /blog/{category}/{slug?.join('/')}</p>
    </div>
  );
};
export default BlogPost;
```


###  6.Not Found Page 404

🔹file name `not-found.js`

```
import Link from 'next/link'
 
export default function NotFound() {
  return (
    <div>
      <h2>Not Found</h2>
      <p>Could not find requested resource</p>
      <Link href="/">Return Home</Link>
    </div>
  )
}
```

---
### 7.Loading Page

✏️. loading.js![[next007.png]]

```js
import React from 'react';
const LoadingPage = () => {
    return (
        <div>
            <h1 className='text-4xl text-rose-700'>Loading..........</h1>
        </div>
    );
};
export default LoadingPage;
```

✏️. Fallback

```js
import React, { Suspense, lazy } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

const App = () => {
  return (
    <div>
      <h1>React Suspense Example</h1>
      {/* Wrap the lazy-loaded component in Suspense */}
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    </div>
  );
};
export default App;
```

### 8. Error Page

![[next004.png]]

```js
"use client"
const ErrorPage = ({error,reset}) => {
    return (
        <div>
            <h1>Something went wrong</h1>
            <h1>{error.message}</h1>
            <button onClick={reset} >Try Again</button>
        </div>
    );
};
export default ErrorPage;
```

➕ শুধু মাএ এটা একটা page যা "use client "  দিতে হবে,বাকি গুলো by default server component.
✖️ শুধুমাএ যে page error আছে , এই page hit করলে error সামনে আসবে।যা আগে globally সামনে আসতো।
✖️ অনেক সময় data fetching error network  কারনেও সমানে আসতে পারেনা।যার ফলে reset option, এতে পুরোটা একবার reload-load নেয়,বাটন চাপলে। এছাড়াও error message option দেখা যায় ।