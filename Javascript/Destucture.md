
```ts
{ user: 
       { name: 'Tanvir Ahamed', 
         email: 'tanvirdiu200@gmail.com',
         image: 'https://avatars.githubusercontent.com/u/142485438?v=4' }
        }
```

Now 

```ts

 const { name, email, image } = session?.user || {};

or

 const { user } = session || {}; //

 const { name, email, image } = user || {};

```

- **Destructuring**:
    - Extract the `user` object from the `session`.
    - Further destructure `name`, `email`, and `image` from the `user` object.
- **Null Handling**:
    - Use `||` to provide default values (like `"Dashboard"` if `name` is not available).
- **Conditional Rendering**: 
    - Check if `email` and `image` exist before rendering their respective elements