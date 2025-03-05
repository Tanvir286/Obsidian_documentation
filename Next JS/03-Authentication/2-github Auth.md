
### 1️⃣  Provider Add

```ts
import { NextAuthOptions } from "next-auth"
import GitHubProvider from "next-auth/providers/github";

export const authOptions:NextAuthOptions = {
  providers: [
    GitHubProvider({
        clientId: process.env.GITHUB_ID as string,
        clientSecret: process.env.GITHUB_SECRET as string,
      })
  ],
}
```

### 2️⃣  .env file
![[Next020.png]]
```ts
GITHUB_ID= Ov23liGw50FDXrnTqqIh
GITHUB_SECRET=5b86e80f8c6f1d9571d85ccbfddd1e883cb12e58
```


### 3️⃣  Onclick Add

```js
import { signIn } from "next-auth/react";
const LoginPage = () => {

  return (

    <div className="my-10">
       <button className="btn btn-circle"
           onClick={() => signIn("github",{
                callbackUrl: "http://localhost:3000/dashboard",
               })}
            >
              <Image
                src="https://cdn-icons-png.flaticon.com/512/25/25231.png"
                width={35}
                height={35}
                alt="github logo"
              />
            </button>
    </div>
  );
};
export default LoginPage;
```

now Cookies add All information

![[Next021.png]]

## ♕ Show User


#### 4️⃣  secret add with env

```ts
import { NextAuthOptions } from "next-auth"
import GitHubProvider from "next-auth/providers/github";

export const authOptions:NextAuthOptions = {

  providers: [
    GitHubProvider({
        clientId: process.env.GITHUB_ID as string,
        clientSecret: process.env.GITHUB_SECRET as string,
      })
  ],
  secret: process.env.NEXTAUTH_SECRET,
}
```

```ts
GITHUB_ID= Ov23liGw50FDXrnTqqIh
GITHUB_SECRET=5b86e80f8c6f1d9571d85ccbfddd1e883cb12e58
NEXTAUTH_SECRET=abc
```

#### 5️⃣  Page View

```ts
import { authOptions } from "@/utils/authOption";
import { getServerSession } from "next-auth"; 

const DashboardPage = async () => {
  const session = await getServerSession(authOptions);
  const { name, email, image } = session?.user || {};

  return (

    <div className="text-center mt-10">
      <h1 className="text-4xl">Welcome To {name || "Dashboard"}</h1>
      <div className="mt-4">
        {email && <p className="text-lg">Email: {email}</p>}
        {image && (
          <img
            src={image}
            alt={name || "User Image"}
            className="w-20 h-20 rounded-full mx-auto mt-4"
          />
        )}
      </div>
    </div>
  );
};
export default DashboardPage;
```


![[Next022.png]]