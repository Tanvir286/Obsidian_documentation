🕔 The `generateStaticParams` function is used in **Next.js** when working with **dynamic routes** in a **Static Site Generation (SSG)** or **Incremental Static Regeneration (ISR)** setup. 
When you have a page with dynamic segments (e.g., `/blogs/[blogId]`), Next.js needs to know which specific paths to generate at build time. `generateStaticParams` provides those paths.

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
    const blog = await res.json();
    return (
        <div>
            <BlogDetails blog={blog} />
        </div>
    );
};
export default Blogspage;
```

