
<h1 style="
    background: linear-gradient(90deg, #ff7e5f, #feb47b);
    -webkit-background-clip: text;
    color: transparent;
    font-size: 3.5rem;
    font-weight: bold;
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
    letter-spacing: 1px;
    text-align: center;
    padding: 15px;
    box-shadow: rgba(6, 24, 44, 0.4) 0px 0px 0px 2px, rgba(6, 24, 44, 0.65) 0px 4px 6px -1px, rgba(255, 255, 255, 0.08) 0px 1px 0px inset;
">
    Grid basic
</h1>

![[grid.jpg]]

CSS Grid হল একটি 2D লেআউট সিস্টেম, যা আপনাকে **column (স্তম্ভ) এবং row (সারি)** তৈরি করতে সাহায্য করে। এটি Flexbox-এর মতন হলেও, Flexbox প্রধানত **1D (একদিকের লেআউট)** করে, আর Grid **2D (দুই দিকের লেআউট)** করতে পারে।
#### **CSS Grid: X-axis (Column) & Y-axis (Row) একসাথে কাজ করা ❓**

CSS Grid-এর সবচেয়ে বড় সুবিধা হলো এটি **দুই দিকেই (X-axis ও Y-axis) একসাথে কাজ করতে পারে**। Flexbox একসময় **একটি মাত্র দিক** (Row বা Column) নিয়ন্ত্রণ করতে পারে, কিন্তু **Grid একই সাথে Column & Row উভয় দিকেই কাজ করতে পারে**।

#### **CSS Grid এর মূল বিষয়বস্তু**

Grid ব্যবহার করতে গেলে দুটি জিনিস লাগে:

1. **Grid Container:** এটি পুরো গ্রিডের প্রধান কন্টেইনার।
2. **Grid Items:** কন্টেইনারের ভেতরের প্রতিটি আইটেম।

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
    Properties of the parent
</h1>
# 🚩 grid-template-columns 
---
### ✔️ example 01

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3 টি সমান কলাম */
  grid-gap: 10px;
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
</div>

```

এখানে প্রতিটি কলাম সমান প্রস্থে বিভক্ত হয়েছে।
### ✔️ example 02

```css
.grid-container {
  display: grid;
  grid-template-columns: 200px 300px 1fr; 
  /* প্রথম কলাম 200px, দ্বিতীয় 300px, তৃতীয় কলাম বাকী জায়গা পূর্ণ করবে */
  grid-gap: 10px;
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
</div>
```

প্রথম কলাম 200px প্রস্থ, দ্বিতীয় কলাম 300px প্রস্থ এবং তৃতীয় কলাম বাকী জায়গা পূর্ণ করবে।

### ✔️ example 03

```css
.grid-container {
  display: grid;
  grid-template-columns: 200px auto 150px; 
  /* প্রথম কলাম 200px, দ্বিতীয় কলাম স্বয়ংক্রিয়ভাবে বাকি জায়গা পূর্ণ করবে, 
    তৃতীয় কলাম 150px */
  grid-gap: 10px;
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
</div>
```

![[grid01.png]]

### ✔️ `repeat()` ফাংশন ব্যবহার করে কলাম সংখ্যা

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* 4 টি সমান কলাম */
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
</div>
```

এখানে `repeat(4, 1fr)` ব্যবহার করে ৪টি সমান কলাম তৈরি হয়েছে।


# 🚩 grid-template-rows
---
### ✔️ example 01

```css
.grid-container {
  display: grid;
  grid-template-rows: 100px 200px 150px; /* 3 টি সারি, প্রতিটির উচ্চতা ভিন্ন */
  grid-gap: 10px;
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
</div>

```

প্রথম সারি 100px, দ্বিতীয় সারি 200px এবং তৃতীয় সারি 150px উচ্চতা থাকবে।

![[grid02.png]]

### ✔️ example 02 `auto` ব্যবহার করে সারির উচ্চতা

```css
.grid-container {
  display: grid;
  grid-template-rows: auto auto auto;
  /* প্রতিটি সারির উচ্চতা কন্টেন্ট অনুযায়ী অটো হবে */
  grid-gap: 10px;
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
</div>

```


![[grid03.png]]

### ✔️ `repeat()` ফাংশন ব্যবহার করে কলাম সংখ্যা

```css
.grid-container {
  display: grid;
  grid-template-rows: repeat(3, 150px); 
  /* 3 টি সারি, প্রতিটির উচ্চতা 150px */
  grid-row-gap:10px;
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
</div>
```

এখানে `repeat(4, 1fr)` ব্যবহার করে ৪টি সমান কলাম তৈরি হয়েছে।


# 🚩 grid-auto-rows
---
### ✔️ example 01

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* ৩টি কলাম */
  grid-auto-rows: 150px; /* প্রতিটি অটো সারির উচ্চতা ১৫০px */
}
```

### ✔️ example 02

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* ৩টি কলাম */
  grid-auto-rows: 1fr; /* প্রতিটি অটো সারির উচ্চতা ১৫০px */
}
```


### ✔️ example 03 minmax

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; 
  /* ৩টি কলাম */
  grid-auto-rows: minmax(100px, 300px); 
  /* সারির উচ্চতা ১০০px থেকে ৩০০px এর মধ্যে থাকবে */
  gap: 10px;
}
```


# 🚩 grid-template-rows-columns
---
### ✔️ example 01

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* ৩টি সমান কলাম */
  grid-template-rows: 100px 100px; /* ২টি সমান সারি */
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
  <div class="grid-item">4</div>
  <div class="grid-item">5</div>
  <div class="grid-item">6</div>
  <div class="grid-item">7</div>
  <div class="grid-item">8</div>
</div>

```


![[grid04.png]]

### ✔️ example 02

```jsx
.grid-container {
  display: grid;
  grid-template-columns: 200px 1fr 3fr; 
  /* প্রথম কলাম 200px, দ্বিতীয় কলাম 1fr, তৃতীয় কলাম 3fr */
  grid-template-rows: 150px 200px 300px; 
  /* প্রথম সারি 150px, দ্বিতীয় সারি 200px,তৃতীয় সারি 300px
}

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
  <div class="grid-item">4</div>
  <div class="grid-item">5</div>
  <div class="grid-item">6</div>
  <div class="grid-item">7</div>
  <div class="grid-item">8</div>
  <div class="grid-item">9</div>
</div>
```


![[grid05.png]]


# 🚩 grid-template-rows-columns Combine
---

```jsx
.container {
  display: grid;
  grid-template: 100px 200px / 150px 1fr 100px; /*  rows and  columns */
}
```


# 🚩 grid-gap
---

### ✔️ example 01

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* ৩টি সমান কলাম */
  grid-template-rows: 100px 100px; /* ২টি সারি */
  
  grid-row-gap: 10px; /* সারির মধ্যে ১০px গ্যাপ */
  grid-column-gap: 10px; /* কলামের মধ্যে ১০px গ্যাপ */
}
```

### ✔️ example 02

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* ৩টি সমান কলাম */
  grid-template-rows: 100px 100px; /* ২টি সারি */
  
  grid-gap: 10px 10px; /* প্রথম মান সারির গ্যাপ, দ্বিতীয় মান কলামের গ্যাপ */
}
```

