[Middleware](https://next-auth.js.org/configuration/nextjs#middleware)

<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 20px; font-weight: bold;text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 Create Middleware File
    </h1>

![[auth07.png]]

```ts
export { default } from "next-auth/middleware"
export const config = { matcher: ["/dashboard","/"] }
```

✔️ ইউজার `/dashboard` বা `/` (হোমপেজ) এ গেলে **middleware চেক করবে** ইউজার লগ ইন করেছে কিনা।  

💯 **যদি ইউজার লগ ইন করা না থাকে**, তাহলে middleware **তাকে `/login` পেজে রিডাইরেক্ট করবে**।  **যদি ইউজার লগ ইন করা থাকে**, তাহলে সে **পেজ দেখতে পারবে**।

<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 20px; font-weight: bold;text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 Provider Page Add
    </h1>

```js
import { NextAuthOptions } from "next-auth"
import GitHubProvider from "next-auth/providers/github";
import GoogleProvider from "next-auth/providers/google";

export const authOptions:NextAuthOptions = {

  providers: [
    GitHubProvider({
        clientId: process.env.GITHUB_ID as string,
        clientSecret: process.env.GITHUB_SECRET as string,
      }),

      GoogleProvider({
        clientId: process.env.GOOGLE_ID as string,
        clientSecret: process.env.GOOGLE_SECRET as string,
      })
  ],
  pages:{
    signIn: "/login",
  },
  secret: process.env.NEXTAUTH_SECRET,
}
```

- এই middleware `/dashboard` এবং `/` (হোম পেজ) রক্ষিত (protected) রাখবে।
- অর্থাৎ, যদি ব্যবহারকারী **লগ ইন না থাকে**, তাহলে তাকে `/login` পেজে পাঠিয়ে দেওয়া হবে।