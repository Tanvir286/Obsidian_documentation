
## 🚥 server post
```ts
"use server"
import { Blog } from "@/components/types";

export const createblog = async (data:Blog) =>{
    const res = await fetch("http://localhost:5000/blogs",{
        method: "POST",
        headers: {
           "Content-Type": "application/json",
        },
        body: JSON.stringify(data),
        cache: "no-store",
    });  
    const blogInfo = await res.json();
    return blogInfo;
}
```

## 🚥 form

```ts
"use client"
import { useForm } from "react-hook-form";
import { createblog } from './../../actions/createBlog';
  
type FormValues = {
  id: string;
  title: string;
  description: string;
  publish_date: string;
  author_name: string;
  blog_image: string;
  total_likes: string;
};

const CreateBlogForm = () => {
  
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm<FormValues>();

  const onSubmit = async (data: FormValues) => {
    console.log(data);
    const res = await fetch("http://localhost:5000/blogs");
    const blogs = await res.json();
    data.id = JSON.stringify(blogs.length + 1);
    data.total_likes = "100";



    try{
        const res = await createblog(data);
        console.log(res);
    }
    catch(err:any){
       console.log(err.message);
       throw new Error(err.messsage) 
   };


  return (
    <div className="my-10">
      <h1 className="text-center text-4xl">
        Post Your <span className="text-accent">Blog</span>
      </h1>
  
      <div className="hero min-h-screen">
        <div className="card w-[50%] shadow-xl bg-base-100">
          <form onSubmit={handleSubmit(onSubmit)} className="card-body">
            <div className="form-control">
              <label className="label">
                <span className="label-text">Title</span>
              </label>
              <input
                type="text"
                {...register("title")}
                placeholder="Title"
                className="input input-bordered"
                required
              />
            </div>
            <div className="form-control">
             <label className="label">
               <span className="label-text">Description</span>
              </label>
              <textarea
                {...register("description")}
                placeholder="Description"
                className="textarea textarea-bordered"
                required
              />
            </div>
            <div className="form-control">
              <label className="label">
               <span className="label-text">Publish Date</span>
              </label>
              <input
                {...register("publish_date")}
                type="date"
                className="input input-bordered"
                required
              />
            </div>
            <div className="form-control">
              <label className="label">
                <span className="label-text">Author Name</span>
              </label>
              <input
                type="text"
                {...register("author_name")}
                placeholder="Author Name"
                className="input input-bordered"
                required
              />
            </div>
            <div className="form-control">
              <label className="label">
                <span className="label-text">Blog Image</span>
              </label>
              <input
                type="url"
                {...register("blog_image")}
                placeholder="Image URL"
                className="input input-bordered"
                required
              />
            </div>
            <div className="form-control mt-6">
              <button type="submit" className="btn btn-accent btn-outline">
                Post
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  );
};
export default CreateBlogForm;
```