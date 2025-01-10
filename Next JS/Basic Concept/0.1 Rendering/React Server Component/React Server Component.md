Next js render শুরুতে সকল log server run হয়।কিন্তু যখন এটা use client দেওয়া হয়,তখন browser  log করে দেখা যায় ।

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

এতে পুরোটা render হবে। যার ফলে সময় অনেক বেশি লাগবে। তারজন্য সময় যেন কম লাগে সে জন্য specific component use client ব্যাবহার করবো। এতে render টাইম কম লাগবে ।

![[next005.png]]

part one
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

part2
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