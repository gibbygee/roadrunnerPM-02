# RoadrunnerPM Technical Stack

## Core Infrastructure

### Database
- **PostgreSQL 15+**
  - Primary database system
  - Essential extensions:
    - pgAudit (audit logging)
    - pg_stat_statements (query analysis)
  - Backup: pg_dump

### API Layer
- **tRPC**
  - Type-safe API framework
  - Integration with Next.js

## Backend Stack

### Runtime & Framework
- **Node.js 18+**
- **Next.js 14+**
  - App Router
  - Server Components
  - API Routes

### ORM & Data Access
- **Drizzle ORM 0.28+**
  - Type-safe database toolkit
  - Migration management

### Authentication & Authorization
- **NextAuth.js**
  - OAuth 2.0 providers
  - JWT handling

### Validation & Type Safety
- **TypeScript 5+**
- **Zod**
  - Runtime type validation
  - Schema definition

## Frontend Stack

### Framework & UI
- **React 18+**
- **Next.js 14+**
- **TailwindCSS**
  - Styling framework
- **Shadcn/ui**
  - Component library

### State Management
- **TanStack Query (React Query) 5+**
  - Server state management

## DevOps & Infrastructure

### Deployment
- **Vercel**
  - Frontend hosting
- **GitHub Actions**
  - CI/CD pipeline

### Monitoring
- **Sentry**
  - Error tracking

### Testing
- **Jest**
  - Unit testing
- **Testing Library**
  - Component testing

## Development Tools

### Code Quality
- **ESLint**
  - Basic error prevention
- **Prettier**
  - Automatic formatting

### Version Control
- **Git**
- **GitHub**
  - Repository hosting
  - Issue tracking

## Security Measures

### Authentication
- OAuth 2.0
- JWT tokens
- Session management

### Data Protection
- SSL/TLS encryption
- Row-level security
