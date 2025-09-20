# Medium Clone
  <img src="https://skillicons.dev/icons?i=sentry,githubactions,supabase,vercel,vitest,typescript,prisma,postgres,docker,cloudflare,workers,vite,react,nodejs,tailwind"/>

Medium Clone is a feature-rich, production-ready blogging application inspired by Medium. It's built from the ground up with a modern, serverless, and type-safe technology stack, designed to be performant, scalable, and maintainable. This project serves as a comprehensive demonstration of advanced full-stack development practices, from database architecture to automated CI/CD pipelines.


**Live Demo:** [medium-clone-one-blush.vercel.app](https://medium-clone-one-blush.vercel.app/)

[![CI/CD Pipeline](https://github.com/sumitbhuia/medium-clone/actions/workflows/deploy.yml/badge.svg)](https://github.com/sumitbhuia/medium-clone/actions)


---

## 📸 Project Showcase
<img width="1285" height="660" alt="SIGNUP" src="https://github.com/user-attachments/assets/4681155c-d0f2-49ba-8476-db398470e1d4" />
<img width="1282" height="655" alt="SIGNIN" src="https://github.com/user-attachments/assets/85989d42-c5ca-4114-ad1f-1b335a25eb4b" />
<img width="1293" height="670" alt="ALL BLOGS" src="https://github.com/user-attachments/assets/fae59223-6e3d-4188-befd-3d8a21417148" />
<img width="1287" height="667" alt="BLOG" src="https://github.com/user-attachments/assets/3f244bcc-88b9-4495-af73-dafc96c7b32c" />
<img width="1285" height="664" alt="WRITE" src="https://github.com/user-attachments/assets/43598efa-4d39-4418-b0c9-001f84959d0b" />
<img width="1273" height="655" alt="EDIT" src="https://github.com/user-attachments/assets/5e772db2-ddb3-49f7-9635-0dffcfaff553" />
<img width="1287" height="665" alt="PROFILE" src="https://github.com/user-attachments/assets/5a39b606-fab4-45ce-8f57-b98fdff9ed04" />
<img width="1267" height="643" alt="CREATED" src="https://github.com/user-attachments/assets/d4ba1bb6-1982-4367-9e5f-e6eff8d6fca3" />
<img width="1279" height="655" alt="SAVED" src="https://github.com/user-attachments/assets/12322399-c6ae-44f4-b8be-e0ce3fb71ba3" />


<div align="center">
<img src="https://github.com/user-attachments/assets/fc759096-ad1d-443d-8d8f-380a9426faaa" alt="Mobile View" width="45%"/> 
<img src="https://github.com/user-attachments/assets/734156ac-5d4c-4473-871e-e243555544c7" alt="Homepage Feed" width="45%"/>
<img src="https://github.com/user-attachments/assets/d3e0641f-4c11-4811-9d6e-69dd1c10d339" alt="User Profile" width="45%"/>
<img src="https://github.com/user-attachments/assets/d011706d-a3bc-4be6-9cfa-b809f623043f" alt="Mobile View" width="45%"/>
<img src="https://github.com/user-attachments/assets/8a6bf53e-cbb2-40c4-9cc4-f64e84c31f2f" alt="Mobile View" width="45%"/> 
<img src="https://github.com/user-attachments/assets/0ef766a2-f6bb-4bee-a6c6-1817ae1e1d1b" alt="Blog Post Page" width="45%"/>

</div>




---

## ✨ Core Features


* **Full User Authentication:** Secure sign-up and sign-in with email/password and OAuth (Google), powered by Supabase Auth.
* **Rich Text Editor:** A beautiful and intuitive Tiptap-based editor for writing posts, complete with formatting options and support for syntax-highlighted code blocks.
* **Personalized "Following" Feed:** A custom, algorithm-driven feed that shows users the latest posts from authors they follow.
* **Interactive Engagements:** Users can clap for posts, create nested comments and replies, and bookmark articles for later reading, with all interactions updating optimistically for a seamless UX.
* **Real Image Uploads:** Users can upload and manage their own profile avatars and cover images, as well as featured images for their posts, using Supabase Storage.
* **Comprehensive User Profiles:** Public user profiles showcasing their posts, bio, and social stats.
* **AI-Powered Tagging:** Posts are automatically tagged using Google's Gemini AI if no manual tags are provided, improving content discovery.
* **Fully Responsive Design:** A clean, mobile-first UI built with Tailwind CSS that looks great on all devices.

---

## 🛠️ Technical Architecture & Stack

This project was built with a focus on modern, scalable, and developer-friendly technologies. The architecture is designed to be performant and cost-effective by leveraging serverless platforms.

### **Frontend (Vercel)**

The frontend is a dynamic and responsive single-page application built with a focus on performance and user experience.

* **Framework:** **React 18** with **Vite** for a lightning-fast development experience.
* **Language:** **TypeScript** for end-to-end type safety.
* **Styling:** **Tailwind CSS** for a utility-first, responsive design system.
* **State Management:** **React Context** is used to manage global state like authentication and UI actions, avoiding prop-drilling and unnecessary re-renders.
* **Performance:**
    * **Optimistic UI Updates:** All user engagements (claps, bookmarks, comments) update the UI instantly, providing a snappy, responsive feel while the API request completes in the background.
    * **Lazy Loading:** Components like the rich text editor are lazy-loaded to reduce the initial bundle size.
    * **LRU Caching:** A custom LRU cache is implemented for avatars to reduce network requests and improve performance.
* **Testing:** **Vitest** and **React Testing Library** are used to write comprehensive unit and integration tests for components and hooks, ensuring UI reliability.

### **Backend (Cloudflare Workers)**

The backend is a high-performance, serverless API built to run on Cloudflare's global edge network, ensuring low latency for users worldwide.

* **Framework:** **Hono**, a lightweight and incredibly fast web framework designed for edge environments.
* **Language:** **TypeScript** for robust, type-safe API development.
* **Database & ORM:** **PostgreSQL** (hosted on Supabase) with **Prisma** as the ORM.
    * **Prisma Accelerate** is used for globally distributed database connection pooling and caching, dramatically reducing latency.
* **Authentication:** **Supabase Auth** is used to handle user authentication and JWT management.
* **File Storage:** **Supabase Storage** is used for handling all user image uploads.
* **Error Monitoring:** **Sentry** is integrated to automatically capture and report any backend errors.
* **Testing:** **Vitest** is used with a mocked Prisma client to write fast and reliable integration tests for all API endpoints.

### **Database Architecture**

The PostgreSQL database is designed to be robust and scalable, with a key architectural feature:

* **Auth & Profile Synchronization:** A custom **PostgreSQL trigger** automatically creates a public user profile in our `users` table whenever a new user signs up via Supabase Auth. This ensures that our application's data is always in sync with the authentication system, a common challenge in full-stack applications.

### **DevOps & CI/CD**

To ensure code quality and automate the deployment process, a full CI/CD pipeline is implemented using **GitHub Actions**.

* **On every push to `master`:**
    1.  The backend and frontend tests are run in parallel.
    2.  If all tests pass, the backend is automatically deployed to **Cloudflare Workers**.
    3.  Simultaneously, the frontend is deployed to **Vercel**.
* **Source Map Uploads:** The pipeline automatically uploads source maps to **Sentry** for the backend, allowing for easy debugging of production errors.
* **Secret Management:** All sensitive keys and tokens are securely managed using **GitHub Encrypted Secrets**.

---

## 🧠 Key Architectural Decisions & What They Demonstrate

This project goes beyond a simple implementation and showcases several key architectural decisions that reflect a deep understanding of modern web development principles.

* **Serverless-First Approach:** Choosing Cloudflare Workers and Hono for the backend demonstrates an understanding of modern, scalable, and cost-effective infrastructure. It shows I can build applications that are fast, globally distributed, and have a low operational overhead.
* **Decoupled Frontend & Backend:** The monorepo structure with a clear separation between the frontend and backend allows for independent development and deployment, which is a standard practice in modern teams.
* **Performance by Design:**
    * The use of a centralized `HeaderLayout` and React Context to manage state prevents unnecessary re-renders, a common performance bottleneck in React applications.
    * API endpoints are carefully designed to send only the data needed for a specific view (e.g., sending lightweight `snippets` for the blog list instead of the full post content), minimizing network latency.
* **A Robust Testing Strategy:** The project includes a comprehensive suite of **integration tests** for the backend and **component tests** for the frontend. This demonstrates a commitment to code quality and reliability that is critical in a professional environment.
* **Automated & Reliable Deployments:** The CI/CD pipeline is not just a "nice-to-have." It's a critical piece of infrastructure that acts as a quality gate, ensuring that only tested and verified code makes it to production. This proves I can be trusted to build and maintain a reliable deployment process.

---

## 🚀 Getting Started Locally

*(You can fill in the specific steps for your environment variables here)*

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/sumitbhuia/medium-clone.git
    cd medium-clone
    ```
2.  **Install dependencies :**
    ```bash
    npm i
    ```
3.  **Set up environment variables:**
    * Create a `.env` file in the `frontend` directory.
    * Create a `.dev.vars` file in the `backend` directory.
    * Populate them with your Supabase, Prisma, and other necessary keys by following the `.env.example` files.
4.  **Run the development servers:**
    * In one terminal, run the backend: `cd backend && npm run dev`
    * In another terminal, run the frontend: `cd frontend && npm run dev`

---

## 💡 What I Learned

Building this project was a fantastic opportunity to go deep into the full-stack development lifecycle. I particularly enjoyed:
* Designing and implementing a robust, database-backed authentication system that synchronizes perfectly with a third-party service.
* Architecting a performant frontend with a focus on optimistic UI and efficient state management.
* Building a complete CI/CD pipeline from scratch, which has given me a much deeper appreciation for the importance of automated testing and deployment in a professional workflow.
