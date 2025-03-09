The Next.js [`<Image>`](https://nextjs.org/docs/app/building-your-application/optimizing/images) component extends the HTML `<img>` element to provide:

Next.js-তে `next/image` কম্পোনেন্ট ব্যবহার করে ইমেজ লোডিং এবং অপ্টিমাইজেশন করা যায়। নিচে একটি উদাহরণ দেওয়া হলো যেখানে `next/image` ব্যবহার করে ইমেজ ডিসপ্লে করা হয়েছে এবং এর সাথে কিছু ডিটেইলস যোগ করা হয়েছে।



✔️ এইটা সব সময় ব্যবহার করবে তাহলে যে কোন image problem করবে না ।

0.0 next.config.js
```js
const nextConfig = {
    images: {
        remotePatterns: [
            {
                protocol: 'https',
                hostname: '**',
            },
        ],
    },
};  
module.exports = nextConfig;
```

## ❒ Example: 01

```js
import React from 'react';
import Image from 'next/image';
import One from "../../assets/one.jpg"
const GalleryPage = () => {
    return (
        <div>
           <h1 className='text-5xl'>Image Optimization</h1>
            <div className='text-center'>
              <Image
                src="https://plus.unsplash.com/premium"
                alt="Next.js Image Optimization"
                width={500}
                height={400}/>   
                
               <Image
                src={One}
                alt="Next.js Image Optimization"
                width={500}
                height={400}/>

              </div>
        </div>
    );
};
export default GalleryPage;
```


✔️ `fill` প্রপার্টি ব্যবহার করা হয়েছে, যার ফলে ইমেজটি তার প্যারেন্ট কন্টেইনারের পুরো জায়গা জুড়ে বিস্তৃত হবে।`fill` ব্যবহার করলে `width` এবং `height` সেট করার প্রয়োজন নেই।