# 🚀 Astro Test Blog

This is a **test blog** built with [Astro](https://astro.build), designed to explore Astro’s capabilities for content-driven websites. The blog supports **Markdown/MDX-based posts**, a dynamic routing system, and **RSS feed generation**.

## 📌 Features

- 📄 **Markdown & MDX Support** – Write posts in `.md` or `.mdx` format.
- 🔗 **Dynamic Routing** – Blog posts are generated dynamically from the `/posts` directory.
- 🎨 **Custom Layouts** – Uses `MainLayout.astro` and `BlogLayout.astro` for a structured content experience.
- 📱 **RSS Feed Integration** – Easily generate an RSS feed for blog syndication.
- 🌙 **Dark Mode Ready** – Styled with a sleek, modern dark theme.

---

## 💂️ Project Structure

```
/src
 ├── /assets                  # Static assets (icons, background images, post images)
 │   ├── astro.svg
 │   ├── background.svg
 │   ├── post-01.png
 │   ├── post-02.png
 │   ├── post-03.png
 │   ├── post-04.png
 │   ├── post-05.png
 │
 ├── /components              # Reusable UI components for blog posts
 │   ├── BlogPost.astro       # Individual blog post preview component
 │   ├── TypeBlogPost.astro   # Handles blog post previews dynamically
 │   ├── Welcome.astro        # Welcome component with introductory info
 │
 ├── /config
 │   ├── site-config.ts       # Configuration file for site settings
 │
 ├── /content
 │   ├── /blog                # Blog content storage
 │   ├── config.ts            # Blog settings configuration
 │
 ├── /layouts                 # Layout components for pages and posts
 │   ├── BlogLayout.astro     # Layout for individual blog posts
 │   ├── MainLayout.astro     # Base layout for the website
 │
 ├── /pages                   # Astro pages
 │   ├── /images              # Folder for storing images (if needed)
 │   ├── /posts               # Active blog posts
 │   ├── /posts-old           # Archive for old blog posts
 │   ├── blog-file-system.astro  # Blog page displaying posts
 │   ├── index.astro          # Homepage listing all blog posts
 │
 ├── /styles
 │   ├── blog.css             # Custom styling for blog pages
 │
 ├── /utils
 │   ├── formatter.ts         # Utility for formatting dates
```

---

## 🚀 Getting Started

### **1️⃣ Install Dependencies**
Make sure you have **Node.js** installed, then run:

```sh
npm install
```

### **2️⃣ Run the Blog Locally**
Start the Astro development server:

```sh
npm run dev
```

This will launch the blog at `http://localhost:4321` (or another port if already in use).

---

## 📱 RSS Feed Setup

This blog supports **RSS feed generation**, allowing users to subscribe via feed readers.

### **How to Generate an RSS Feed**

1. **Install the RSS Plugin (if not installed)**
   ```sh
   npm install @astro/rss
   ```
   
2. **Create an RSS Feed File**
   Add an `rss.xml.js` file inside `/pages/api` (or similar):

   ```js
   import rss from '@astro/rss';
   import { getCollection } from 'astro:content';

   export async function get() {
       const posts = await getCollection('blog');

       return rss({
           title: "Jordi's Blog",
           description: "A test blog powered by Astro",
           site: "https://yourblogdomain.com",
           items: posts.map((post) => ({
               title: post.data.title,
               link: `/posts/${post.slug}`,
               pubDate: new Date(post.data.date),
               description: post.data.description,
           })),
       });
   }
   ```

3. **Access the RSS Feed**
   Once deployed, your RSS feed will be available at:

   ```
   https://yourblogdomain.com/rss.xml
   ```

   Users can subscribe by adding this URL to their feed reader.

---

## 💯 Deployment

Deploy your Astro blog using **Netlify, Vercel, or GitHub Pages**.

### **Netlify**
1. Connect your GitHub repo to [Netlify](https://app.netlify.com/).
2. Set the **build command**:  
   ```
   npm run build
   ```
3. Set the **publish directory** to `dist/`.
4. Deploy 🚀.

### **Vercel**
1. Install the **Vercel CLI**:
   ```sh
   npm install -g vercel
   ```
2. Deploy:
   ```sh
   vercel
   ```

Your blog will be live instantly!

---

## 📝 Notes
- Make sure your `astro.config.mjs` is configured to support **RSS feeds**.
- To add new blog posts, create `.md` or `.mdx` files inside `/posts`.
- Ensure `astro:content` is properly set up to fetch and render blog posts.

🚀✨
