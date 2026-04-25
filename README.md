# MealMind

MealMind is an AI-powered cooking companion that helps users turn pantry ingredients into practical recipes.
It combines a modern Next.js frontend with a Strapi backend, user authentication, and AI services for ingredient detection and recipe generation.

## Live Deployment

https://mealmind.tech

## What This Project Does

- Scans pantry/fridge images and extracts ingredients using Gemini Vision.
- Lets users manage pantry items manually (add, edit, remove).
- Recommends recipes from pantry ingredients using AI.
- Generates full recipe details on-demand (steps, nutrition, substitutions, tips).
- Supports bookmarking/saving recipes per user.
- Provides recipe exploration by category/cuisine via TheMealDB.
- Uses authenticated user accounts with free/pro tier behavior.

## Tech Stack

### Frontend

- Next.js 16 (App Router)
- React 19
- Tailwind CSS 4
- Clerk (auth + user/session management)
- Arcjet (WAF, bot protection, rate limiting)
- Google Generative AI SDK (Gemini)
- Unsplash API (recipe images)
- shadcn/ui + Radix-based UI components

### Backend

- Strapi 5 (headless CMS + APIs)
- PostgreSQL (production) / SQLite fallback supported by Strapi config
- Users & permissions plugin

### External Data/APIs

- TheMealDB (recipe discovery metadata)
- Gemini API (AI vision + text generation)
- Unsplash API (image enrichment)

## Monorepo Structure

```
MealMind/
	frontend/   # Next.js app (UI, auth, server actions)
	backend/    # Strapi app (content types and API)
```

## Prerequisites

- Node.js 20+
- npm
- A running Strapi backend instance
- Clerk account and app keys
- Gemini API key
- Unsplash access key (optional but recommended)
- Arcjet key

## Environment Variables

### Backend (`backend/.env`)

Start from `backend/.env.example` and add/update as needed.

Required base keys:

- `HOST`
- `PORT`
- `APP_KEYS`
- `API_TOKEN_SALT`
- `ADMIN_JWT_SECRET`
- `TRANSFER_TOKEN_SALT`
- `JWT_SECRET`
- `ENCRYPTION_KEY`

Common DB keys (for PostgreSQL/local customization):

- `DATABASE_CLIENT` (e.g. `postgres`)
- `DATABASE_URL` or
- `DATABASE_HOST`, `DATABASE_PORT`, `DATABASE_NAME`, `DATABASE_USERNAME`, `DATABASE_PASSWORD`

### Frontend (`frontend/.env.local`)

Set the following keys (based on app usage):

- `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`
- `CLERK_SECRET_KEY`
- `NEXT_PUBLIC_CLERK_SIGN_IN_URL` (typically `/sign-in`)
- `NEXT_PUBLIC_CLERK_SIGN_UP_URL` (typically `/sign-up`)
- `NEXT_PUBLIC_STRAPI_URL` (e.g. `http://localhost:1337`)
- `STRAPI_API_TOKEN` (Strapi API token with relevant permissions)
- `GEMINI_API_KEY`
- `UNSPLASH_ACCESS_KEY`
- `ARCJET_KEY`


## Local Development Setup

Run backend and frontend in separate terminals.

### 1) Install dependencies

```bash
cd backend
npm install

cd ../frontend
npm install
```

### 2) Start backend (Strapi)

```bash
cd backend
npm run dev
```

Backend default URL: `http://localhost:1337`

### 3) Start frontend (Next.js)

```bash
cd frontend
npm run dev
```

Frontend default URL: `http://localhost:3000`

## Usage Flow

1. Sign up/sign in using Clerk.
2. Add pantry items manually or upload a pantry image for AI scanning.
3. Ask MealMind for recipe suggestions using available ingredients.
4. Open a recipe to view full details and cooking instructions.
5. Save recipes to your collection and revisit them anytime.



