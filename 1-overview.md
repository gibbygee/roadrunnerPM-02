# RoadrunnerPM Architecture Overview

## System Purpose
RoadrunnerPM is a roadmap management application designed to help teams visualize product development timelines and understand the hierarchy of features. The application allows for upload of roadmap items, and generation of presentation materials in PowerPoint.

## Technology Stack

- **Frontend**: Next.js 14 with TypeScript
- **Build System**: Node.js and npm/yarn
- **Type Safety**: TypeScript for enhanced developer experience and code reliability
- Backend: Express.js
- Database: PostgreSQL with Drizzle ORM
- UI Framework: shadcn/ui components
- State Management: TanStack Query
- Routing: wouter

## Core Architecture Patterns

1. **Component-Based UI Architecture**
   - Reusable UI components
     - Form components
     - Navigation menu
     - Sidebar
   - Shared layout components
     - Application layout
     - Page layouts and containers
   - Domain-specific components
     - Roadmap view
     - Item management
     - Version control

2. **Data Flow Architecture**
   - REST API endpoints for data operations
   - React Query for server state management
   - Custom hooks for data management
     - Roadmap data
     - Version control
     - Label management
   - Zod for runtime type validation

3. **Feature Organization**
   - Page-based routing with wouter
   - Feature-specific components grouped by domain
   - Shared hooks
     - Toast notifications
     - Mobile detection
     - Label management

## Key System Boundaries

1. **Frontend Application**
   - React application served by Vite
   - Client-side routing and state management
   - UI component library integration

Main Views:
- Home View: Landing page showing RoadmapList component
- Roadmap Detail View: Shows specific roadmap with:
  - CategorySelector for filtering
  - VersionSelector for version control
  - DownloadPPT for PowerPoint export
  - ExcelUpload for data import
  - RoadmapView for visualization
- Settings View: Application settings page
- Not Found (404) View: Fallback for undefined routes

2. **Backend API**
   - Express.js REST API
   - Database access layer
   - File processing for Excel/PowerPoint

3. **Database Layer**
   - PostgreSQL database
   - Drizzle ORM for type-safe queries
   - Schema management and migrations