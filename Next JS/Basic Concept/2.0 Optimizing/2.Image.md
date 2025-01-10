The Next.js [`<Image>`](https://nextjs.org/docs/app/building-your-application/optimizing/images) component extends the HTML `<img>` element to provide:

- **Size optimization:** Automatically serving correctly sized images for each device, using modern image formats like WebP and AVIF.
- **Visual stability:** Preventing [layout shift](https://web.dev/articles/cls)

- automatically when images are loading.
- **Faster page loads:** Only loading images when they enter the viewport using native browser lazy loading, with optional blur-up placeholders.
- **Asset flexibility:** Resizing images on-demand, even images stored on remote servers.


0.0 next.config.js
```js
/** @type {import('next').NextConfig} */
const nextConfig = {
    images: {
        remotePatterns: [
            {
                protocol: 'https',
                hostname: '**',
            },
        ],
    },
};  
module.exports = nextConfig;
```

1.1 Image add local and url
```js
import React from 'react';
import Image from 'next/image';
import One from "../../assets/one.jpg"
const GalleryPage = () => {
    return (
        <div>
           <h1 className='text-5xl'>Image Optimization</h1>
            <div className='text-center'>
              <Image
                src="https://plus.unsplash.com/premium"
                alt="Next.js Image Optimization"
                width={500}
                height={400}/>   
                
               <Image
                src={One}
                alt="Next.js Image Optimization"
                width={500}
                height={400}/>

              </div>
        </div>
    );
};
export default GalleryPage;
```

