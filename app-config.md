# RoadrunnerPM Application Configuration
asdf

## Frontend Configuration

### Theme Configuration
1. **Theme Settings**
   - Location: `theme.json`
   - Purpose: Defines application-wide styling
   - Components:
     - Color schemes
     - Typography
     - Component variants

2. **Tailwind Configuration**
   - Location: `tailwind.config.ts`
   - Purpose: Custom utility classes and theme extension
   - Features:
     - Custom color palette
     - Responsive breakpoints
     - Component-specific utilities

### Vite Configuration
1. **Build Settings**
   - Location: `vite.config.ts`
   - Purpose: Frontend build configuration
   - Features:
     - Alias definitions (`@` for client/src, `@db` for database)
     - Runtime error overlay plugin
     - Theme plugin configuration
     - Build output configuration for production

2. **Environment Variables**
   - Prefix: `VITE_`
   - Purpose: Frontend-specific configuration
   - Access: `import.meta.env`

## Backend Configuration

### Express Server
1. **Server Settings**
   - Location: `server/index.ts`
   - Features:
     - Middleware configuration
     - Route registration
     - Error handling
     - WebSocket setup

2. **API Configuration**
   - CORS settings
   - Rate limiting
   - Request parsing
   - Session management (`express-session`)

### Database Configuration
1. **Drizzle Settings**
   - Location: `drizzle.config.ts`
   - Purpose: Database connection and schema management
   - Features:
     - Migration configuration
     - Schema organization (`./db/schema.ts`)
     - Query logging

2. **Connection Management**
   - Location: `db/index.ts`
   - Features:
     - Connection pooling
     - WebSocket support
     - Error handling
     - Schema type safety

## Development Tools

### TypeScript Configuration
1. **Compiler Options**
   - Location: `tsconfig.json`
   - Purpose: TypeScript compilation settings
   - Features:
     - Path aliases (`@/*`, `@db/*`)
     - ESM module configuration
     - Strict type checking
     - Project structure definition

2. **Type Definitions**
   - Location: `src/types`
   - Purpose: Global type declarations
   - Features:
     - Component props
     - API responses
     - Database models

### Development Server
1. **Watch Settings**
   - Location: `server/vite.ts`
   - Features:
     - Hot module replacement
     - Fast refresh configuration
     - Source map generation
     - Development error overlay

2. **Development Tools**
   - Browser debugging support (`@replit/vite-plugin-runtime-error-modal`)
   - React DevTools integration
   - Network request inspection
   - Automatic workflow restarts

### Replit Configuration
1. **Project Settings**
   - Location: `.replit`
   - Purpose: Replit-specific configuration
   - Features:
     - Environment modules
     - Development commands
     - Port configuration
     - Deployment settings

2. **Runtime Configuration**
   - Environments: `nodejs-20`, `web`, `postgresql-16`
   - Build command: `npm run build`
   - Run command: `npm run dev`
   - Port mapping: 5000 -> 80