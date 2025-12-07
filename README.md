# 🕸️ SocialGraph - Social Media Backend

<div align="center">

![GraphQL](https://img.shields.io/badge/-GraphQL-E10098?style=for-the-badge&logo=graphql&logoColor=white)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)

**The high-performance backend infrastructure for a full-stack Twitter Clone.**

[Report Bug](https://github.com/hk12maddheshiya/SocialGraph-API/issues) · [Request Feature](https://github.com/hk12maddheshiya/SocialGraph-API/issues)

</div>

---

## 📖 Overview

**SocialGraph** serves as the backend engine for a large-scale **Social Media Application** (Twitter Clone).

> **👨‍💻 Team Project Role:**
> While this was a full-stack team initiative, **I worked exclusively on the backend architecture**. My contributions included designing the GraphQL API, optimizing database modeling with Prisma, implementing secure authentication, and integrating Redis caching for high-speed social graph traversals.

## 🚀 Key Features

### 🔐 Authentication & Security
* **Secure Auth:** Email/password login using **bcrypt** hashing.
* **Session Management:** Stateless authentication via **JWT**.
* **OAuth:** Optional Google Login integration.
* **Rate Limiting:** Protection against API abuse.

### 🐦 Social Core (Twitter Logic)
* **Tweet Management:** Create, delete, like, unlike, and retweet functionality.
* **Timeline Generation:** Personalized feeds based on the user's social graph.
* **Social Graph:** Complex Follow/Unfollow system with optimized graph traversal queries.
* **User Profiles:** Public profiles displaying live stats (Tweets, Followers, Following).

### ⚡ Performance & Infrastructure
* **Caching Layer:** **Redis** integration to cache hot queries (e.g., user feeds, interaction counts).
* **Database:** **PostgreSQL** with **Prisma ORM** for type-safe, efficient relational queries.
* **Cloud Storage:** Media assets (Profile pictures, tweet images) securely stored in **AWS S3**.

## 💻 Tech Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Runtime** | Node.js | Server-side JavaScript runtime |
| **API** | Apollo Server | GraphQL server implementation |
| **Language** | TypeScript | Static typing for scalability |
| **Database** | PostgreSQL | Primary relational database |
| **ORM** | Prisma | Database schema & query management |
| **Caching** | Redis | In-memory store for performance |
| **Storage** | AWS S3 | Object storage for files |

## 📂 Folder Structure

```text
/backend
src/
 ├── app/               # GraphQL Resolvers & Types
 │    ├── tweet/        # Tweet-related logic
 │    └── user/         # User & Auth logic
 ├── clients/           # External client connections
 │    ├── db/           # Prisma Client instance
 │    └── redis/        # Redis Client instance
 ├── services/          # Business Logic Layer
 │    ├── jwt.ts        # Token generation/validation
 │    ├── tweet.ts      # Tweet service methods
 │    └── user.ts       # User service methods
 └── index.ts           # Entry point
prisma/
 ├── migrations/        # SQL Migrations
 └── schema.prisma      # Data Model
```

## 🛠️ Getting Started
Follow these steps to set up the backend locally.

Prerequisites
Node.js (v16+)

PostgreSQL & Redis (running locally or via Docker)

AWS S3 Bucket (optional, for file uploads)

Installation
Clone the repository

Bash

git clone [https://github.com/hk12maddheshiya/SocialGraph-API.git](https://github.com/hk12maddheshiya/SocialGraph-API.git)
cd backend
Install Dependencies

Bash

npm install
Environment Configuration Create a .env file in the root directory:

Code snippet

# Database
DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/twitter_clone"

# Redis
REDIS_URL="redis://localhost:6379"

# Auth
JWT_SECRET="your_strong_secret_key"

# Google OAuth (Optional)
GOOGLE_CLIENT_ID=""
GOOGLE_CLIENT_SECRET=""
GOOGLE_REDIRECT_URI="http://localhost:4000/oauth/google/callback"

# AWS S3 (For Storage)
AWS_ACCESS_KEY_ID="your_access_key"
AWS_SECRET_ACCESS_KEY="your_secret_key"
AWS_REGION="ap-south-1"
AWS_S3_BUCKET="twitter-clone-bucket"
Database Setup

Bash

# Generate Prisma Client
npx prisma generate

# Push schema to DB
npx prisma migrate dev --name init
Run the Server

Bash

npm run dev
Playground: Open http://localhost:4000/graphql to test the API.

🐳 Docker Quickstart
To quickly spin up the database and cache without local installation:

YAML

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
Run docker-compose up -d to start these services.

🤝 Contributing
Fork the Project

Create your Feature Branch (git checkout -b feature/NewFeature)

Commit your Changes (git commit -m 'Add some NewFeature')

Push to the Branch (git push origin feature/NewFeature)

Open a Pull Request
