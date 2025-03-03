
### 1️⃣ Google Provider 

```ts
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
  secret: process.env.NEXTAUTH_SECRET,
}
```

### 2️⃣ .env

```ts
GITHUB_ID= Ov23liGw50FDXrnTqqIh
GITHUB_SECRET=5b86e80f8c6f1d9571d85ccbfddd1e883cb12e58
  
GOOGLE_ID= 430679638850-qqn455dr4qimmoobu6e4aherconten
GOOGLE_SECRET=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

NEXTAUTH_SECRET=abc
```


### 3️⃣ Login page

```js
import { signIn } from "next-auth/react";
const LoginPage = () => {

  return (

    <div className="my-10">
       <button className="btn btn-circle"
           onClick={() => signIn("google",{
                callbackUrl: "http://localhost:3000/dashboard",
               })}
            >
              <Image
                src="https://cdn-icons-png.flaticon.com/512/25/25231.png"
                width={35}
                height={35}
                alt="google logo"
              />
            </button>
    </div>
  );
};
export default LoginPage;
```

