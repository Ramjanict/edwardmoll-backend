# 🔧 Edward Moll — Backend API

> REST API for **Edward Moll Moving & Relocation Services** — built with NestJS, Prisma, and PostgreSQL.

🌐 **Frontend:** [https://edwardmoll-frontend-nine.vercel.app](https://edwardmoll-frontend-nine.vercel.app)  
🚀 **Live API:** [https://edwardmoll526.onrender.com](https://edwardmoll526.onrender.com)  
📖 **Swagger Docs:** [https://edwardmoll526.onrender.com/api](https://edwardmoll526.onrender.com/api)

---

## 📸 Tech Stack

| Technology | Version | Purpose |
|---|---|---|
| [NestJS](https://nestjs.com/) | 11 | Backend Framework |
| [TypeScript](https://www.typescriptlang.org/) | 5 | Type Safety |
| [Prisma](https://www.prisma.io/) | 7 | ORM & Database Client |
| [PostgreSQL](https://www.postgresql.org/) | — | Primary Database |
| [JWT + Passport](https://docs.nestjs.com/security/authentication) | — | Authentication |
| [Cloudinary](https://cloudinary.com/) | 2 | Image Storage & Upload |
| [Nodemailer](https://nodemailer.com/) | 9 | Email Notifications |
| [Swagger](https://swagger.io/) | — | API Documentation |
| [Bcrypt](https://github.com/kelektiv/node.bcrypt.js) | 6 | Password Hashing |
| [class-validator](https://github.com/typestack/class-validator) | — | DTO Validation |

---

## 📁 Project Structure

```
src/
├── admin/                  # Admin user management
├── auth/                   # JWT authentication & guards
│   ├── auth.controller.ts
│   ├── auth.service.ts
│   ├── jwt.strategy.ts
│   ├── jwt-auth.guard.ts
│   └── roles.guard.ts
├── contact/                # Contact inquiry module
├── gallery/                # Gallery image module
├── posts/                  # Blog posts & comments module
├── services/               # Moving services module
├── upload/                 # File upload (Cloudinary)
├── mailer/                 # Email notification service
├── prisma/                 # Prisma service & module
├── common/                 # Shared filters & interceptors
│   ├── filters/
│   └── interceptors/
├── generated/              # Prisma generated client
├── app.module.ts           # Root module
└── main.ts                 # Entry point
prisma/
└── schema.prisma           # Database schema
```

---

## 🗄️ Database Schema

| Model | Description |
|---|---|
| `AdminUser` | Admin accounts with OWNER / ADMIN roles |
| `Service` | Moving service listings |
| `GalleryImage` | Gallery photos with categories |
| `Post` | Blog / update posts with slugs |
| `Comment` | Nested comments on posts |
| `ContactInquiry` | Customer contact form submissions |

---

## ✨ API Modules

### 🔐 Auth
- `POST /auth/login` — Admin login, returns JWT token

### 🛠️ Services
- `GET /services` — Get all active services
- `POST /services` — Create service *(Admin)*
- `PATCH /services/:id` — Update service *(Admin)*
- `DELETE /services/:id` — Delete service *(Admin)*

### 🖼️ Gallery
- `GET /gallery` — Get all active gallery images
- `POST /gallery` — Add gallery image *(Admin)*
- `PATCH /gallery/:id` — Update gallery image *(Admin)*
- `DELETE /gallery/:id` — Delete gallery image *(Admin)*

### 📝 Posts
- `GET /posts` — Get all published posts
- `GET /posts/:slug` — Get post by slug
- `POST /posts` — Create post *(Admin)*
- `PATCH /posts/:id` — Update post *(Admin)*
- `DELETE /posts/:id` — Delete post *(Admin)*
- `POST /posts/:id/like` — Like a post
- `POST /posts/:id/comments` — Add comment

### 📬 Contact
- `POST /contact` — Submit contact inquiry
- `GET /contact` — Get all inquiries *(Admin)*
- `DELETE /contact/:id` — Delete inquiry *(Admin)*

### 📤 Upload
- `POST /upload` — Upload image to Cloudinary *(Admin)*

---

## 🚀 Getting Started

### Prerequisites
- Node.js `>= 18`
- PostgreSQL database
- Cloudinary account
- SMTP email credentials

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/edwardmoll-backend.git
cd edwardmoll-backend

# Install dependencies
npm install
```

### Environment Variables

Create a `.env` file in the root directory:

```env
# Database
DATABASE_URL=postgresql://USER:PASSWORD@HOST:PORT/DATABASE

# JWT
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=7d

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email (SMTP)
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USER=your_email@gmail.com
MAIL_PASS=your_app_password
MAIL_FROM=your_email@gmail.com

# App
PORT=3000
FRONTEND_URL=https://edwardmoll-frontend-nine.vercel.app
```

### Database Setup

```bash
# Run Prisma migrations
npx prisma migrate dev

# Generate Prisma client
npx prisma generate

# (Optional) Open Prisma Studio
npx prisma studio
```

### Running the App

```bash
# Development (watch mode)
npm run start:dev

# Production build
npm run build
npm run start:prod

# Debug mode
npm run start:debug
```

### Running Tests

```bash
# Unit tests
npm run test

# Test coverage
npm run test:cov

# End-to-end tests
npm run test:e2e
```

---

## 📖 API Documentation

Swagger UI is live at:

```
https://edwardmoll526.onrender.com/api
```

> Auto-generated from NestJS decorators using `@nestjs/swagger`. All endpoints, request/response schemas, and auth flows are documented there.

---

## 🌐 Deployment

Recommended platforms for deployment:

| Platform | Type | Notes |
|---|---|---|
| [Railway](https://railway.app/) | PaaS | Supports Node.js + PostgreSQL add-on |
| [Render](https://render.com/) | PaaS | Free tier available |
| [Fly.io](https://fly.io/) | Container | Good for production |

### General Steps

1. Push the code to GitHub
2. Create a new project on your chosen platform
3. Add all environment variables from the `.env` section above
4. Set the start command: `npm run start:prod`
5. Provision a **PostgreSQL** database and set `DATABASE_URL`
6. Run migrations on deploy: `npx prisma migrate deploy`

---

## 🔗 Related

- 🌐 **Frontend:** [edwardmoll-frontend](https://edwardmoll-frontend-nine.vercel.app) — React + TypeScript + Vite (deployed on Vercel)
- 📖 **Swagger Docs:** [edwardmoll526.onrender.com/api](https://edwardmoll526.onrender.com/api)

---

## 📄 License

This project is private and proprietary. All rights reserved © Edward Moll Moving & Relocation Services.
