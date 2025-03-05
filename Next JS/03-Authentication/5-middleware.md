## 1️⃣ source file

![[next019.png]]
## 2️⃣ middleware

```ts
export { default } from "next-auth/middleware"
export const config = { matcher: ["/dashboard","/"] }
```

## 3️⃣ Provider

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
