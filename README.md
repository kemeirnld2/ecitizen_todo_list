# Fleet Management System 
### Manages vehicles and fuel consumption 

[![Next.js](https://img.shields.io/badge/Next.js-16.x-black)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.x-blue)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.x-38B2AC)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-Proprietary-red)](LICENSE)

FLEET is a centralized web-based transport management system for the State Department for Immigration and Citizen Services that digitizes fuel consumption tracking, vehicle fleet management, and reconciliation processes through role-based access, work ticket workflows, and automated fuel register generation. The system enhances accountability and operational efficiency by providing real-time analytics, secure document storage, and comprehensive audit trails for all government vehicle operations.


## 📋 Table of Contents
- [Tech Stack](#-tech-stack)
- [Project Overview](#-project-overview)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Core Features](#-core-features)
- [Database Schema](#-database-schema)
- [API Routes](#-api-routes)
- [Authentication & RBAC](#-authentication--rbac)
- [Development Guidelines](#-development-guidelines)
- [Testing](#-testing)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [Troubleshooting](#-troubleshooting)

## 🛠 Tech Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| **Next.js** | 16.x | React framework with App Router |
| **React** | 19.x | UI library |
| **TypeScript** | 5.x | Type safety |
| **Tailwind CSS** | 4.x | Styling |
| **Supabase** | 2.x | Database, Auth, Storage |
| **date-fns** | 3.x | Date manipulation |
| **React Hook Form** | 7.x | Form handling |
| **Zod** | 3.x | Schema validation |

## 🎯 Project Overview


- **Centralized Fleet Management** – A web-based system for tracking fuel consumption, vehicle usage, and driver assignments across all government vehicles in the State Department for Immigration and Citizen Services.

-**Role-Based Access Control** – Five user roles (System Administrator, Transport Manager, Secretary Administrator, Senior Admin Officer, and Clerk) with customized permissions for secure and efficient operations.

-**Work Ticket System** – End-to-end digital workflow for generating, submitting, and reviewing work tickets with odometer readings, journey details, and receipt uploads.

-**Fuel Management Module** – Comprehensive fuel tracking through eWallet/virtual card systems, fuel card onboarding (General and Individual cards), and automated fuel register generation with calculated totals.

-**Analytics & Reporting** – Real-time dashboards for monitoring fuel consumption, vehicle efficiency, user activities, and anomaly detection with customizable report generation.

-**Document Repository** – Centralized storage for scanned receipts, bin cards, and related documentation with secure retrieval capabilities.

-**Security & Compliance** – Encrypted data transmission, role-based authorization, immutable audit trails, and full compliance with Kenya Data Protection Act.

## 🚀 Getting Started

### Prerequisites
- Node.js 20.x or higher
- npm/yarn/pnpm
- Supabase account (free tier works)
- Git

### Environment Setup

1. **Clone the repository**

git clone https://github.com/denniskibett/angazams.git
cd angazams

2. **Install dependencies**

bash
npm install
# or
yarn install
# or
pnpm install
Set up Supabase

3. **Create a new Supabase project**

Run the migration scripts in database/migrations/

Configure authentication providers (email/password)

Environment variables
Create a .env.local file:

env
# Supabase Configuration
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

# App Configuration
NEXT_PUBLIC_APP_NAME=angazaMS
NEXT_PUBLIC_APP_URL=http://localhost:3000
Run database migrations
Execute the SQL from database/schema.sql in your Supabase SQL editor.

4. **Start development server**

bash
npm run dev
# or
yarn dev
# or
pnpm dev

Visit http://localhost:3000 to see the application.

