# Eco Huerto Montgo — Frontend

E-commerce web application for purchasing fresh agricultural produce, built with Angular 21.

Live site: [ecohuertomontgo.com](https://ecohuertomontgo.com)

---

## Tech stack

| Layer | Technology |
|---|---|
| Framework | Angular 21 (standalone components) |
| Language | TypeScript 5.9 |
| Reactive layer | RxJS 7.8 |
| i18n | @ngneat/transloco |
| Rich text | Quill / ngx-quill |
| Unit tests | Vitest |
| CI/CD | GitHub Actions → GitHub Pages |

---

## Getting started

**Prerequisites:** Node.js ≥ 18, npm ≥ 10

```bash
npm install
npm start          # dev server at http://localhost:4200
```

---

## Scripts

| Command | Description |
|---|---|
| `npm start` | Development server with live reload |
| `npm run build` | Production build → `dist/HuertoCarlos-front/browser/` |
| `npm run watch` | Build in watch mode |
| `npm test` | Run unit tests with Vitest |

---

## Project structure

```
src/
├── app/
│   ├── components/
│   │   ├── admin/            # Admin panel (dashboard, products, orders, customers, notifications)
│   │   ├── catalogue/        # Product listing with category/variety filters
│   │   ├── product-detail/   # Single product view
│   │   ├── cart/             # Shopping cart
│   │   ├── orders/           # Customer order history
│   │   ├── order-detail/     # Single order details
│   │   ├── login/            # Customer login
│   │   ├── register/         # Customer registration
│   │   └── profile/          # Customer profile
│   ├── core/
│   │   ├── auth/             # Guards and authentication logic
│   │   ├── model/            # Interfaces (Product, Order, Customer, Variety…)
│   │   ├── services/         # API services
│   │   ├── pipes/            # Custom pipes
│   │   └── utils/
│   └── shared/               # Navbar, toast, loading spinner
├── assets/
│   └── i18n/                 # Translation files: en.json, es.json, nl.json
└── environments/             # API base URL per environment
```

---

## Features

**Customer**
- Browse and search products by category and variety
- Add/remove items from the shopping cart
- Register, log in, and manage profile
- View order history and order status (Pending → Confirmed → Ready for pickup → Delivered)

**Admin** (protected by `adminGuard`)
- Manage products, varieties, customers, and orders
- Send notifications to customers

**General**
- Multi-language support: Spanish, English, Dutch (via URL `?lang=` or localStorage)
- HTTP interceptor for JWT injection
- Lazy-loaded routes
- Toast notification service

---

## Environment configuration

Both environments point to the same hosted API:

```
https://huerto-api.up.railway.app/api/v1
```

To override locally, edit [src/environments/environment.ts](src/environments/environment.ts).

---

## Deployment

Pushes to the main branch trigger a GitHub Actions workflow that builds the app for production and deploys it to GitHub Pages under the custom domain `ecohuertomontgo.com`.
