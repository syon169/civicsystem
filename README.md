# CivicSystem

A civic services web app built with Next.js — lets citizens browse services, file complaints, track requests, register/login, and chat with an AI assistant.

## Tech Stack

- **Framework:** Next.js 16 (App Router), React 19
- **Styling:** Tailwind CSS 4
- **UI components:** Radix UI primitives + shadcn-style components
- **Forms:** React Hook Form + Zod validation
- **Charts:** Recharts
- **Analytics:** Vercel Analytics

## Project Structure

```
app/
  page.tsx              Home page
  admin/                Admin dashboard
  ai-chatbot/            AI chatbot page
  complaint/              Complaint filing page
  contact/                Contact page
  login/                  Login page
  register/               Registration page
  services/               Services listing page
  track/                  Request tracking page
components/             Shared UI and feature components
hooks/                  Custom React hooks
lib/                    Utility functions
styles/                 Global styles
```

## Getting Started

### Prerequisites

- Node.js 20 or later
- npm (this project uses `package-lock.json` — don't mix in pnpm/yarn lockfiles, as that can break automated builds like Google Cloud Buildpacks)

### Install dependencies

```bash
npm install
```

### Run the dev server

```bash
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000).

### Build for production

```bash
npm run build
npm run start
```

### Lint

```bash
npm run lint
```

## Deployment (Google Cloud Run)

This project deploys via Cloud Run's buildpack-based continuous deployment (no Dockerfile required):

- **Build type:** Go, Node.js, Python, Java, .NET Core, Ruby or PHP via Google Cloud's buildpacks
- **Build context directory:** `/`
- **Entrypoint:** leave blank (buildpacks auto-detect `npm run build` + `npm start`)
- The app listens on the `PORT` environment variable automatically, as required by Cloud Run.

**Important:** keep only one lockfile in the repo (`package-lock.json`). If a `pnpm-lock.yaml` or `yarn.lock` is present alongside it, the buildpack may pick the wrong package manager and fail with dependency build-script errors.

## Notes

- No database or authentication layer is currently wired in this version of the project.
- `node_modules` should never be committed — if dependency folders appear loose in the repo root, they were committed by mistake and should be removed.
