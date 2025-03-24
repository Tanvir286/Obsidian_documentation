

#  🚧【 **flex-grow কিভাবে কাজ করে** 】
<h1 style="
    background: linear-gradient(90deg, #ff7e5f, #feb47b);
    -webkit-background-clip: text;
    color: transparent;
    font-size: 20px;
    font-weight: bold;
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
    letter-spacing: 1px;
    text-align: center;
    padding: 15px;
    box-shadow: rgba(6, 24, 44, 0.4) 0px 0px 0px 2px, rgba(6, 24, 44, 0.65) 0px 4px 6px -1px, rgba(255, 255, 255, 0.08) 0px 1px 0px inset;
">
    flex-grow কিভাবে কাজ করে
</h1>

যখন একটি `display: flex;` ব্যবহার করা container-এর ভেতর কয়েকটি flex item থাকে, তখন `flex-grow` ব্যবহার করে আমরা ঠিক করতে পারি **কোন item কতটুকু অতিরিক্ত জায়গা নেবে।**

### **👉 flex-grow-এর মূল কাজ:**

- এটি **parent flex container-এর** অতিরিক্ত ফাঁকা জায়গা বণ্টন করে।
- ডিফল্টভাবে `flex-grow: 0;` থাকে, মানে কোনো item অতিরিক্ত জায়গা নেবে না।
- যদি একাধিক item-এ `flex-grow` সেট করা থাকে, তবে **গুণিতক অনুযায়ী তারা জায়গা ভাগাভাগি করবে।**


```css
.box1 { flex-grow: 1; } /* 1 অংশ নেবে */
.box2 { flex-grow: 3; } /* 3 অংশ নেবে */
.box3 { flex-grow: 1; } /* 1 অংশ নেবে */
```

| flex-grow Value | কাজ কি?                                 |
| --------------- | --------------------------------------- |
| `flex-grow: 0;` | কোনো অতিরিক্ত জায়গা নেবে না।            |
| `flex-grow: 1;` | অতিরিক্ত জায়গা সমানভাবে ভাগ হবে।        |
| `flex-grow: 2;` | অন্যদের তুলনায় দ্বিগুণ জায়গা নেবে।      |
| `flex-grow: 3;` | অন্যদের তুলনায় তিনগুণ জায়গা নেবে।       |
| `flex-grow: X;` | X এর মান অনুযায়ী জায়গা ভাগ হবে অনুপাতে। |

#  🚧【align-items: stretch কিভাবে কাজ করে】
<h1 style="
    background: linear-gradient(90deg, #ff7e5f, #feb47b);
    -webkit-background-clip: text;
    color: transparent;
    font-size: 20px;
    font-weight: bold;
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
    letter-spacing: 1px;
    text-align: center;
    padding: 15px;
    box-shadow: rgba(6, 24, 44, 0.4) 0px 0px 0px 2px, rgba(6, 24, 44, 0.65) 0px 4px 6px -1px, rgba(255, 255, 255, 0.08) 0px 1px 0px inset;
">
    align-items: stretch কিভাবে কাজ করে
</h1>

#### যদি দুটি পাশাপাশির কনটেন্টের উচ্চতা সমান করতে চান, তবে **CSS Grid** বা **Flexbox** ব্যবহার করে সহজেই এটি করা যায়। এখানে আমি একটি উদাহরণ দিচ্ছি, যেখানে দুটি কনটেন্ট একই উচ্চতায় থাকবে, যদিও তাদের কনটেন্টের আকার আলাদা।



একটি **CSS Flexbox** এবং **CSS Grid** প্রপার্টি, যা ব্যবহৃত হয় **উল্লম্বভাবে (cross-axis)** এলিমেন্টগুলিকে প্রসারিত বা স্ট্রেচ করতে। এই প্রপার্টিটি, সাধারণত, flexbox বা grid কন্টেইনারের ভিতরে আইটেমগুলির উচ্চতা বা প্রস্থ সামঞ্জস্য করতে ব্যবহৃত হয়।
### **`align-items: stretch;` এর কাজ:**

- **Flexbox** বা **Grid** কন্টেইনারের **child elements (items)** গুলিকে একে অপরের সাথে স্ট্রেচ করে, যাতে তারা কন্টেইনারের পুরো উচ্চতা বা প্রস্থ দখল করে।
- **`stretch`** মূলত **default value** (ডিফল্ট মান) এবং এটি উল্লম্বভাবে আইটেমগুলিকে প্রসারিত করে যাতে তারা তাদের কন্টেইনারের পূর্ণ উচ্চতা দখল করে।

![[grid06.png]]

### **বিস্তারিত ব্যাখ্যা:**

1. **Flexbox** এ:
    - **`align-items: stretch;`** এভাবে ব্যবহৃত হলে, **cross-axis** (যেটি flexbox কন্টেইনারের উল্লম্ব অক্ষ) বরাবর সব আইটেমের উচ্চতা সমান হয়ে যায়, যতটুকু কন্টেইনারের উচ্চতা থাকবে।
2. **Grid** এ:
    - গ্রিড কন্টেইনারে এই প্রপার্টি ব্যবহার করলে, গ্রিড আইটেমগুলো তাদের কন্টেইনারের পূর্ণ উচ্চতা এবং প্রস্থ দখল করে, যদি না তাদের নিজস্ব উচ্চতা বা প্রস্থ নির্দিষ্ট করা থাকে।

**`align-items: stretch;`** একটি খুবই গুরুত্বপূর্ণ প্রপার্টি যা flexbox এবং grid কন্টেইনারে ব্যবহৃত হয়ে সমস্ত আইটেমকে কন্টেইনারের পূর্ণ উচ্চতা বা প্রস্থ দখল করতে সাহায্য করে, যদি তাদের কনটেন্টের আকার ছোট হয়।


