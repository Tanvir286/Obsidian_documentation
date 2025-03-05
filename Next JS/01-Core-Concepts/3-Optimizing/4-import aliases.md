In JavaScript (and particularly in a Node.js or Next.js environment), you can use **import aliases** to simplify the import paths in your project. Instead of using long, relative paths (e.g., `../../../components/Button`), you can define aliases like `@components/Button`.

#### 🔶Create a `jsconfig.json` file in the root directory of your project:

 ```js
 {
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@components/*": ["components/*"],
      "@utils/*": ["utils/*"],
      "@styles/*": ["styles/*"]
    }
  }
}

// Instead of using:
import Button from '../../../components/Button';
// Use:
import Button from '@components/Button';
```

### 🔶my own file project:

```js
{
  "compilerOptions": {
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}

import One from "@/assets/one.jpg";
```
