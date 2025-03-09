Next.js-এ **import alias** ব্যবহার করলে **কোড ক্লিন** ও **ম্যানেজেবল** হয়, বিশেষ করে বড় প্রোজেক্টে যেখানে একাধিক কম্পোনেন্ট ও মডিউল থাকে।
## **✅ Import Alias কী ?**

সাধারণভাবে, আমরা **`import`** করলে **relative paths** ব্যবহার করি, যেমন:

```js
import Button from "../../components/Button";
import Header from "../../components/Header";
```

এভাবে `../../` ইউজ করলে **কোড রিডেবল থাকে না** এবং **মেইনটেন করা কঠিন** হয়।

👉 **সমাধান:** **Import Aliases** ব্যবহার করে আমরা সহজেই শর্টকাট পাথ সেট করতে পারি!

#### **✅`jsconfig.json` বা `tsconfig.json` ফাইলে alias সেট করুন ?**

 ```js
 {
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
      "@components/*": ["components/*"],
      "@utils/*": ["utils/*"],
      "@styles/*": ["styles/*"]
    }
  }
}
```

◐ **`@components/*` → `components/` ডিরেক্টরির শর্টকাট।**  
◐ **`@utils/*` → `utils/` ডিরেক্টরির শর্টকাট।**  
◐ **`@styles/*` → `styles/` ডিরেক্টরির শর্টকাট।**


## ❐ কিভাবে Import Alias ব্যবহার করবো?

এখন আমরা সহজেই শর্টকাট ব্যবহার করতে পারি!
### ⛔ আগের মতো জটিল path:

```js
import Button from "../../components/Button";
import Header from "../../components/Header";
```
### ✅ Import Alias দিয়ে সহজ পাথ:

```js
import Button from "@components/Button";
import Header from "@components/Header";
```

👉 দেখো, **`../../` এর ঝামেলা বাদ পড়েছে!** 