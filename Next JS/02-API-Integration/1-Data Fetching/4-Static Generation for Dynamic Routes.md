#### ✎ Static Paths তৈরি করার জন্য `generateStaticParams` ফাংশন । এই ফাংশনটি static pages generate করার জন্য ব্যবহার করা হচ্ছে।
#### 🔒user যখন server side hit করবে server side request অনুসারে data আনে,কিন্তু এটা সময় সাপেক্ষ। তাই আমরা চাচ্ছি যে আগেই থেকেই কিছু data এনে রেখে দিতে।

⛳️ ধরেন ১০০ data ভিতর  ১০ data আগেই static generation(html content create) করে রাখলাম। এতে  user request করার সাথে সাথে instand data পাবে। 

⛳️ এতে হবে কি একই page এ কিছু অংশ server side আবার কিছু অংশ static site run করবে । 

⛔ এটা dynamic route ব্যবহার করা যায়।

![[next017.png]]

```js
import { Blog } from '@/components/types';
import BlogDetails from '@/components/ui/BlogDetails';

interface BlogId {
    params: {
        blogId: string;
    };
}

export const generateStaticParams = async () => {
    const res = await fetch(`http://localhost:5000/blogs`);
    const blogs = await res.json();
    return blogs.slice(0,3).map((blog: Blog ) =>({
            blogId:blog.id,
      }));
}

  
const Blogspage = async ({ params }: BlogId) => {
   
   const res = await fetch(`http://localhost:5000/blogs/${params.blogId}`,{
        cache:"no-store"
    });

   if(!res.ok){
     return notFound();
   }

    const blog = await res.json();
    
    return (
        <div>
            <BlogDetails blog={blog} />
        </div>
    );
};

export default Blogspage;
```

---
##  ☂ Explanation:

### 🚩  **যখন `/blog/1` থেকে `/blog/3` visit করবো, তখনও কি এই API কল হবে? নাকি Static Page থেকে আসবে?**

### **📢 উত্তর:**  **না! `/blog/1` থেকে `/blog/3` visit করলে API থেকে fetch হবে না।**  

**কারণ:** Next.js আগেই **SSG (Static Site Generation)** করে **এই ব্লগগুলোর HTML পেজ তৈরি করে রেখেছে।**  **তাই, `/blog/1` থেকে `/blog/3` একদম ইনস্ট্যান্ট লোড হবে, কোনো API request লাগবে না।**


### 🚩  **যখন `/blog/4` বা তার বেশি ID-এর ক্ষেত্রে (Dynamic Mode)?**

```js
const res = await fetch(`http://localhost:5000/blogs/${params.blogId}`, {     cache: "no-store", });
```

Next.js `cache: "no-store"` থাকার কারণে API থেকে ডাটা আনবে।

### **📢 উত্তর:  এই  ব্লগগুলো Build Time-এ Static হয়নি, তাই Next.js Dynamic ভাবে fetch করবে।  

🔹 **কারণ:** 
✓ Next.js দেখবে যে `/blog/4` static generate হয়নি।
✓ তখন`fetch("http://localhost:5000/blogs/11")` থেকে ডাটা আনবে ।
✓ নতুনভাবে Page Render হবে (SSR এর মতো) ।

| **Route**               | **Static Page?** | **API Call হবে?**                |
| ----------------------- | ---------------- | -------------------------------- |
| `/blog/1` - `/blog/3`   | ✅ (Static)       | ❌ না, কারণ এগুলো আগেই তৈরি হয়েছে |
| `/blog/4` - `/blog/100` | ❌ (Dynamic)      | ✅ হ্যাঁ, API থেকে ডাটা আনবে      |
