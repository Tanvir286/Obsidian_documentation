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

যখন আমি npm run bulid করব, তখন static content html file create করে রাখে। তখন যদি cache দেই , তাহলে data cache করে রাখে,by default cache  করে রাখে । route সহ static file তৈরি করে দেই .

![[next006.png]]

💯 npm start দিয়ে production mood on করে । production mood run করার সময় যদি code  change করা হয়, তা change হবে না । আবার build করতে হবে ।

**🔒** তবে আবার new করে build করে আবার npm start করা অনেক বড় সমস্যা, এত বার data change হবে যে নতুন করে  বার বার build  করা সম্ভব না।তার জন্য  revalidation যুক্ত করলে,সমস্যা সমাধান।

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

you can use the `next.revalidate` option provided by Next.js. This is particularly useful for pages that require periodic updates to their data.