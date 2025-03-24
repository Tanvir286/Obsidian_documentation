
| Question No | Topic                                   |
| ----------- | --------------------------------------- |
| 1           | **Button কে কিভাবে  সেন্টার আনা যাবে ** |
| 2           | **Image কে কিভাবে  সেন্টার আনা যাবে **  |
|             |                                         |
|             |                                         |
|             |                                         |

#  01: Button কে কিভাবে সেন্টার আনা যাবে

<body style="font-family: 'Roboto', sans-serif; margin: 0; padding: 0; display: flex; justify-content: center; align-items: center; height: 10vh; background-color: #e2e8f0;">
  <header style="background: #6a89cc; color: #fff; padding: 20px 30px; text-align: center; border-radius: 12px; box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15); max-width: 700px; width: 100%;">
    <h1 style="font-size: 22px; font-weight: 700; margin: 0; color: #fff;text-align: center; ">Button কে কিভাবে  সেন্টার আনা যাবে </h1>
  </header>
</body>

####  ➥ 01 div class text center kore

```js
<div className="text-center">
  <button className="">Click Me</button>
</div>

```
#### ➥ 02 mx-auto with block

```js
<button className="block mx-auto">Click Me</button>
```

#### ➥ 03 flex with justify-center

```js
<div className="flex justify-center">
  <button>Click Me</button>
</div>
```

#### ➥ 03 grid with place-items-center

```js
<div className="grid place-items-center">
  <button>Click Me</button>
</div>

```

**`place-items-center`**: বাটনটিকে উভয় দিক থেকে (হরিজেন্টালি এবং ভারটিকালি) সেন্টার করবে।



# 02: Image কে কিভাবে সেন্টার আনা যাবে

<body style="font-family: 'Roboto', sans-serif; margin: 0; padding: 0; display: flex; justify-content: center; align-items: center; height: 10vh; background-color: #e2e8f0;">
  <header style="background: #6a89cc; color: #fff; padding: 20px 30px; text-align: center; border-radius: 12px; box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15); max-width: 700px; width: 100%;">
    <h1 style="font-size: 22px; font-weight: 700; margin: 0; color: #fff;text-align: center; ">image কে কিভাবে  সেন্টার আনা যাবে </h1>
  </header>
</body>

####  ➥ 01 `text-center`: তবে, ইমেজকে **`inline-block`** করতে হবে

```js
<div className="text-center">
  <img src="image.jpg" alt="example" className="inline-block" />
</div>
```
####  ➥ 02 mx-auto: তবে, ইমেজকে **`block`** করতে হবে

```js
<img src="image.jpg" alt="example" className="block mx-auto" />
```

#### ➥ 03 flex with justify-center

```js
<div className="flex justify-center">
  <img src="image.jpg" alt="example" className="w-1/2" />
</div>
```

#### ➥ 04 grid with place-items-center

```js
<div className="grid place-items-center h-64">
  <img src="image.jpg" alt="example" className="w-1/2" />
</div>
```

**`place-items-center`**: ইমেজকে সেন্টার করবে উভয় দিক দিয়ে (হরিজেন্টালি এবং ভারটিকালি)।


#### ➥ 05 Next.js `Image` কম্পোনেন্টের জন্য `object-center` ব্যবহার করা:

```js
import Image from "next/image";

const MyComponent = () => (
  <div className="relative w-64 h-64">
    <Image
      src="image.jpg"
      alt="example"
      layout="fill"
      className="object-cover object-center"
    />
  </div>
);

```

- **`object-cover`**: ইমেজটি কন্টেইনারকে কভার করবে। 
- **`object-center`**: ইমেজটিকে কন্টেইনারের মাঝে সেন্টার করবে।