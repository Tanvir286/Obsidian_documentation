![[next012.png]]

![[next015.png]]

## 📰 SSG( Static Site Generation )

◎ **বিল্ড টাইমে HTML জেনারেট করে, যা পারফরম্যান্সের জন্য ভালো।**

যখন কোনো Project কে Deploy করি,তখন কিন্তু পুরো Project Build  করে নিতে হয়। Next js তাদের Project গুলোর Static Content কে Bundle করে Html File তৈরি করে। যা Build Time এ Create করে Html file গুলো যখন কোনো route৷ হিট করে,তখন তার deploy করা static file গুলো সব প্রথম visible হয়। সবগুলো static কোনো dynamic  content থাকবে না।

1. **Deployment প্রক্রিয়া**:
    - যখন আপনি Next.js প্রজেক্ট ডেপ্লয় করেন, তখন পুরো প্রজেক্টটি বিল্ড (Build) করা হয়।    
    - বিল্ড প্রক্রিয়ায় Next.js আপনার অ্যাপ্লিকেশনের সমস্ত Static Content (যেমন HTML, CSS, JavaScript) Bundle করে এবং প্রি-রেন্ডার করে।
        
2. **Static File Generation**:
    - Next.js বিল্ড টাইমে Static Site Generation (SSG) ব্যবহার করে HTML ফাইল তৈরি করে।   
    - উদাহরণস্বরূপ, যদি আপনার প্রজেক্টে `pages/index.js`, `pages/about.js`, এবং `pages/blog/[id].js` থাকে, তাহলে বিল্ড টাইমে এই পেজগুলোর জন্য আলাদা আলাদা HTML ফাইল তৈরি হবে।
        
3. **Deploy করার পর**:
    - ডেপ্লয় করার পর এই Static HTML ফাইলগুলো সার্ভারে স্টোর করা হয়।    
    - যখন কোনো ইউজার আপনার ওয়েবসাইটে ভিজিট করে (যেমন, `/about` রুটে), তখন সার্ভার সেই রুটের জন্য প্রি-জেনারেট করা Static HTML ফাইলটি দ্রুত সার্ভ করে।
        
4. **Static Content এর সুবিধা**:
    
    - **দ্রুত লোড টাইম**: যেহেতু পেজগুলো প্রি-রেন্ডার করা থাকে, তাই ইউজার দ্রুত কন্টেন্ট দেখতে পায়।   
    - **SEO ফ্রেন্ডলি**: সার্চ ইঞ্জিন Static HTML ফাইল সহজেই ক্রল করতে পারে, যা SEO-এর জন্য ভালো। 
    - **সার্ভার লোড কম**: Static ফাইলগুলো CDN-এ হোস্ট করা যায়, ফলে সার্ভার লোড কমে।
- 
## 📰 SSR(Server Site Rendering)

◎ **রিকোয়েস্ট টাইমে HTML জেনারেট করে।**

User কোনো কিছুর জন্য Request করল,Request অনুসারে Database থেকে Query করে  Data নিয়ে এসে সে তার Html Content Create হয়,এবং Server থেকে Brower visible হয়ে থাকে। যা আগে থেকে তৈরি করা নেই ।

## 📰 Incremental Static Regeneration (ISR):

◎ **স্ট্যাটিক পেজ আপডেট করার সুবিধা।**

User কোনো কিছুর জন্য Request করল,Request অনুসারে Database থেকে Query করে  Data নিয়ে এসে সে তার Html Content Create হয়,এবং Server থেকে Brower visible হয়ে থাকে। যা আগে থেকে তৈরি করা নেই ।