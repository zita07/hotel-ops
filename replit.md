# Hotel Operations Management System

## Overview

A professional hotel operations management system designed for tracking inventory, prélèvements (withdrawals), casse (breakage), and retours (returns) across multiple hotel departments. The system serves Front of House outlets (restaurants and bars), Staff Restaurant (Al Mansouria), Cuisine, and Stewarding departments.

The application provides:
- Department-based inventory tracking with independent cost centers
- Article management with QR code generation for quick scanning
- Prélèvements, Casse, and Retours workflow management
- Real-time alerts for low stock, high breakage rates, and inventory discrepancies
- Analytics and reporting dashboards with consumption trends
- Mobile-responsive interface with QR scanner functionality
- Dark/light theme support

## Current State

The MVP is complete with all pages functional:
- Dashboard: Real-time KPIs from backend APIs
- Departments: 9 FOH outlets + Cuisine + Stewarding
- Articles: CRUD with QR code generation
- Prélèvements: Withdrawal tracking with statistics
- Casse: Breakage tracking with department ranking
- Retours: Returns to Stewarding
- Inventory: Stock management with écart calculations
- Analytics: Charts using dedicated API endpoints
- Settings: User management with secure password handling
- QR Scanner: Camera-based article lookup

## Recent Changes

- 2025-12-18: Fixed security issue - passwords are now hashed with bcrypt and omitted from API responses
- 2025-12-18: Analytics now uses dedicated /api/analytics/* endpoints
- 2025-12-18: Dashboard fetches real data instead of mock data
- 2025-12-18: All API endpoints complete with proper statistics

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight client-side routing)
- **State Management**: TanStack React Query for server state caching and synchronization
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming (light/dark mode support)
- **Forms**: React Hook Form with Zod validation
- **Charts**: Recharts for analytics visualizations
- **Build Tool**: Vite with custom plugins for Replit integration

### Backend Architecture
- **Runtime**: Node.js with Express
- **Language**: TypeScript (ESM modules)
- **API Design**: RESTful endpoints under `/api/*` prefix
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Session Management**: Express sessions with connect-pg-simple for PostgreSQL session storage
- **Build**: esbuild for production server bundling

### Data Storage
- **Primary Database**: PostgreSQL (provisioned via Replit)
- **Schema Location**: `shared/schema.ts` using Drizzle ORM table definitions
- **Migrations**: Drizzle Kit with `db:push` command for schema synchronization

### Key Design Patterns
- **Shared Types**: Schema definitions in `shared/` directory are imported by both client and server
- **Storage Abstraction**: `server/storage.ts` provides an interface layer for all database operations
- **API Request Helper**: `client/src/lib/queryClient.ts` provides centralized fetch wrapper with error handling
- **Component Architecture**: Feature pages in `client/src/pages/`, reusable UI in `client/src/components/ui/`

### Project Structure
```
├── client/src/          # React frontend
│   ├── components/      # UI components (shadcn/ui + custom)
│   ├── pages/           # Route page components
│   ├── hooks/           # Custom React hooks
│   └── lib/             # Utilities and query client
├── server/              # Express backend
│   ├── routes.ts        # API endpoint definitions
│   ├── storage.ts       # Database operations interface
│   └── db.ts            # Drizzle database connection
├── shared/              # Shared types and schema
│   └── schema.ts        # Drizzle table definitions
└── migrations/          # Database migrations (generated)
```

## External Dependencies

### Database
- **PostgreSQL**: Primary data store, connection via `DATABASE_URL` environment variable
- **Drizzle ORM**: Schema definition and query building
- **connect-pg-simple**: Session storage in PostgreSQL

### UI Framework
- **Radix UI**: Headless component primitives (dialogs, dropdowns, forms, etc.)
- **shadcn/ui**: Pre-styled component library using Radix
- **Lucide React**: Icon library
- **Recharts**: Charting library for analytics

### Third-Party Libraries
- **html5-qrcode**: QR code scanning functionality
- **qrcode**: QR code generation for articles
- **date-fns**: Date manipulation and formatting
- **Zod**: Runtime schema validation (shared between client and server)

### Development Tools
- **Vite**: Frontend build and dev server with HMR
- **esbuild**: Server bundling for production
- **TypeScript**: Type checking across the entire codebase