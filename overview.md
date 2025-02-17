# RoadrunnerPM Architecture Overview

## System Purpose
RoadrunnerPM is a roadmap management application designed to help teams visualize product development timelines and understand the hierarchy of features. The application allows for upload of roadmap items, and generation of presentation materials in PowerPoint.

## Technical Stack
- Frontend: React with TypeScript
  - Entry point: `client/src/main.tsx`
  - Root component: `client/src/App.tsx`
- Backend: Express.js
  - Entry point: `server/index.ts`
  - Route definitions: `server/routes.ts`
- Database: PostgreSQL with Drizzle ORM
  - Schema: `db/schema.ts`
  - Connection: `db/index.ts`
- UI Framework: shadcn/ui components (`client/src/components/ui/`)
- State Management: TanStack Query (`client/src/lib/queryClient.ts`)
- Routing: wouter (configured in `client/src/App.tsx`)

## Core Architecture Patterns

1. **Component-Based UI Architecture**
   - Reusable UI components in `client/src/components/ui/`
     - Form components (`form.tsx`)
     - Navigation menu (`navigation-menu.tsx`)
     - Sidebar (`sidebar.tsx`)
   - Shared layout components in `client/src/components/layout/`
     - Application layout (`AppLayout.tsx`)
     - Page layouts and containers
   - Domain-specific components in `client/src/components/roadmap/`
     - Roadmap view (`RoadmapView.tsx`)
     - Item management (`ItemEditor.tsx`)
     - Version control (`VersionSelector.tsx`)

2. **Data Flow Architecture**
   - REST API endpoints for data operations (`server/routes.ts`)
   - React Query for server state management (`client/src/lib/queryClient.ts`)
   - Custom hooks for data management (`client/src/hooks/`)
     - Roadmap data (`use-roadmaps.ts`)
     - Version control (`use-versions.ts`)
     - Label management (`use-labels.ts`)
   - Zod for runtime type validation (`client/src/types/*.ts`)

3. **Feature Organization**
   - Page-based routing with wouter (`client/src/App.tsx`)
   - Feature-specific components grouped by domain
   - Shared hooks in `client/src/hooks/`
     - Toast notifications (`use-toast.ts`)
     - Mobile detection (`use-mobile.ts`)
     - Label management (`use-labels.ts`)

## Key System Boundaries

1. **Frontend Application**
   - React application served by Vite (`vite.config.ts`)
   - Client-side routing and state management
   - UI component library integration (`client/src/components/ui/`)

Main Views:
- Home View (`/pages/home.tsx`): Landing page showing RoadmapList component
- Roadmap Detail View (`/pages/roadmap/[id].tsx`): Shows specific roadmap with:
  - CategorySelector for filtering
  - VersionSelector for version control
  - DownloadPPT for PowerPoint export
  - ExcelUpload for data import
  - RoadmapView for visualization
- Settings View (`/pages/settings.tsx`): Application settings page
- Not Found (404) View: Fallback for undefined routes

2. **Backend API**
   - Express.js REST API (`server/index.ts`)
   - Database access layer (`db/index.ts`, `db/schema.ts`)
   - File processing for Excel/PowerPoint (`server/services/`)

3. **Database Layer**
   - PostgreSQL database (connection in `db/index.ts`)
   - Drizzle ORM for type-safe queries (`db/schema.ts`)
   - Schema management and migrations (`drizzle.config.ts`)