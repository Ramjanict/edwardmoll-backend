# 🔧 Edward Moll — Core REST API & Backend Engine

<div align="center">

[![NestJS](https://img.shields.io/badge/NestJS-11.0.1-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)](https://nestjs.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Prisma](https://img.shields.io/badge/Prisma-7.9.1-2D3748?style=for-the-badge&logo=prisma&logoColor=white)](https://www.prisma.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16+-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![JWT](https://img.shields.io/badge/Auth-JWT_Passport-black?style=for-the-badge&logo=jsonwebtokens&logoColor=white)](https://jwt.io/)
[![Cloudinary](https://img.shields.io/badge/Storage-Cloudinary_CDN-3448C5?style=for-the-badge&logo=cloudinary&logoColor=white)](https://cloudinary.com/)
[![Swagger](https://img.shields.io/badge/API_Docs-Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)](https://edwardmoll526.onrender.com/api)
[![Render](https://img.shields.io/badge/Deployed-Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)](https://edwardmoll526.onrender.com)

<br/>

**Enterprise-grade REST API backend powering Edward Moll Moving & Relocation Services (AAAAAffordable Moving)**  
*Engineered with NestJS 11, Prisma ORM, PostgreSQL, JWT Authentication, and Cloudinary Media Services.*

[Live API Health](https://edwardmoll526.onrender.com) • [Interactive Swagger Docs](https://edwardmoll526.onrender.com/api) • [Client Frontend](https://edwardmoll-frontend-nine.vercel.app) • [Frontend Repo](https://github.com/Ramjanict/edwardmoll-frontend)

</div>

---

## 📌 Repository Overview

| Property | Value |
|---|---|
| **Repository Name** | `edwardmoll-backend` |
| **Project Name** | **Edward Moll Relocation Core REST API Engine** |
| **Live Base URL** | [https://edwardmoll526.onrender.com](https://edwardmoll526.onrender.com) |
| **Interactive API Specs** | [https://edwardmoll526.onrender.com/api](https://edwardmoll526.onrender.com/api) |
| **Frontend Web App** | [https://edwardmoll-frontend-nine.vercel.app](https://edwardmoll-frontend-nine.vercel.app) |
| **Database Architecture** | PostgreSQL managed instance via Prisma ORM client |

---

## 📸 Domain Visuals & Service Coverage

The backend services handle data flows for moving fleet management, media assets, blog CMS, and customer inquiries:

<div align="center">
  <img src="docs/images/moving-truck-fleet.jpg" alt="Commercial Fleet and Moving Operations" width="850" />
</div>

<div align="center">
  <table border="0">
    <tr>
      <td width="50%" align="center">
        <img src="docs/images/crew-packing-service.jpg" alt="Packing Services" width="100%" />
        <br/><b>Packing & Protection Catalog</b>
      </td>
      <td width="50%" align="center">
        <img src="docs/images/office-relocation.jpg" alt="Commercial Moves" width="100%" />
        <br/><b>Commercial Logistics Management</b>
      </td>
    </tr>
    <tr>
      <td width="50%" align="center">
        <img src="docs/images/specialty-piano-moving.jpg" alt="Specialty Moving" width="100%" />
        <br/><b>Specialty Relocation Records</b>
      </td>
      <td width="50%" align="center">
        <img src="docs/images/happy-homeowners.jpg" alt="Client Testimonials" width="100%" />
        <br/><b>Customer Inquiry & Lead Processing</b>
      </td>
    </tr>
  </table>
</div>

---

## 🛠️ Architecture & Core Modules

```
src/
├── admin/                  # Admin profile & system user operations
├── auth/                   # JWT authentication, Passport strategy & RBAC guards
│   ├── dto/                # Login & auth validation DTOs
│   ├── auth.controller.ts  # POST /auth/login
│   ├── auth.service.ts     # Password hashing & JWT token issuance
│   ├── jwt.strategy.ts     # Bearer token validation
│   ├── jwt-auth.guard.ts   # Route protection guard
│   └── roles.guard.ts      # Role-based authorization guard (OWNER / ADMIN)
├── services/               # Moving service catalog module
│   ├── dto/                # CreateServiceDto, UpdateServiceDto
│   ├── services.controller.ts # Public & Admin service endpoints
│   └── services.service.ts # Prisma queries for services
├── gallery/                # Media gallery management
│   ├── dto/                # CreateGalleryDto, UpdateGalleryDto
│   ├── gallery.controller.ts # Public image feeds & Admin image manager
│   └── gallery.service.ts  # Gallery operations & ordering
├── posts/                  # Updates, blog posts & nested comments
│   ├── dto/                # CreatePostDto, CommentDto
│   ├── posts.controller.ts # Public blog feeds, slug lookups, likes & comments
│   └── posts.service.ts    # Slug generation, post CRUD & comment trees
├── contact/                # Customer inquiries & instant quote requests
│   ├── dto/                # CreateContactDto
│   ├── contact.controller.ts # Lead submission & Admin inbox management
│   └── contact.service.ts  # DB persistence & Nodemailer trigger
├── upload/                 # Cloudinary CDN integration
│   ├── upload.controller.ts # File upload gateway (multipart/form-data)
│   └── upload.service.ts   # Cloudinary buffer upload & optimization
├── mailer/                 # Automated email notification engine
│   └── mailer.service.ts   # SMTP transporter for new contact lead alerts
├── common/                 # Global filters, interceptors & transforms
│   ├── filters/            # Global HTTP exception filter
│   └── interceptors/       # Response format standardization
├── prisma/                 # Prisma client service wrapper & lifecycle hooks
├── app.module.ts           # Root NestJS application module
└── main.ts                 # Bootstrap script, Swagger setup, CORS & global pipes
```

---

## 🗄️ Database Schema & Data Models

Managed seamlessly via **Prisma ORM** with automated migrations for PostgreSQL:

| Model | Table | Description |
|---|---|---|
| `AdminUser` | `admin_users` | Admin accounts with bcrypt password hashes and roles (`OWNER`, `ADMIN`) |
| `Service` | `services` | Moving services (Residential, Commercial, Packing, etc.) with sorting and status |
| `GalleryImage` | `gallery_images` | High-res showcase images, categories, and display order |
| `Post` | `posts` | Company updates & articles with unique slug, cover image, and like counters |
| `Comment` | `comments` | Multi-level threaded discussions attached to posts with cascade deletion |
| `ContactInquiry` | `contact_inquiries` | Customer leads and quote requests with read/unread tracking |
| `SiteSetting` | `site_settings` | Dynamic key-value configuration flags for website metadata |

---

## 📡 REST API Reference

All requests and responses use JSON format. Protected endpoints require:
`Authorization: Bearer <your_jwt_token>`

### 🔐 Authentication (`/auth`)
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/auth/login` | Public | Authenticates admin credentials and returns JWT bearer token |

### 🚚 Moving Services (`/services`)
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/services` | Public | Retrieve all active moving services |
| `POST` | `/services` | Admin | Create a new moving service listing |
| `PATCH` | `/services/:id` | Admin | Update service details, icon, or sort order |
| `DELETE` | `/services/:id` | Admin | Remove a service from the catalog |

### 🖼️ Media Gallery (`/gallery`)
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/gallery` | Public | Retrieve active gallery photos sorted by priority |
| `POST` | `/gallery` | Admin | Register new image record with category and caption |
| `PATCH` | `/gallery/:id` | Admin | Modify image metadata or category |
| `DELETE` | `/gallery/:id` | Admin | Delete gallery image record |

### 📝 Posts & Articles (`/posts`)
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/posts` | Public | Get all published posts with comment counts |
| `GET` | `/posts/:slug` | Public | Fetch single post by SEO-friendly URL slug |
| `POST` | `/posts` | Admin | Publish a new article with markdown content |
| `PATCH` | `/posts/:id` | Admin | Edit existing post content or publish state |
| `DELETE` | `/posts/:id` | Admin | Permanently delete post and associated comments |
| `POST` | `/posts/:id/like` | Public | Increment like counter for a post |
| `POST` | `/posts/:id/comments` | Public | Submit top-level or threaded reply comment |

### 📬 Contact & Leads (`/contact`)
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/contact` | Public | Submit quote inquiry (triggers automated email alert) |
| `GET` | `/contact` | Admin | Fetch all customer inquiries with pagination |
| `DELETE` | `/contact/:id` | Admin | Delete customer inquiry record |

### ☁️ Media Uploads (`/upload`)
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/upload/image` | Admin | Upload image file (`multipart/form-data`) to Cloudinary CDN |

---

## 🚀 Local Development Setup

### Prerequisites
- **Node.js:** `>= 18.0.0`
- **PostgreSQL:** Local server or cloud database (e.g. Supabase / Neon / Render)
- **Cloudinary Account:** For image asset hosting
- **SMTP Server:** For email forwarding (e.g., Gmail App Password or SendGrid)

### 1. Clone the Repository
```bash
git clone https://github.com/Ramjanict/edwardmoll-backend.git
cd edwardmoll-backend
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Configuration
Create a `.env` file in the root directory:

```env
# Application Port
PORT=3000

# Database Connection String
DATABASE_URL="postgresql://username:password@localhost:5432/edwardmoll?schema=public"

# JWT Authentication
JWT_SECRET="your-ultra-secure-jwt-secret-key"
JWT_EXPIRES_IN="7d"

# Cloudinary Storage Configuration
CLOUDINARY_CLOUD_NAME="your_cloud_name"
CLOUDINARY_API_KEY="your_api_key"
CLOUDINARY_API_SECRET="your_api_secret"

# Nodemailer / SMTP Configuration
SMTP_HOST="smtp.gmail.com"
SMTP_PORT=587
SMTP_USER="your-email@gmail.com"
SMTP_PASS="your-app-password"
MAIL_FROM="Edward Moll Moving <your-email@gmail.com>"
MAIL_TO="Aaaaaffordabl@gmail.com"

# CORS Allowed Origin
FRONTEND_URL="http://localhost:5173"
```

### 4. Database Setup & Migrations
```bash
# Run Prisma migrations
npx prisma migrate dev --name init

# Generate Prisma Client
npx prisma generate
```

### 5. Start the Application
```bash
# Start in watch mode for development
npm run start:dev

# Start in production mode
npm run start:prod
```

Interactive Swagger documentation is available locally at:
👉 `http://localhost:3000/api`

---

## 🌐 Production Deployment (Render)

This backend is designed for continuous deployment on **Render**:

1. Link repository `Ramjanict/edwardmoll-backend`.
2. Configure Build & Start Commands:
   - **Build Command:** `npm install && npx prisma generate && npm run build`
   - **Start Command:** `npm run start:prod`
3. Add Environment Variables under the **Environment** tab on Render.
4. Set CORS `FRONTEND_URL` to `https://edwardmoll-frontend-nine.vercel.app`.

---

## 🔗 Related Repositories

- 🖥️ **Frontend Web Application:** [Ramjanict/edwardmoll-frontend](https://github.com/Ramjanict/edwardmoll-frontend)
- 🌐 **Live Website:** [https://edwardmoll-frontend-nine.vercel.app](https://edwardmoll-frontend-nine.vercel.app)

---

## 📄 License & Attribution

Copyright © Edward Moll Moving & Relocation Services.  
Developed and maintained by [Ramjan](https://github.com/Ramjanict).
