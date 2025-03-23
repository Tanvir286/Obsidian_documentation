Next.js-এ **Dynamic Routing** একটি শক্তিশালী ফিচার যা আপনাকে ডাইনামিক URL তৈরি করতে সাহায্য করে। Dynamic Routing ব্যবহার করে আপনি URL-এ প্যারামিটার পাস করতে পারেন এবং সেই প্যারামিটার ব্যবহার করে পেজে ডাইনামিক কন্টেন্ট রেন্ডার করতে পারেন।

❐ Dynamic Routing তৈরি করতে, পেজের ফাইল নামে ব্র্যাকেট (`[]`) ব্যবহার করুন। উদাহরণস্বরূপ, `pages/posts/[id].js` ফাইল তৈরি করলে এটি একটি ডাইনামিক রুট হবে, যেখানে `id` একটি প্যারামিটার।

A Dynamic Segment can be created by wrapping a folder's name in square brackets: `[folderName]`. For example, `[id]` or `[slug]`.

```js
import { useRouter } from 'next/router';

export default function Post() {
  const router = useRouter();
  const { id } = router.query; // URL থেকে `id` প্যারামিটার পড়া

  return (
    <div>
      <h1>পোস্ট ID: {id}</h1>
      <p>এই পোস্টের ID হল: {id}</p>
    </div>
  );
}
```

এই উদাহরণে, যদি URL হয় `/posts/123`, তাহলে `id`-এর মান `123` হবে এবং পেজে এটি ডিসপ্লে হবে।

---
---


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

## ❏Catch-all segments

**Catch-All Segments** একটি শক্তিশালী ফিচার যা আপনাকে একাধিক প্যারামিটারকে একটি সিঙ্গেল রুটে হ্যান্ডেল করতে সাহায্য করে।

Catch-All Segments তৈরি করতে, ফাইল নামে তিনটি ডট (`...`) ব্যবহার করুন। উদাহরণস্বরূপ, `pages/posts/[...slug].js` ফাইল তৈরি করলে এটি একটি Catch-All রুট হবে, যেখানে `slug` একটি অ্যারে হিসেবে প্যারামিটার গুলোকে ধারণ করবে।

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

✔️ যদি URL হয় `/posts`, তাহলে `slug` হবে `undefined`।
✔️ যদি URL হয় `/posts/123`, তাহলে `slug` হবে `['123']`।
✔️যদি URL হয় `/posts/123/456`, তাহলে `slug` হবে `['123', '456']`।