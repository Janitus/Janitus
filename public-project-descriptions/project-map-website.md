To be deployed on February 2026.

# What is it?

This is a website where people can collaborate on intel found within video games by uploading game maps and uploading markers on it.
<img src="../media/f504731e07affeba392599f4a7982b29.jpg"/>

## Features
- Highly customizable categories and subcategories
- Adjustable filters for ease of searching
- ACL-based access right controls ensuring privacy to each individual game and the platform as a whole.
- Easy-to-use UX, avoiding manual work for both users and admins
- Optimized to handle high volume of requests via caches (Redis), load balancers and replicas, and sharding.
- Discord based auth
- UPCOMING: Auth will support SSO later
- UPCOMING: Mobile version

## Tech stack

| Layer        | Technology                   |
|--------------|------------------------------|
| Framework    | Next.js 15 (App Router)      |
| Language     | TypeScript                   |
| Database     | SQLite (dev) / PostgreSQL (prod) |
| ORM          | Prisma 7                     |
| Auth         | Auth.js v5 (Discord OAuth)   |
| Map          | React Leaflet + Leaflet      |
| Cache        | Redis (optional)             |
| Styling      | Tailwind CSS + Radix UI      |
| Validation   | Zod                          |
| Unit tests   | Vitest                       |
| E2E tests    | Playwright                   |