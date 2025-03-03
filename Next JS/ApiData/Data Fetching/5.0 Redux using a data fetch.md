![[next018.png]]

📗 Store
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

📗 Provider
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

📗 Layout
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


**📗 API** 
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


**📗 Fetch API**
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
