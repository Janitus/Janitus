To be deployed later in 2026.

# What is it?

This platform enables users to collaborate on in-game intelligence by uploading custom game maps and placing interactive markers to share information with others. [Video link](https://i.gyazo.com/7474fe431e869beec751af81045cebfc.mp4)

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
- Automated AI-based Admin reports on collected data (Statistics & Logs)

## Tech stack

| Layer           | Technology                                       |
|-----------------|--------------------------------------------------|
| Framework       | Next.js 16 (App Router)                          |
| Language        | TypeScript                                       |
| Database        | SQLite (dev) / PostgreSQL (prod)                 |
| ORM             | Prisma 7                                         |
| Auth            | Auth.js v5 (Discord OAuth)                       |
| Map             | Leaflet (imperative) + leaflet.markercluster     |
| Client cache    | IndexedDB via `idb`                              |
| Styling         | Tailwind CSS v4                                  |
| UI primitives   | Radix UI (dialog, dropdown, select, label)       |
| Validation      | Zod                                              |
| Image processing| sharp                                            |
| Cloud storage   | Cloudflare R2 (S3-compatible)                    |
| Upload gateway  | Cloudflare Worker (upload-guard)                 |
| Deployment      | Railway (staging + production)                   |
| Unit tests      | Vitest                                           |
| E2E tests       | Playwright                                       |

## High-Level Diagram

```mermaid
flowchart TB
    subgraph Client ["Browser"]
        UI["React UI<br/>(Leaflet, Radix)"]
        IDB["IndexedDB<br/>Marker Cache"]
    end

    subgraph Railway ["Railway"]
        Next["Next.js 16<br/>App Router"]
        Prisma["Prisma 7"]
        DB[(SQLite / PostgreSQL)]
    end

    subgraph Cloudflare ["Cloudflare"]
        Worker["Upload Guard<br/>Worker"]
        R2["R2 Bucket"]
        CDN["CDN<br/>(pub-xxx.r2.dev)"]
    end

    Discord["Discord OAuth"]

    UI <-->|API calls| Next
    UI <-->|Cache R/W| IDB
    UI -->|Sign in| Discord
    Discord -->|Callback| Next
    Next <--> Prisma
    Prisma <--> DB
    Next -->|Upload / Delete / Info| Worker
    Worker <-->|R2 Binding| R2
    R2 -->|Public read| CDN
    CDN -->|Map images| UI
```
