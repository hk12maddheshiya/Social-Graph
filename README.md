# Twitter Clone — Backend (Team Project)

> This repository documents the **backend** of a full-stack Twitter-like application.
> **Team project**: I worked **exclusively on the backend** (API, DB, auth, caching, performance).

## 🚀 Backend at a Glance

* **API**: GraphQL (Apollo Server)
* **Runtime**: Node.js
* **ORM/DB**: Prisma ORM + PostgreSQL
* **Cache/Queues**: Redis
* **Auth**: JWT (plus Google OAuth if enabled)
* **Infra/Storage**: AWS S3 for file storage
* **Typing/Tooling**: TypeScript + GraphQL Codegen

---

## ✨ Backend Features

* **User auth**: Email/password with **bcrypt**; JWT-based sessions; optional Google OAuth.
* **Tweets**: Create, delete, fetch timelines; like/unlike; retweet.
* **Follow system**: Follow/unfollow users; personalized feeds.
* **Profiles**: Public profile, stats (tweets/followers/following).
* **Performance**: Redis caching of hot queries and counts; optimized Prisma queries.
* **File Storage**: Profile images & media stored in **AWS S3**.

---

## 📂 Folder Structure (Backend)

```
/backend
src/
 ├── app/
 │    ├── tweet/
 │    └── user/
 ├── clients/
 │    ├── db/
 │    └── redis/
 ├── services/
 │    ├── jwt.ts
 │    ├── tweet.ts
 │    └── user.ts
 └── index.ts
prisma/
 ├── migrations/
 └── schema.prisma


---

## 🔑 Environment Variables

Create a `.env` file at `/backend/.env` (local dev).

```env
# Database
DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/twitter_clone"

# Redis
REDIS_URL="redis://localhost:6379"

# Auth
JWT_SECRET="replace_with_strong_secret"

# Optional: Google OAuth
GOOGLE_CLIENT_ID=""
GOOGLE_CLIENT_SECRET=""
GOOGLE_REDIRECT_URI="http://localhost:4000/oauth/google/callback"

# AWS (for storage)
AWS_ACCESS_KEY_ID=""
AWS_SECRET_ACCESS_KEY=""
AWS_REGION="ap-south-1"
AWS_S3_BUCKET="twitter-clone-bucket"
```

---

## 🛠️ Setup & Run (Backend Only)

1. **Clone & move into backend**

   ```bash
   git clone https://github.com/your-org/your-repo.git
   cd backend
   ```

2. **Install deps**

   ```bash
   npm install
   ```

3. **Generate Prisma client & apply schema**

   ```bash
   npx prisma generate
   npx prisma migrate dev --name init
   ```

4. **Start dev server**

   ```bash
   npm run dev
   ```

   * GraphQL Playground: `http://localhost:4000/graphql`

5. **Build & run (prod-like)**

   ```bash
   npm run build
   npm start
   ```

---

## 🐳 Docker Quickstart

```yaml
version: "3.8"
services:
  db:
    image: postgres:15
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: twitter_clone
    ports: ["5432:5432"]

  redis:
    image: redis:7
    ports: ["6379:6379"]
```

---

## 🔒 Security Highlights

* Passwords hashed with **bcrypt**.
* **JWT** for stateless auth; verified in Apollo context.
* Files (profile pics, media) stored in **AWS S3**.
* Input validation & rate-limiting.

---

## 👥 Credits

* **Team project** (full-stack).
* **My role**: Backend only — GraphQL API, Prisma models, auth (JWT + bcrypt), Redis caching, AWS S3 integration, and performance improvements.
