![[next018.png]]

```js
npm install @reduxjs/toolkit react-redux
```


##  ==📗 Store  

old
```js
import { configureStore } from '@reduxjs/toolkit'

export const store = configureStore({
  reducer: {},
})

// Infer the `RootState` and `AppDispatch` types from the store itself
export type RootState = ReturnType<typeof store.getState>
// Inferred type: {posts: PostsState, comments: CommentsState, users: UsersState}
export type AppDispatch = typeof store.dispatch
```

new
```ts
import { configureStore } from '@reduxjs/toolkit'
import { baseApi } from './api/baseApi'
  
export const store = configureStore({
  reducer: {
   [baseApi.reducerPath]: baseApi.reducer,
  },
    middleware: (getDefaultMiddleware) =>
       getDefaultMiddleware().concat(baseApi.middleware),
})

export type RootState = ReturnType<typeof store.getState>
export type AppDispatch = typeof store.dispatch
```

## ==📗 Provider==

```ts
"use client"
import { store } from "@/redux/store";
import { Provider } from "react-redux";

const Providers = ({ children } : { children:React.ReactNode } ) => {

    return (
        <Provider store={store}>
            {children}
        </Provider>
    );
};
export default Providers;
```

## ==📗 Layout ==

```ts
import Providers from './../lib/Provider';

const roboto = Roboto({
  weight: "400",
  subsets: ["latin"],
  display: "swap",
})
 

export default function RootLayout({
  children,
}: Readonly<{ children: React.ReactNode;}>) {

  return (
    <Providers>
        <html lang="en" data-theme="light">
      <body className={roboto.className}>
        <Header />
          <div className="min-h-screen">{children}</div>
        <Footer />
      </body>
    </html>
    </Providers>
  );
}
```


## ==📗React RTK Query API ==


Old

```js
import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query/react'
import type { Pokemon } from './types'


export const pokemonApi = createApi({
  reducerPath: 'pokemonApi',
  baseQuery: fetchBaseQuery({ baseUrl: 'https://pokeapi.co/api/v2/' }),
  endpoints: (build) => ({
    getPokemonByName: build.query<Pokemon, string>({
      query: (name) => `pokemon/${name}`,
    }),
  }),
})

export const { useGetPokemonByNameQuery } = pokemonApi
```

New

```ts
import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query/react'

export const baseApi = createApi({
  reducerPath: 'Api',
  baseQuery: fetchBaseQuery({ baseUrl: 'http://localhost:5000/' }),
  endpoints: (builder) => ({
    getBlogs: builder.query({
      query: () => `/blogs`,
    }),
  }),
})
export const { useGetBlogsQuery } = baseApi
```

---


<h1 style="
    background: linear-gradient(90deg, #ff7e5f, #feb47b);
    -webkit-background-clip: text;
    color: transparent;
    font-size: 3rem;
    font-weight: bold;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    letter-spacing: 2px;
    text-align: center;
    padding: 10px;
">
    Fetch API
</h1>
---


```ts
"use client"
import { useGetBlogsQuery } from '@/redux/api/baseApi';
const Blogspage = () => {

   const { data:blogs, error, isLoading } = useGetBlogsQuery('');

    return (
        <div className='w-[90%] mx-auto'>
            <div className='grid grid-cols-3  gap-5 my-14'>
                {blogs?.map((blog:Blog) => (
                    <BlogCard blog={blog} key={blog.id} />
                ))}
            </div>
        </div>
    );
};
export default Blogspage;
```
