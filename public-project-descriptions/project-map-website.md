To be deployed on February 2026.

# What is it?

This is a website where people can collaborate on intel found within video games by uploading game maps and uploading markers on it.

<table>
  <tr>
    <td><img src="../media/f504731e07affeba392599f4a7982b29.jpg" width="500"></td>
    <td><img src="../media/bea600e03851c4cca5b7405be08dac0e.png" width="500"></td>
  </tr>
</table>

## Features

- Highly customizable category and subcategory system  
- Advanced filtering for efficient search and navigation  
- Fine-grained ACL-based access control ensuring privacy per game and across the platform  
- Intuitive UX minimizing manual effort for both users and administrators  
- Designed for high scalability using caching (Redis), load balancing, replication, and sharding  
- Discord-based authentication  

## Upcoming

- Single Sign-On (SSO) support  
- Mobile-optimized version
- Additional marker types (Zones & Lines)


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