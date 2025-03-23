
<<<<<<< HEAD
<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 30px; font-weight: bold; text-transform: uppercase; text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 Provider Add
    </h1>
[Github](https://next-auth.js.org/providers/github)

![[auth04.png]]
=======
### 1️⃣  Provider Add
>>>>>>> 0aefa4ccfb4297cbddde6a1fa2d12b8b0cc7c5b1

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

<<<<<<< HEAD
<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 30px; font-weight: bold;  text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 .env file
    </h1>

=======
### 2️⃣  .env file
>>>>>>> 0aefa4ccfb4297cbddde6a1fa2d12b8b0cc7c5b1
![[Next020.png]]
```ts
GITHUB_ID= Ov23liGw50FDXrnTqqIh
GITHUB_SECRET=5b86e80f8c6f1d9571d85ccbfddd1e883cb12e58
```

<<<<<<< HEAD
<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 30px; font-weight: bold;  text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 onClick add
    </h1>
=======

### 3️⃣  Onclick Add
>>>>>>> 0aefa4ccfb4297cbddde6a1fa2d12b8b0cc7c5b1

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

<<<<<<< HEAD
---

  <h1 style="
        font-size: 70px;
        font-weight: bold;
        text-transform: uppercase;
        text-align: center;
        background: linear-gradient(135deg, #6a11cb, #2575fc); /* Cool purple and blue */
        background-size: 400%;
        color: transparent;
        -webkit-background-clip: text;
        text-shadow: 0 0 10px rgba(38, 110, 255, 0.6), 0 0 15px rgba(38, 110, 255, 0.8); 
        letter-spacing: 4px;
        border: 3px solid transparent;
        padding: 20px 40px;
        border-radius: 10px;
        box-shadow: 0 0 20px rgba(38, 110, 255, 0.5);
        position: relative;
        z-index: 1;
    ">
         Show User 
    </h1>


<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 30px; font-weight: bold;  text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 secret add with env
    </h1>
=======
## ♕ Show User


#### 4️⃣  secret add with env
>>>>>>> 0aefa4ccfb4297cbddde6a1fa2d12b8b0cc7c5b1

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
<<<<<<< HEAD
  secret: process.env.NEXTAUTH_SECRET,  //new
=======
  secret: process.env.NEXTAUTH_SECRET,
>>>>>>> 0aefa4ccfb4297cbddde6a1fa2d12b8b0cc7c5b1
}
```

```ts
GITHUB_ID= Ov23liGw50FDXrnTqqIh
GITHUB_SECRET=5b86e80f8c6f1d9571d85ccbfddd1e883cb12e58
<<<<<<< HEAD

NEXTAUTH_SECRET=abc // new 
```

<h1 style="background: linear-gradient(45deg, #ff8c00, #ff0080); -webkit-background-clip: text; color: transparent; font-size: 30px; font-weight: bold;  text-align: center; padding: 10px 20px; border-bottom: 3px solid #ff0080;">
        🚀 Page View
    </h1>
=======
NEXTAUTH_SECRET=abc
```

#### 5️⃣  Page View
>>>>>>> 0aefa4ccfb4297cbddde6a1fa2d12b8b0cc7c5b1

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


<<<<<<< HEAD
![[Next022.png]]

### `getServerSession` কীভাবে কাজ করে?

`getServerSession` ফাংশনটি Next.js এর **API routes** বা **server-side components** (যেমন `getServerSideProps` বা **server components**) এ ব্যবহৃত হয়। এটি আপনার NextAuth কনফিগারেশন ব্যবহার করে সেশন ডেটা ফিরিয়ে দেয়।

#### **কীভাবে কাজ করে:**
 `getServerSession(authOptions)` এই ফাংশনটি আপনার `authOptions` কনফিগারেশন অনুসারে সেশন ডেটা ফেরত দেয়।
- এর মাধ্যমে আপনি ইউজারের তথ্য যেমন নাম, ইমেইল, ছবি ইত্যাদি ব্যবহার করতে পারেন।
- এই ফাংশনটি **server-side** রান করে, মানে এটি সার্ভারে ইউজারের সেশন যাচাই করবে এবং এরপর আপনি সেই তথ্য ক্লায়েন্টকে দেখাতে পারবেন


  <h1 style="
        font-size: 70px;
        font-weight: bold;
        text-transform: uppercase;
        text-align: center;
        background: linear-gradient(135deg, #6a11cb, #2575fc); /* Cool purple and blue */
        background-size: 400%;
        color: transparent;
        -webkit-background-clip: text;
        text-shadow: 0 0 10px rgba(38, 110, 255, 0.6), 0 0 15px rgba(38, 110, 255, 0.8); 
        letter-spacing: 4px;
        border: 3px solid transparent;
        padding: 20px 40px;
        border-radius: 10px;
        box-shadow: 0 0 20px rgba(38, 110, 255, 0.5);
        position: relative;
        z-index: 1;
    ">
         Logout 
    </h1>

যেহেতু  use client ভিতর data  fetching করা যায় না,সেহেতু use client যেগুলো তে থাকবে data props মাধ্যমে আনতে হবে।

![[auth05.png]]


```jsx
import Navbar from "@/components/shared/Navbar";
import { getServerSession } from "next-auth";
import { authOptions } from "@/utils/authOption";

export const metadata: Metadata = {
  title: "Next Auth",
  description: "Generated by create next app",
};

export default async function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {

 const session = await getServerSession(authOptions

  return (

    <html lang="en" data-theme="light">
      <body>
        <Navbar session={session}/>
        <div className="min-h-screen w-[90%] mx-auto">{children}</div>
      </body>
    </html>
  );
}
```

যদি ব্যবহারকারী লগইন করা থাকে, তাহলে **লগআউট** বোতাম দেখাও, আর যদি লগইন না করা থাকে, তাহলে **লগইন** বোতাম দেখাও।

```jsx
"use client"
import Link from "next/link";
import { signOut } from "next-auth/react";

type UserProps = {
  user?: {
    name?: string | null | undefined;
    email?: string | null | undefined;
    image?: string | null | undefined;
  };
};

const Navbar = ({ session }: { session: UserProps | null }) => {
  return (
    <div className="navbar bg-base-100 border-b w-[90%] mx-auto">
      
      <div className="navbar-end">
        {session?.user ? (
          <>
            <div className="flex items-center space-x-2">
              {session.user.image && (
                <img
                  src={session.user.image}
                  alt="User Avatar"
                  className="w-8 h-8 rounded-full"
                />
              )}
              <span className="text-sm font-medium">
                {session.user.name || "User"}
              </span>
            </div>
            <button
              onClick={() => signOut()}
              className="btn btn-errorpx-5"
            >
              Logout
            </button>
          </>
        ) : (
          <Link
            href="/login"
            className="btn btn-accent btn-outwhite rounded-full px-5"
          >
            Login
          </Link>
        )}
      </div>
    </div>
  );
};
export default Navbar;
```

=======
![[Next022.png]]
>>>>>>> 0aefa4ccfb4297cbddde6a1fa2d12b8b0cc7c5b1