### ✔️ একক `gap` প্রপার্টি

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* ৩টি সমান কলাম */
  grid-template-rows: 100px 100px; /* ২টি সারি */
  
  gap: 10px; /* সারি ও কলামের গ্যাপ একসাথে ১০px */
}
```




---
                                                                    
---

# Properties of the children


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
    Properties of the Children
</h1>

| Property                | Description                                               |
| ----------------------- | --------------------------------------------------------- |
| **`grid-column-start`** | এটি নির্ধারণ করে যে গ্রিড আইটেমটি কোন কলাম থেকে শুরু হবে। |
| **`grid-column-end`**   | এটি নির্ধারণ করে যে গ্রিড আইটেমটি কোন কলামে শেষ হবে।      |
| **`grid-row-start`**    | এটি নির্ধারণ করে যে গ্রিড আইটেমটি কোন সারি থেকে শুরু হবে। |
| **`grid-row-end`**      | এটি নির্ধারণ করে যে গ্রিড আইটেমটি কোন সারিতে শেষ হবে।     |
|                         |                                                           |

### **`-1` এর ব্যবহার:**

- যখন আপনি **`-1`** ব্যবহার করেন, এটি গ্রিডের **শেষ** লাইনকে নির্দেশ করে।

# 🚩 grid-column-start & grid-column-end
---

```css

.grid-container {
  display: grid;
  grid-template-columns: 100px 200px 100px 200px; /* ৪টি কলাম */
  grid-template-rows: 100px 100px; /* ২টি সারি */
  gap: 10px;
}


.item1 {
  grid-column-start: 1; /* প্রথম কলাম থেকে শুরু */
  grid-column-end: 3;   /* তৃতীয় কলাম পর্যন্ত (১ম ও ২য় কলামে বিস্তৃত হবে) */
}

.item2 {
  grid-column-start: 2; /* দ্বিতীয় কলাম থেকে শুরু */
  grid-column-end: 4;   /* চতুর্থ কলাম পর্যন্ত (২য়, ৩য় ও ৪র্থ কলামে বিস্তৃত হবে) */
}

```


# 🚩 grid-row-start & grid-row-end
---

```css
.grid-container {
  display: grid;
  grid-template-columns: 100px 100px 100px; /* ৩টি কলাম */
  grid-template-rows: 100px 100px 100px; /* ৩টি সারি */
  gap: 10px;
}
.item1 {
  grid-row-start: 1;    /* প্রথম সারি থেকে শুরু */
  grid-row-end: 3;     /* তৃতীয় সারি পর্যন্ত (১ম ও ২য় সারিতে বিস্তৃত হবে) */
}
.item2 {
  grid-row-start: 2; /* দ্বিতীয় সারি থেকে শুরু */
  grid-row-end: 4;   /* চতুর্থ সারি পর্যন্ত (২য় ও ৩য় সারিতে বিস্তৃত হবে) */
}
```

<h1 style="font-family: 'Times New Roman', Times, serif; font-size: 30px; color: #1ABC9C; text-align: center; border-bottom: 2px solid #1ABC9C;">
     Total grid part
</h1>

```css

.grid-container { 
  display: grid;
  grid-template-columns: 100px 100px 100px; /* ৩টি কলাম, প্রতিটি ১০০px */
  grid-template-rows: 100px 100px 100px; /* ৩টি সারি, প্রতিটি ১০০px */
  gap: 10px; 
}

/* Item 1 Setup */
.item1 { 
  grid-column: 1 / 3; /* প্রথম কলাম থেকে তৃতীয় কলাম পর্যন্ত বিস্তৃত হবে */
  grid-row: 1 / 3; /* প্রথম সারি থেকে তৃতীয় সারি পর্যন্ত বিস্তৃত হবে */
}

/* Item 2 Setup */
.item2 { 
  grid-column: 2 / 4; /* দ্বিতীয় কলাম থেকে চতুর্থ কলাম পর্যন্ত বিস্তৃত হবে */
  grid-row: 2 / 4; /* দ্বিতীয় সারি থেকে তৃতীয় সারি পর্যন্ত বিস্তৃত হবে */
}

```



---
                                                                    
---

