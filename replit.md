# RST ROADLINES - Cargo Transportation Platform

## Overview

This is a full-stack web application for RST ROADLINES, a cargo transportation company operating in West Bengal, India. The platform provides booking services for both full truck and mini truck cargo transportation, along with company information and contact features.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **UI Framework**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: TanStack Query for server state management
- **Form Handling**: React Hook Form with Zod validation
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (@neondatabase/serverless)
- **Validation**: Zod schemas shared between client and server
- **Session Storage**: In-memory storage (MemStorage class) as fallback

### Deployment Strategy
- **Development**: Vite dev server with HMR
- **Production**: Express server serving static files
- **Database Migrations**: Drizzle Kit for schema management
- **Environment**: Designed for Replit deployment

## Key Components

### Database Schema
Located in `shared/schema.ts`:
- **Bookings Table**: Stores cargo booking requests with pickup/delivery details, service type, weight, estimated fare, contact info, and status tracking
- **Contacts Table**: Stores general inquiry messages from customers
- **Validation**: Zod schemas for type-safe data validation across frontend and backend

### API Endpoints
Located in `server/routes.ts`:
- `POST /api/bookings` - Create new booking
- `GET /api/bookings` - Retrieve all bookings
- `GET /api/bookings/:id` - Get specific booking
- `PATCH /api/bookings/:id/status` - Update booking status
- `POST /api/contacts` - Submit contact form

### Frontend Components
Located in `client/src/components/`:
- **Navigation**: Sticky header with smooth scroll navigation
- **Hero Section**: Main landing area with call-to-action buttons
- **Services Section**: Details about full truck and mini truck services
- **Booking System**: Form for cargo booking with real-time fare estimation
- **Fleet Gallery**: Image showcase of company vehicles
- **Founder Section**: About the company founder with achievements
- **Contact Section**: Contact form and company information
- **Footer**: Links, social media, and company details

## Data Flow

1. **User Interaction**: Users interact with React components using shadcn/ui form elements
2. **Form Validation**: React Hook Form validates input using Zod schemas
3. **API Communication**: TanStack Query handles HTTP requests to Express endpoints
4. **Server Processing**: Express routes validate data and interact with storage layer
5. **Database Operations**: Drizzle ORM manages PostgreSQL interactions
6. **Response Handling**: Success/error states trigger toast notifications

## External Dependencies

### UI and Styling
- **Radix UI**: Accessible component primitives
- **Tailwind CSS**: Utility-first CSS framework
- **Lucide React**: Icon library
- **Class Variance Authority**: Component variant management

### Data Management
- **TanStack Query**: Server state management and caching
- **React Hook Form**: Form state and validation
- **Zod**: Runtime type validation
- **Drizzle ORM**: Type-safe database operations

### Development Tools
- **Vite**: Fast build tool with HMR
- **ESBuild**: Production bundling
- **TypeScript**: Static type checking
- **PostCSS**: CSS processing with Autoprefixer

## Deployment Strategy

The application is configured for Replit deployment with:
- **Development Mode**: `npm run dev` starts both Vite dev server and Express API
- **Production Build**: `npm run build` creates optimized client bundle and server code
- **Database Setup**: `npm run db:push` applies Drizzle schema to PostgreSQL
- **Environment Variables**: `DATABASE_URL` required for PostgreSQL connection
- **Static Serving**: Express serves built React app in production

The architecture separates concerns clearly with shared types/schemas, independent client/server code, and a storage abstraction layer that can switch between in-memory and database storage based on configuration.