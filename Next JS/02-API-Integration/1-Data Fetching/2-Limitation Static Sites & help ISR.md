### ❐ Force-cache

◈ এটি ডেটা ক্যাশে করে রাখে এবং পরবর্তী রিকোয়েস্টে ক্যাশে করা ডেটা ব্যবহার করে, যাতে ডেটা বারবার ফেচ না করতে হয়।

```js
export const metadata = {
  title: "Home",
  description: "This is home page",
};

const Home = async() => {

 const res = await fetch('http://localhost:5000/shoes',{
  cache:"force-cache",
 });
 const shoes = await res.json();
 
  return (
   <div>
       <h1 className="text-amber-500">Hi tanvir</h1>
       <div>
         {
           shoes.slice(0,3).map(shoe => (
             <div key={shoe.id}>
               <h1>{shoe.title}</h1>
               <p>{shoe.price}</p>
             </div>           ))
         }
       </div>
   </div>
  );
}
export default Home;
```

##### ⌚যখন আমি `npm run bulid` করব, তখন `static content html file create` করে রাখে। তখন যদি `cache` দেই , তাহলে `data cache` করে রাখে,jodio by default cache  করে রাখে । route সহ static file তৈরি করে দেই ।

![[next006.png]]

##### ❐  NPM Start দিয়ে Production mood on করে । Production mood run করার সময় যদি code  change করা হয়, তা change হবে না । আবার build করতে হবে ।

##### **🔒** তবে আবার new করে build করে আবার npm start করা অনেক বড় সমস্যা, এত বার data change হবে যে নতুন করে  বার বার build  করা সম্ভব না।তার জন্য  revalidation যুক্ত করলে,সমস্যা সমাধান।

---
### ⌛ এ সমস্যা জন্য ISR ব্যবহার ।

#### ⌨ ISR হল Next.js-এর একটি শক্তিশালী ফিচার, যা স্ট্যাটিক পেজ আপডেট করার সুবিধা দেয়।

#### ▣ ISR হল Next.js-এর একটি শক্তিশালী ফিচার, যা Static Site Generation (SSG)-কে আরও ডাইনামিক এবং ফ্লেক্সিবল করে তোলে। এটি আপনাকে স্ট্যাটিক পেজ আপডেট করার সুবিধা দেয়, এমনকি বিল্ড টাইমের পরেও।

### **ISR-এর সুবিধা**:

I. **ডাইনামিক ডেটা**: পেজগুলো স্ট্যাটিক থাকার পরেও ডেটা আপডেট করা যায়।
II. **সার্ভার লোড কম**: পেজগুলো স্ট্যাটিক থাকার কারণে সার্ভার লোড কম হয়।
III. **স্কেলেবিলিটি**: বড় সাইটগুলোর জন্য আদর্শ।
### **ISR vs SSG vs SSR**:

I. **SSG**: বিল্ড টাইমে পেজ রেন্ডার হয়। পারফরম্যান্স ভালো, কিন্তু ডেটা আপডেট হয় না।
II.**SSR**: প্রতি রিকোয়েস্টে পেজ রেন্ডার হয়। রিয়েল-টাইম ডেটার জন্য ভালো, কিন্তু সার্ভার লোড বেশি।
II.**ISR**: বিল্ড টাইমে পেজ রেন্ডার হয়, কিন্তু নির্দিষ্ট সময় পর পর আপডেট করা যায়। এটি SSG এবং SSR-এর মধ্যে একটি ব্যালেন্স।

---
### ❐ Revalidate

◈`Revalidate` ব্যবহার করে নির্দিষ্ট সময় পর পর পেজ আপডেট করা যায়।

```js
export const metadata = {
  title: "Home",
  description: "This is home page",
};

const Home = async () => {
  const res = await fetch('http://localhost:5000/shoes', {
    next: { revalidate: 10 }, // Revalidate every 10 seconds
  });
  const shoes = await res.json();

  return (
    <div>
      <h1 className="text-amber-500">Hi Tanvir</h1>
      <div>
        {shoes.slice(0, 3).map((shoe) => (
          <div key={shoe.id}>
            <h1>{shoe.title}</h1>
            <p>{shoe.price}</p>
          </div>
        ))}
      </div>
    </div>
  );
};
export default Home;
```
