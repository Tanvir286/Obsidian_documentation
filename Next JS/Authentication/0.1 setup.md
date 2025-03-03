
### 1️⃣  Install
```ts
npm install next-auth
```

### 2️⃣ Route add  

⍚ /app/api/auth/[...nextauth]/route.ts

```ts
import NextAuth from "next-auth"

const handler = NextAuth()

export { handler as GET, handler as POST }
```


### 3️⃣  Provider Add

⍚ /app/utils/authOption.ts

```ts
import { NextAuthOptions } from "next-auth"

export const authOptions:NextAuthOptions = {

  providers: [

  ],
}
```

### 4️⃣  Provider Add Route

```ts
import { authOptions } from "@/utils/authOption"
import NextAuth from "next-auth"

const handler = NextAuth(authOptions)
  
export { handler as GET, handler as POST }
```