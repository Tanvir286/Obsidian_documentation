## ✏️ Loading.js![[next007.png]]

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

## ✏️ Fallback

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


---

<h1 style="
    background: linear-gradient(90deg, #ff7e5f, #feb47b);
    -webkit-background-clip: text;
    color: transparent;
    font-size: 3rem;
    font-weight: bold;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    letter-spacing: 2px;
    text-align: center;
    padding: 10px;
">
    Data Card Loading
</h1>

![[34.png]]


অনেক সময় ছবির মতন আমরা বিভিন্ন ওয়েব-সাইট দেখি। তাদের data লোড হওয়ার আগে এ রকম দেখায়। যাতে আগে থেকে user বুঝতে পারে সামনে কি আসতে যাচ্ছে।


```js

import { Blog } from '@/components/types';
import LoadingCard from '@/components/ui/LoadingCard';

const Loading =  async() => {

 const res = await fetch("http://localhost:5000/blogs")
 const blogs = await res.json()

  return (

    <div>
      <div className='grid grid-cols-4 gap-3'>
        { blogs.map((blog: Blog) =>(
          <LoadingCard key={blogs.id} />
        ))    
        }
      </div>
    </div>
  );
}
export default Page;
```

```css
const LoadingCard = () => {

  return (

    <div className="card w-full bg-base-100 shadow-xl ">
      <div className="w-full h-36 bg-gray-100 rounded-xl"></div>
      <div className="card-body h-36"></div>
    </div>
  );
};

export default LoadingCard;
```

