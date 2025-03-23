
##  ❒==1.Link==
এই উদাহরণে, "Go to About Page" লিঙ্কে ক্লিক করলে `/about` পেজে নেভিগেট হবে পুরো পেজ রিলোড না করেই।
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

## ❒==2.Query Parameters with Links==

✍️ type:01
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


## ❒==3 `useRouter`==

✍️ **Topic:01**

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


✍️ **Topic:02**

```js

import { useRouter } from 'next/router';

export default function Home() {
  const router = useRouter();

  const navigateWithMultipleQuery = () => {
    router.push({
      pathname: '/search',
      query: { q: 'nextjs', category: 'tutorial' }, // একাধিক Query Parameter
    });
  };

  return (
    <div>
      <h1>হোম পেজ</h1>
      <button onClick={navigateWithMultipleQuery}>খুঁজুন</button>
    </div>
  );
}
```

```js

import { useRouter } from 'next/router';

export default function Search() {
  const router = useRouter();
  const { q, category } = router.query; // একাধিক Query Parameter পড়া

  return (
    <div>
      <h1>খুঁজুন</h1>
      <p>আপনি খুঁজছেন: {q}</p>
      <p>ক্যাটাগরি: {category}</p>
    </div>
  );
}
```


## 4==❑ Query Parameter ডিফল্ট মান সেট করা==

☢ যদি Query Parameter না থাকে, তাহলে ডিফল্ট মান সেট করা যায়।

```js
import { useRouter } from 'next/router';

export default function Search() {
  const router = useRouter();
  const { q = 'default' } = router.query; // ডিফল্ট মান সেট করা

  return (
    <div>
      <h1>খুঁজুন</h1>
      <p>আপনি খুঁজছেন: {q}</p>
    </div>
  );
}
```



 
## 5 Params and Search params
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

```java
http://localhost:3000/product/123?color=blue&size=large

{
  "color": "blue",
  "size": "large"
}

🔹 params: { id: "123" } 
🔹 searchParams: { color: "blue", size: "large" }

```

☗`searchParams` মূলত **URL Query Parameters** (যেমন: `?color=blue&size=large`) থেকে মান (values) বের করতে সাহায্য করে। এগুলো সাধারণত কোনো অতিরিক্ত তথ্য পাঠানোর জন্য ব্যবহৃত হয়, যেমন **ফিল্টারিং, সাজানো (sorting), বা সার্চিং**।