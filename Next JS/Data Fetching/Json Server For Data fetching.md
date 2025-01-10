
<div>
    <h2>
     Data Fetching কাজ করে Asyn ভেতর,
     আর এটা শুধুমাএ Server Component কাজ করবে,
     "use client"  কাজ করবে না 
    </h5>

</div>

❶ Json NPM Link : [link](https://www.npmjs.com/package/json-server)
 
```
npm install json-server
```

❷ Usage: Create a `db.json`

```js
{
  "posts": [
    { "id": "1", "title": "a title", "views": 100 },
    { "id": "2", "title": "another title", "views": 200 }
  ],
  "comments": [
    { "id": "1", "text": "a comment about post 1", "postId": "1" },
    { "id": "2", "text": "another comment about post 1", "postId": "1" }
  ],
  "profile": {
    "name": "typicode"
  }
}
```

### Alternative port ( run different server server )

❸ Now package.json scripts add

```js
"scripts": {
    "dev": "next dev",
    "json-server": "json-server --watch db.json --port 5000",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
```

Run Code
```js
npm run json-server
```

এরপর ঐ URL hit করলে value পাওয়া যাবে । যা যেকোনো place fetch করা যাবে । server all time সবসমায় অন্য terminal run থাকতে হবে ।

```js
export const metadata = {
  title: "Home",
  description: "This is home page",
};

const Home = async() => {

 const res = await fetch('http://localhost:5000/shoes');
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
