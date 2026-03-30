
# FLEET - Transport Management System (Frontend)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Next.js](https://img.shields.io/badge/Next.js-15.x-000000.svg)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.x-61dafb.svg)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178c6.svg)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.x-38bdf8.svg)](https://tailwindcss.com/)

A modern, responsive frontend application for the Transport Management System (FLEET), designed to streamline fuel consumption tracking, vehicle fleet management, and reconciliation processes for government vehicles within the State Department for Immigration and Citizen Services.

## 📋 Table of Contents

- [✨ Features](#-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [📋 Prerequisites](#-prerequisites)
- [🚀 Getting Started](#-getting-started)
- [📁 Project Structure](#-project-structure)
- [🔧 Configuration](#-configuration)
- [🔐 Authentication](#-authentication)
- [🚢 Deployment](#-deployment)
- [📄 License](#-license)

## ✨ Features

- **User Management** – Role-based access control for five user classes (System Administrator, Transport Manager, Secretary Administrator, Senior Admin Officer, Clerk)
- **Fleet Management** – Vehicle onboarding, updating, and tracking with comprehensive vehicle details
- **Driver Management** – Driver onboarding, assignment, and license tracking
- **Work Ticket System** – Digital work ticket generation, submission with odometer readings, receipt uploads, and multi-level review workflow
- **Fuel Management Module** – Fuel card onboarding (General/Individual cards), eWallet tracking, fuel issuance recording, and automated fuel register generation
- **Document Repository** – Centralized storage for scanned receipts, bin cards, and related documents
- **Analytics & Dashboards** – Real-time monitoring of fuel consumption, vehicle efficiency, user activities, and anomaly detection
- **Responsive Design** – Fully functional across desktops, tablets, and mobile devices
- **Audit Trails** – Immutable logs for all system activities with timestamps

## 🛠️ Tech Stack

| Category | Technology |
|----------|------------|
| **Framework** | Next.js 15 (App Router) |
| **Language** | TypeScript 5.x |
| **Styling** | Tailwind CSS 3.x |
| **UI Components** | Radix UI, Custom Components |
| **State Management** | Zustand, TanStack Query |
| **HTTP Client** | Axios with interceptors |
| **Forms** | React Hook Form, Zod |
| **Package Manager** | pnpm (recommended) |
| **Deployment** | Vercel / Government infrastructure |

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- Node.js 18.17.0 or higher
- pnpm (recommended) / npm / yarn
- **Backend API** must be running (Node.js backend service)

## 🚀 Getting Started

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/ecitizen-ke/fleet-frontend.git
cd fleet-frontend
```

2. **Install dependencies**
```bash
# Using pnpm (recommended)
pnpm install

# Using npm
npm install

# Using yarn
yarn install
```

3. **Set up environment variables**
```bash
cp .env.example .env.local
```

Edit `.env.local` with your configuration:
```env
# API Configuration (Backend must be running)
NEXT_PUBLIC_API_URL=http://localhost:5000/api
# or your backend server URL
# NEXT_PUBLIC_API_URL=https://api.fleet.go.ke/api

# Application
NEXT_PUBLIC_APP_NAME=FLEET
NEXT_PUBLIC_APP_ENV=development

# Authentication (if using NextAuth with backend)
NEXTAUTH_SECRET="your-secret-key"
NEXTAUTH_URL=http://localhost:3000

# Optional: Backend endpoints
NEXT_PUBLIC_AUTH_ENDPOINT=/auth/login
NEXT_PUBLIC_USERS_ENDPOINT=/users
NEXT_PUBLIC_VEHICLES_ENDPOINT=/vehicles
NEXT_PUBLIC_DRIVERS_ENDPOINT=/drivers
NEXT_PUBLIC_WORK_TICKETS_ENDPOINT=/work-tickets
NEXT_PUBLIC_FUEL_ENDPOINT=/fuel
```

4. **Ensure Backend is Running**
The backend Node.js service must be running before starting the frontend:
```bash
# Backend should be running on its configured port
# Verify backend health at http://localhost:5000/health
```

5. **Start the development server**
```bash
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) to access the FLEET system.

### Available Scripts

| Script | Description |
|--------|-------------|
| `pnpm dev` | Start development server with Turbopack |
| `pnpm build` | Create production build |
| `pnpm start` | Start production server |
| `pnpm lint` | Run ESLint |
| `pnpm lint:fix` | Fix ESLint issues |
| `pnpm format` | Format code with Prettier |
| `pnpm type-check` | Run TypeScript type checking |

## 📁 Project Structure

```
fleet-frontend/
├── public/                      # Static assets
│   ├── images/                  # Image files
│   └── favicon.ico              # Favicon
│
├── src/
│   ├── app/                     # App Router pages
│   │   ├── (auth)/              # Authentication routes
│   │   │   ├── login/           # Login page
│   │   │   ├── register/        # Registration page
│   │   │   └── layout.tsx       # Auth layout
│   │   │
│   │   ├── (dashboard)/         # Main application routes
│   │   │   ├── dashboard/       # Dashboard home
│   │   │   │   └── page.tsx
│   │   │   ├── vehicles/        # Fleet management
│   │   │   │   ├── page.tsx     # Vehicle listing
│   │   │   │   └── [id]/        # Vehicle details
│   │   │   ├── drivers/         # Driver management
│   │   │   │   └── page.tsx
│   │   │   ├── work-tickets/    # Work ticket management
│   │   │   │   ├── page.tsx     # Work ticket listing
│   │   │   │   ├── create/      # Create work ticket
│   │   │   │   └── [id]/        # Work ticket details
│   │   │   ├── fuel/            # Fuel management
│   │   │   │   ├── cards/       # Fuel card management
│   │   │   │   ├── ewallet/     # eWallet tracking
│   │   │   │   └── register/    # Fuel register
│   │   │   ├── reports/         # Analytics and reports
│   │   │   │   └── page.tsx
│   │   │   ├── users/           # User management (Admin only)
│   │   │   │   └── page.tsx
│   │   │   ├── documents/       # Document repository
│   │   │   │   └── page.tsx
│   │   │   ├── layout.tsx       # Dashboard layout
│   │   │   └── page.tsx         # Redirect to dashboard
│   │   │
│   │   ├── api/                 # API routes (proxy to backend)
│   │   │   └── [...path]/       # API proxy
│   │   │       └── route.ts
│   │   │
│   │   ├── layout.tsx           # Root layout
│   │   ├── page.tsx             # Landing/redirect page
│   │   └── globals.css          # Global styles
│   │
│   ├── components/              # React components
│   │   ├── ui/                  # Reusable UI components
│   │   │   ├── button.tsx
│   │   │   ├── card.tsx
│   │   │   ├── input.tsx
│   │   │   ├── dialog.tsx
│   │   │   ├── table.tsx
│   │   │   └── toast.tsx
│   │   │
│   │   ├── layout/              # Layout components
│   │   │   ├── header.tsx
│   │   │   ├── sidebar.tsx
│   │   │   └── footer.tsx
│   │   │
│   │   ├── vehicles/            # Vehicle-related components
│   │   │   ├── vehicle-card.tsx
│   │   │   ├── vehicle-form.tsx
│   │   │   └── vehicle-table.tsx
│   │   │
│   │   ├── drivers/             # Driver-related components
│   │   │   ├── driver-card.tsx
│   │   │   └── driver-form.tsx
│   │   │
│   │   ├── work-tickets/        # Work ticket components
│   │   │   ├── work-ticket-form.tsx
│   │   │   ├── receipt-upload.tsx
│   │   │   └── work-ticket-list.tsx
│   │   │
│   │   ├── fuel/                # Fuel module components
│   │   │   ├── fuel-card-form.tsx
│   │   │   ├── ewallet-widget.tsx
│   │   │   └── fuel-register-table.tsx
│   │   │
│   │   ├── reports/             # Analytics components
│   │   │   ├── dashboard-charts.tsx
│   │   │   └── report-filters.tsx
│   │   │
│   │   └── providers/           # Context providers
│   │       ├── auth-provider.tsx
│   │       └── theme-provider.tsx
│   │
│   ├── lib/                     # Utility functions
│   │   ├── api.ts               # Axios instance with interceptors
│   │   ├── auth.ts              # Authentication utilities
│   │   ├── utils.ts             # Helper functions
│   │   └── validations.ts       # Zod schemas
│   │
│   ├── hooks/                   # Custom React hooks
│   │   ├── use-auth.ts
│   │   ├── use-vehicles.ts
│   │   ├── use-drivers.ts
│   │   ├── use-work-tickets.ts
│   │   ├── use-fuel.ts
│   │   └── use-toast.ts
│   │
│   ├── store/                   # Zustand stores
│   │   ├── auth-store.ts
│   │   └── ui-store.ts
│   │
│   ├── types/                   # TypeScript type definitions
│   │   ├── user.ts
│   │   ├── vehicle.ts
│   │   ├── driver.ts
│   │   ├── work-ticket.ts
│   │   ├── fuel.ts
│   │   └── index.ts
│   │
│   └── middleware.ts            # Next.js middleware (auth protection)
│
├── .env.example                 # Environment variables example
├── .eslintrc.json               # ESLint configuration
├── .gitignore                   # Git ignore file
├── .prettierrc                  # Prettier configuration
├── next.config.js               # Next.js configuration
├── tailwind.config.ts           # Tailwind CSS configuration
├── postcss.config.js            # PostCSS configuration
├── tsconfig.json                # TypeScript configuration
├── package.json                 # Dependencies and scripts
└── README.md                    # Project documentation
```

## 🔧 Configuration

### API Client Setup

```typescript
// src/lib/api.ts
import axios from 'axios';
import { getSession } from 'next-auth/react';

const api = axios.create({
  baseURL: process.env.NEXT_PUBLIC_API_URL,
  headers: {
    'Content-Type': 'application/json',
  },
});

// Request interceptor to add auth token
api.interceptors.request.use(async (config) => {
  const session = await getSession();
  if (session?.accessToken) {
    config.headers.Authorization = `Bearer ${session.accessToken}`;
  }
  return config;
});

// Response interceptor for error handling
api.interceptors.response.use(
  (response) => response.data,
  (error) => {
    if (error.response?.status === 401) {
      // Handle unauthorized access
      window.location.href = '/login';
    }
    return Promise.reject(error);
  }
);

export default api;
```

### Next.js Configuration with API Proxy

```javascript
// next.config.js
/** @type {import('next').NextConfig} */
const nextConfig = {
  images: {
    domains: ['images.unsplash.com', 'cdn.fleet.go.ke'],
  },
  reactStrictMode: true,
  swcMinify: true,
  async rewrites() {
    return [
      {
        source: '/api/:path*',
        destination: `${process.env.NEXT_PUBLIC_API_URL}/:path*`,
      },
    ];
  },
  compiler: {
    removeConsole: process.env.NODE_ENV === 'production',
  },
};

module.exports = nextConfig;
```

## 🔐 Authentication

The frontend communicates with the backend Node.js API for authentication. Users authenticate with email/credentials, and a JWT token is returned for subsequent requests.

```typescript
// src/hooks/use-auth.ts
import { useMutation } from '@tanstack/react-query';
import api from '@/lib/api';

interface LoginCredentials {
  email: string;
  password: string;
}

export function useLogin() {
  return useMutation({
    mutationFn: async (credentials: LoginCredentials) => {
      const response = await api.post('/auth/login', credentials);
      return response;
    },
  });
}
```

### Role-Based Route Protection

```typescript
// src/middleware.ts
import { withAuth } from 'next-auth/middleware';
import { NextResponse } from 'next/server';

export default withAuth(
  function middleware(req) {
    const token = req.nextauth.token;
    const path = req.nextUrl.pathname;

    // Role-based access control
    if (path.startsWith('/users') && token?.role !== 'system_administrator') {
      return NextResponse.redirect(new URL('/dashboard', req.url));
    }

    if (path.startsWith('/vehicles/create') && !['transport_manager', 'system_administrator'].includes(token?.role)) {
      return NextResponse.redirect(new URL('/vehicles', req.url));
    }

    return NextResponse.next();
  },
  {
    callbacks: {
      authorized: ({ token }) => !!token,
    },
  }
);

export const config = {
  matcher: ['/dashboard/:path*', '/vehicles/:path*', '/drivers/:path*', '/work-tickets/:path*', '/fuel/:path*', '/users/:path*'],
};
```

## 🚢 Deployment

### Prerequisites for Deployment

- Backend Node.js API must be deployed and accessible
- Environment variables configured for production

### Deploy to Vercel

```bash
# Install Vercel CLI
pnpm add -g vercel

# Deploy
vercel

# Set production environment variables
vercel env add NEXT_PUBLIC_API_URL

# Deploy to production
vercel --prod
```

### Environment Variables for Production

```env
NEXT_PUBLIC_API_URL=https://api.fleet.go.ke/api
NEXTAUTH_SECRET="production-secret"
NEXTAUTH_URL=https://fleet.go.ke
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">
  Built for the State Department for Immigration and Citizen Services
</div>
```

This README is now specifically tailored for the FLEET system frontend with:
- Clear separation from backend
- API endpoint configuration
- Backend dependency requirements
- Role-based access aligned with the five user classes
- All FLEET-specific features and modules
- API proxy configuration for development
