
<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 50px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀Install
    </h1>

```ts
npm install next-auth
```

<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 50px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 Route Add
    </h1>

 <div style="background-color: #252526; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px rgba(0, 0, 0, 0.5); font-size: 18px; max-width: 80%; white-space: nowrap;">
        <span style="color: #9cdcfe;">app</span> / 
        <span style="color: #9cdcfe;">api</span> / 
        <span style="color: #ce9178;">[</span><span style="color: #dcdcaa;">...nextauth</span><span style="color: #ce9178;">]</span> / 
        <span style="color: #dcdcaa;">route.ts</span>
    </div>

![[auth01.png]]

```ts
import NextAuth from "next-auth"

const handler = NextAuth()

export { handler as GET, handler as POST }
```

<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 30px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 Auth option
    </h1>


<div style="background-color: #252526; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px rgba(0, 0, 0, 0.5); font-size: 18px; max-width: 80%; white-space: nowrap;">
        <span style="color: #ffcc00;">⍚</span>  
        <span style="color: #9cdcfe;">/app</span> / 
        <span style="color: #9cdcfe;">utils</span> / 
        <span style="color: #dcdcaa;">authOption.ts</span>
    </div>

![[auth02.png]]

```ts
import { NextAuthOptions } from "next-auth"

export const authOptions:NextAuthOptions = {

  providers: [

  ],
}
```



<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 30px; font-weight: bold; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        Route Add Authoption
    </h1>

![[auth03.png]]

```ts
import { authOptions } from "@/utils/authOption"
import NextAuth from "next-auth"

const handler = NextAuth(authOptions)
  
export { handler as GET, handler as POST }
```

