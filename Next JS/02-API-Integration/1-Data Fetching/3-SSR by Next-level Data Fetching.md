To prevent caching entirely and always fetch fresh data on every request, you can use the `cache: "no-store"` option in the `fetch` request.

```js
export const metadata = {
  title: "Home",
  description: "This is home page",
};

const Home = async () => {
  const res = await fetch('http://localhost:5000/shoes', {
    cache: "no-store", // Always fetch fresh data
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

User request অনুসারে, server থেকে নতুন data fetching হয়ে html content create হয়ে তারপর browser আসবে । build time এ html content create হয়না।request অনুসারে server থেকে নতুন content browser visible হয়।

![[next003.png]]

💯 যখন নতুন করে route hit হবে,তখনি latest data দেখাবে।

