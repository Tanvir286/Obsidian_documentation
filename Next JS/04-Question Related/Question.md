
| Question No | Topic                                                  |
| ----------- | ------------------------------------------------------ |
| 1           | **Next.js Data Fetching: Server vs Client Components** |
| 2           | **Client Component-এ async/await কাজ করবে  কিভাবে **   |
|             |                                                        |
|             |                                                        |
|             |                                                        |



<body style="font-family: 'Roboto', sans-serif; margin: 0; padding: 0; display: flex; justify-content: center; align-items: center; height: 10vh; background-color: #e2e8f0;">

  <header style="background: #6a89cc; color: #fff; padding: 60px 30px; text-align: center; border-radius: 12px; box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15); max-width: 700px; width: 100%;">
    <h1 style="font-size: 42px; font-weight: 700; margin: 0; color: #fff;text-align: center; ">01: Next.js Data Fetching</h1>
    <p style="font-size: 20px; margin-top: 20px; font-weight: 400; color: #f1f1f1;">   <span style="font-weight: 700; color: #white;">Topic: </span>  Server vs Client Components:</p>
  </header>

</body>


Next.js-এ **data fetching** মূলত **Server Component** এর মধ্যে করা যায়, কারণ এটি **সার্ভার থেকে** সরাসরি ডাটা আনতে পারে।

কিন্তু **Client Component** (যেখানে `"use client"` থাকে) সার্ভারে চলে না, তাই এটি **async data fetching** সরাসরি করতে পারে না।

তাহলে **Client Component-এ ডাটা কীভাবে আনবো?**  

👉 Server Component-এ ডাটা আনতে হবে, তারপর **props দিয়ে Client Component-এ পাঠাতে হবে**


<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 22px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 Server Component দিয়ে সরাসরি Data Fetch করা
    </h1>
✔️ (Recommended Way)

✅ Server Component-এ সরাসরি **async/await** ব্যবহার করা যায়, কারণ এটি সার্ভারে চলে।

```tsx
// Server Component (directly fetches data from API)
async function ProductsPage() {
  const res = await fetch("https://fakestoreapi.com/products");
  const products = await res.json();

  return (
    <div>
      <h1>Product List</h1>
      {products.map((p: any) => (
        <p key={p.id}>{p.title}</p>
      ))}
    </div>
  );
}
export default ProductsPage;
```

✔ **এখানে সরাসরি `fetch()` করা হয়েছে, কারণ এটি সার্ভারে রান হচ্ছে।**  
✔ **দ্রুত লোড হয় ও SEO-ফ্রেন্ডলি।**


<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 18px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        ❌ Client Component-এ সরাসরি Data Fetch কাজ করবে না
    </h1>
Client Component-এ **async/await** কাজ করবে না, কারণ এটি ব্রাউজারে চলে এবং **server-side API calls করতে পারে না।**

```tsx
"use client";

async function Products() {
  const res = await fetch("https://fakestoreapi.com/products");
   // ❌ কাজ করবে না
  const products = await res.json();

  return (
    <div>
      <h1>Product List</h1>
      {products.map((p: any) => (
        <p key={p.id}>{p.title}</p>
      ))}
    </div>
  );
}

export default Products;

```

❌ **এটা কাজ করবে না, কারণ Client Component-এ async/await সরাসরি ইউজ করা যাবে না।**

**Client Component-এ `async/await` কাজ করবে** যদি এটি **useEffect, event handler, বা অন্য `async` function-এর মধ্যে থাকে।**  

❌ **Client Component-কে সরাসরি `async function` বানানো যাবে না।**



<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 18px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        Server Component থেকে Props দিয়ে Client Component-এ Data পাঠানো
    </h1>
যদি Client Component ব্যবহার করতে চান, তাহলে **Server Component-এ ডাটা আনতে হবে, তারপর props দিয়ে পাঠাতে হবে।**

```jsx
import ProductsList from "./ProductsList"; 

async function ProductsPage() {
  const res = await fetch("https://fakestoreapi.com/products");
  const products = await res.json();

  return <ProductsList products={products} />; 
  // Props দিয়ে Client Component-এ পাঠানো হচ্ছে
}
export default ProductsPage;
```

✔ **এখানে data fetch করা হয়েছে Server Component-এ।**  
✔ **তারপর Client Component-এ `props` হিসেবে পাঠানো হয়েছে।**

```jsx
"use client"; 

function ProductsList({ products }) {
  return (
    <div>
      <h1>Product List</h1>
      {products.map((p) => (
        <p key={p.id}>{p.title}</p>
      ))}
    </div>
  );
}
export default ProductsList;
```

✔ **এখানে props হিসেবে ডাটা এসেছে, তাই `fetch()` করার দরকার নেই।**



<body style="font-family: 'Roboto', sans-serif; margin: 0; padding: 0; display: flex; justify-content: center; align-items: center; height: 10vh; background-color: #e2e8f0;">

  <header style="background: #6a89cc; color: #fff; padding: 60px 30px; text-align: center; border-radius: 12px; box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15); max-width: 700px; width: 100%;">
    <h1 style="font-size: 42px; font-weight: 700; margin: 0; color: #fff;text-align: center; ">02: Next.js Data Fetching</h1>
    <p style="font-size: 20px; margin-top: 20px; font-weight: 400; color: #f1f1f1;">   <span style="font-weight: 700; color: #white;">Topic: </span>  Client Component-এ async/await কাজ করবে  কিভাবে</p>
  </header>

</body>



<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 18px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        useEffect এর মধ্যে  async/await ব্যবহার
    </h1>

```tsx
"use client";

import { useEffect, useState } from "react";

export default function FetchWithUseEffect() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch("https://jsonplaceholder");
        const result = await response.json();
        setData(result);
      } catch (error) {
        console.error("Error fetching data:", error);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []); // Empty dependency array → একবারই রান হবে

  return (
    <div>
      {loading ? <p>Loading...</p> : <h2>{data?.title}</h2>}
    </div>
  );
}
```

✅ **কেন কাজ করবে?**

- `useEffect` API কল শুরু করার জন্য ব্যবহার হয়েছে।
- **`fetchData()` ফাংশন `async`**, তাই এটি **Promise handle করতে পারছে।**


<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 18px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        Button Click করলে Data Fetch হবে (Event Handler-এর মধ্যে `async/await`
    </h1>
```js
"use client";

import { useState } from "react";

export default function FetchOnClick() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(false);

  const handleFetch = async () => {
    setLoading(true);
    try {
      const response = await fetch("https://jsonplaceholder");
      const result = await response.json();
      setData(result);
    } catch (error) {
      console.error("Error fetching data:", error);
    } finally {
      setLoading(false);
    }
  };

  return (
    <div>
      <button onClick={handleFetch}>
        Fetch Data
      </button>

      {loading && <p>Loading...</p>}
      {data && <h2>{data.title}</h2>}
    </div>
  );
}


```


✅ `handleFetch()` হল **একটি `async` function**, যা **Button Click হলে execute হবে**।


| ✅ Client Component-এ `async/await` কাজ করবে যদি: | 📌 কিভাবে কাজ করবে?                                     |
| ------------------------------------------------ | ------------------------------------------------------- |
| 1️⃣ `useEffect` এর মধ্যে রাখো                    | Component লোড হলে API থেকে data fetch করবে।             |
| 2️⃣  Event handler (`button click`) ব্যবহার করো  | Button ক্লিক করলে API কল হবে।                           |
| 3️⃣  আলাদা `async` function লিখে সেটাকে Call করো | অন্য ফাংশনের মধ্যে `async` ব্যবহার করে API কল করা যাবে। |
