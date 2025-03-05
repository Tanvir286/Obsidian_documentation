
###  I. CSS Modules ব্যবহার করা:

CSS Modules ব্যবহার করে আপনি কম্পোনেন্ট-স্পেসিফিক CSS লিখতে পারেন। এটি স্কোপড CSS, অর্থাৎ এক কম্পোনেন্টের CSS অন্য কম্পোনেন্টে প্রভাব ফেলবে না।



###### 🔶`styles` ফোল্ডারে একটি CSS Module ফাইল তৈরি করুন, যেমন `Home.module.css`:

 ```js
.title {
  color: blue;
  font-size: 2rem;
}

.description {
  color: green;
  font-size: 1.2rem;
}
```

##### 🔶এই CSS Module কে আপনার কম্পোনেন্টে ইম্পোর্ট করুন এবং ব্যবহার করুন:

```js
import styles from '../styles/Home.module.css';

export default function Home() {
  return (
    <div>
      <h1 className={styles.title}>Welcome to Next.js!</h1>
      <p className={styles.description}>This is a sample page with CSS Modules.</p>
    </div>
  );
}
```


### II.   Inline CSS ব্যবহার করা:

```js
export default function Home() {
  return (
    <div style={{ backgroundColor: '#f0f0f0', padding: '20px' }}>
      <h1 style={{ color: 'blue' }}>Welcome to Next.js!</h1>
      <p style={{ color: 'green' }}>This is a sample page with inline CSS.</p>
    </div>
  );
}
```


