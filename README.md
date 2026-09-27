# Portfolio — Rupesh Bhandari

A developer portfolio website for **Rupesh Bhandari** (Laravel + React developer), built with Next.js. Dark, playful, code-themed design with animated typing effects, a debug-mode easter egg, and a working contact form.

## Features

- **Animated hero** — typing code snippets, floating terminal cards
- **Sections:** Home, About, Skills, Projects, Contact + a dedicated `/resume` page
- **Debug mode easter egg** and a coffee counter for personality
- **Contact form** — submits via a Next.js server action that sends email through [Resend](https://resend.com), with graceful `mailto:` fallback when the API key is missing
- **Dark/light theme** via next-themes, Framer Motion scroll animations
- PWA manifest (`app/manifest.ts`), SEO metadata

## Tech Stack

- **Framework:** Next.js 14 (App Router)
- **Language:** TypeScript
- **UI:** React 18, Tailwind CSS, shadcn/ui (Radix), Lucide icons, Framer Motion
- **Email:** Resend (server action in `app/actions/contact.ts`)

## Quick Start

```bash
npm install --legacy-peer-deps
cp .env.example .env   # add RESEND_API_KEY (see below)
npm run dev
```

Open http://localhost:3000.

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `RESEND_API_KEY` | For contact form | Resend API key (`re_...`). Without it, the form returns a `mailto:` fallback instead of sending. |

The contact form emails submissions to the portfolio owner's inbox via Resend's API.

## Project Structure

```
app/
  page.tsx            # Full portfolio: hero, about, skills, projects, contact
  resume/page.tsx     # Resume page
  actions/contact.ts  # "use server" action — sends contact email via Resend
  layout.tsx          # Root layout, metadata, theme provider
  manifest.ts         # PWA manifest
components/ui/        # shadcn/ui components
public/images/        # Profile photo
```

## Deployment Notes

- **Deploy target:** Vercel (or any Node host) — the contact form requires a server runtime and the `RESEND_API_KEY` secret, so this app is **not** statically exported and has no GitHub Pages deployment.
- Standard Next.js deploy: `npm run build && npm start`, or connect the repo to Vercel and set `RESEND_API_KEY` in Project Settings → Environment Variables.
- Next.js 14.2.16 — pin/upgrade dependencies before production use.

---

Built by Girish Lade · https://ladestack.in
