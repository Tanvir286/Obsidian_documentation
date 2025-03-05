Next JS render শুরুতে সকল log server run হয়।কিন্তু যখন এটা use client দেওয়া হয়,তখন browser  log করে দেখা যায় ।

![[next013.png]]

#### now use client add 

```js
"use client"
import React from "react";

const Home = () => {

  const [count, setCount] = useState(0);

  const increment = () => {
    setCount((prevCount) => prevCount + 1);
  };

  const decrement = () => {
    setCount((prevCount) => prevCount - 1);
  }
  
  return (
    <div>
      <h1 className="text-5xl text-red-600">Welcome to Next.js</h1>
    
      <button className="btn btn-accent"
       onClick={increment}
      >Increment</button>

      <button className="btn btn-accent"
        onClick={decrement}
      >Decrement</button>

    </div>
  );
};
export default Home;
```

---
---

⚫ এই ক্ষেত্রে সম্পূর্ণ পৃষ্ঠাটি একসাথে **render** হবে, যার ফলে লোড হতে বেশি সময় লাগবে। তবে, সময় কমানোর জন্য **specific components**-গুলোর জন্য **client component** ব্যবহার করা উচিত। এর ফলে **render time** কমে যাবে এবং পারফরম্যান্স উন্নত হবে।

![[next005.png]]

### ①  Main Page

```js
import React from "react";
import Counter from './../component/Counter/page';
const Home = () => {
  return (
    <div>
      <h1 className="text-5xl text-red-600">Welcome to Next.js</h1>
      {/* Add the Counter component */}
      <Counter />
    </div>
  );
};
export default Home;
```

### ②  Specific Component

```js
"use client";
import React, { useState } from "react";
const Counter = () => {
  // Declare a state variable 'count' with an initial value of 0
  const [count, setCount] = useState(0);
  // Function to increment the count
  const increment = () => {
    setCount((prevCount) => prevCount + 1);
  };
  // Function to decrement the count
  const decrement = () => {
    setCount((prevCount) => prevCount - 1);
  };
  return (
    <div>  
      <button className="btn btn-accent"
       onClick={increment}
      >Increment</button>

      <button className="btn btn-accent"
        onClick={decrement}
      >Decrement</button>    
    </div>
  );
};
export default Counter;
```