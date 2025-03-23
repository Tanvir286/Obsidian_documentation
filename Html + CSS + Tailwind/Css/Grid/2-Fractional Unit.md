`1fr` (Fractional Unit) CSS Grid এর একটি ইউনিট যা গ্রিড কন্টেইনারের উপলব্ধ স্থানকে ভাগ করে নিতে ব্যবহৃত হয়। `fr` ইউনিট এমন একটি পরিমাণ বোঝায় যা কন্টেইনারের মোট স্থানকে ভাগ করে।

### **1fr এর অর্থ:**

☑`1fr` এর মান হল কন্টেইনারের প্রস্থ বা উচ্চতার এক ভাগ।
☑এটি একটি অনুপাত ভিত্তিক ইউনিট, যা কন্টেইনারের উপলব্ধ স্থান অনুযায়ী নিজেকে মানিয়ে নেয়।
☑যদি আপনি `1fr` ব্যবহার করেন, তাহলে এটি কন্টেইনারের বাকি অংশের মধ্যে সমানভাবে স্থান ভাগ করে নেয়।


### Example: একক কলাম 1fr ব্যবহার

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr; 
  /* এক কলাম, যা কন্টেইনারের সবটুকু প্রস্থ নেবে */

}

.grid-item {
  background-color: lightcoral;
  text-align: center;
  padding: 20px;
}
```

```css
<div class="grid-container">
  <div class="grid-item">Item 1</div>
</div>
```

এখানে একমাত্র কলামটি কন্টেইনারের সমস্ত প্রস্থ নেবে, যেহেতু এটি একমাত্র কলাম এবং `1fr` এর মাধ্যমে সমস্ত স্থান নেবে।


### Example: একাধিক কলাম 1fr ব্যবহার

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3টি সমান কলাম */
}

.grid-item {
  background-color: lightblue;
  text-align: center;
  padding: 20px;
}
```

```css
<div class="grid-container">
  <div class="grid-item">Item 1</div>
  <div class="grid-item">Item 2</div>
  <div class="grid-item">Item 3</div>
</div>
```

এখানে তিনটি সমান কলাম তৈরি হবে, এবং কন্টেইনারের প্রস্থ সমানভাবে তিনটি অংশে ভাগ হয়ে যাবে, কারণ প্রতিটি কলাম `1fr` ব্যবহার করছে।


### Example: কলাম এবং সারি সংমিশ্রণ

```css
.grid-container {
  display: grid;
  grid-template-columns: 2fr 1fr; /* প্রথম কলাম 2fr, দ্বিতীয় কলাম 1fr */
  grid-template-rows: 1fr 2fr; /* প্রথম সারি 1fr, দ্বিতীয় সারি 2fr */
  gap: 10px;
}

.grid-item {
  background-color: lightgreen;
  text-align: center;
  padding: 20px;
}

```

```css
<div class="grid-container">
  <div class="grid-item">Item 1</div>
  <div class="grid-item">Item 2</div>
  <div class="grid-item">Item 3</div>
  <div class="grid-item">Item 4</div>
</div>
```

এখানে প্রথম কলামটি কন্টেইনারের ২/৩ স্থান নেবে, এবং দ্বিতীয় কলামটি ১/৩ স্থান নেবে। সারিগুলোর মধ্যে প্রথমটি ১/৩ স্থান নেবে এবং দ্বিতীয়টি ২/৩ স্থান নেবে।
