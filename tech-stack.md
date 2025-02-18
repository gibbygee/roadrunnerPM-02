# RoadrunnerPM Technical Stack

## Core Infrastructure

### Database
- **PostgreSQL 15+**
  - Primary database system
  - Essential extensions:
    - pgAudit (audit logging)
    - pg_stat_statements (query analysis)
  - Backup: pg_dump

### Database Layer
- **Drizzle ORM**
  - Purpose: Database connection and schema management
  - Features:
    - Migration configuration
    - Schema organization
    - Query logging
  - Benefits:
    - Type-safe database operations
    - Zero-runtime overhead
    - First-class TypeScript support

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

### Authentication & Authorization
- **NextAuth.js**
  - OAuth 2.0 providers
  - JWT handling

### Validation & Type Safety
- **TypeScript 5+**
- **Zod**
  - Runtime type validation
  - Schema definition
  - Form validation
  - API payload validation
  - Database schema validation

## Frontend Stack

### Framework & UI
- **React 18+**
- **Next.js 14+**
  - App Router
  - Server Components
  - Built-in bundling and optimization
  - Development server with Fast Refresh
  - Production build optimization
- **CSS Modules**
  - Scoped CSS styling
  - Built into Next.js
- **Shadcn/ui**
  - Component library

### State Management
- **TanStack Query (React Query) 5+**
  - Server state management

## DevOps & Infrastructure

### Deployment

- **Vercel**
  - Frontend hosting
  - Hot module replacement in development
  - Production build optimization
  - Development server on port 5000
  - Environment configurations:
    - Required variables:
      - DATABASE_URL
      - AUTH_SECRET
      - [Other secrets managed via environment]
    - Optional variables:
      - Feature flags
      - External service integrations
      - Environment-specific configurations

- **GitHub Actions**
  - CI/CD pipeline
  - Build validation
  - Automated testing

### Development Server
- **Next.js Development Server**
  - Fast Refresh enabled
  - Built-in optimization
  - CORS configuration
  - Rate limiting implementation
  - Request validation middleware

### Monitoring
- **Sentry**
  - Error tracking

### Testing
- **Jest**
  - Unit testing
- **Testing Library**
  - Component testing

### Database Configuration
- **PostgreSQL 15+**
  - Connection pooling configured
  - SSL/TLS encryption enabled
  - Secured via environment variables

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
