###  1. Defining Route and next route
![[next014.png]]

###  2.Layout & Nesting layouts

`Layout.js` হচ্ছে একটি **পুনঃব্যবহারযোগ্য (reusable) wrapper component**, যা Next.js-এ একটি নির্দিষ্ট পেজ বা একাধিক পেজের জন্য **একই স্ট্রাকচার (structure) বজায় রাখতে** সাহায্য করে।

✅ যদি প্রতিটি পেজে একই **Navbar, Sidebar, Footer** থাকে, তাহলে `layout.js` ব্যবহার করা হয়।  
✅ এটি **একই কোড বারবার লেখার প্রয়োজনীয়তা কমায়**।  
✅ `layout.js` মূলত **parent component** হিসেবে কাজ করে, যেখানে **child components** (বা পেজগুলো) `{children}` এর মাধ্যমে রেন্ডার হয়।

![[next010.png]]

Layout ভিতর যা থাকবে তা শুধু ঐ layout অধীনে সকল বিষয়  support পাবে। বাকি গুলো পাবে না । 
Like Here **Footer** ।

তোমার `dashboard` রাউটের সব পেজের জন্য **একই Footer  লাগবে। তাহলে `layout.js` এ এগুলো একবার সেট করলেই সব পেজে দেখাবে!** 

```js
export default function DashboardLayout({ children }) {
  return (
    <div>
      {children}
      <Footer/>
    </div>
  );
}
```


### 3. Router Group
A route group can be created by wrapping a folder's name in parenthesis: ==(folderName)==
To organize routes without affecting the URL, create a group to keep related routes together. The folders in parenthesis will be omitted from the URL (e.g. `(marketing)` or `(shop)`.
 বন্ধনীর ফোল্ডারগুলি URL থেকে বাদ দেওয়া হবে (যেমন (বিপণন) বা (দোকান)।

![[next008.png]]


###  4.Not Found Page 404

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

### 5.Loading Page


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

### 6. Error Page

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
❌শুধুমাএ যে page error আছে , এই page hit করলে error সামনে আসবে।যা আগে globally সামনে আসতো।
❌ অনেক সময় data fetching error network  কারনেও সমানে আসতে পারেনা।যার ফলে reset option, এতে পুরোটা একবার reload-load নেয়,বাটন চাপলে। এছাড়াও error message option দেখা যায় ।