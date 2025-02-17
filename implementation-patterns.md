# RoadrunnerPM Implementation Patterns

## Frontend Patterns

### Component Organization
1. **Layout Components**
   - Location: `client/src/components/layout/`
   - `AppLayout.tsx`: Main application layout wrapper
   - Purpose: Consistent page structure and navigation
   - Implements: Sidebar (`client/src/components/ui/sidebar.tsx`)

2. **Domain Components**
   - Location: `client/src/components/roadmap/*`
   - Purpose: Specific roadmap management functionality
   - Key Components:
     - `RoadmapView.tsx`: Main roadmap visualization
     - `ItemDetailsTray.tsx`: Item editing interface
     - `CategorySelector.tsx`: Category management
     - `VersionSelector.tsx`: Version control interface

3. **UI Components**
   - Location: `client/src/components/ui/*`
   - Purpose: Reusable UI elements
   - Based on shadcn/ui with custom styling
   - Key Files:
     - `form.tsx`: Form components and validation
     - `navigation-menu.tsx`: Navigation structure
     - `sidebar.tsx`: Collapsible sidebar interface

### State Management
1. **Server State**
   - Tool: TanStack Query
   - Pattern: Centralized query client
   - Location: `lib/queryClient.ts`
   - Key Queries:
     - Version fetching
     - Hierarchical data loading
     - Timeline data loading

2. **Form State**
   - Tool: react-hook-form with Zod
   - Pattern: Form validation schemas
   - Implementation: `client/src/components/ui/form.tsx`
   - Component-level form state
   - Validation for hierarchical data

### Navigation
1. **Routing**
   - Tool: wouter
   - Pattern: Page-based routing
   - Location: `client/src/App.tsx`
   - Key Routes:
     - Home (Roadmap List)
     - Roadmap Detail View
     - Settings
     - Not Found (404)

## Backend Patterns

### API Organization
1. **Route Structure**
   - Location: `server/routes.ts`
   - Pattern: Feature-based grouping
   - RESTful endpoint design
   - Key Endpoints:
     - `/api/versions`
     - `/api/roadmap`
     - `/api/items`
     - `/api/labels`

2. **Data Access**
   - Tool: Drizzle ORM
   - Pattern: Type-safe queries
   - Location: `db/schema.ts`
   - Key Patterns:
     - Hierarchical queries
     - Timeline-based queries
     - Lens-based filtering

### File Processing
1. **Excel Integration**
   - Tool: xlsx library
   - Purpose: Import/export roadmap data
   - Location: `client/src/components/roadmap/ExcelUpload.tsx`
   - Features:
     - Category/Group/Area mapping
     - Item import with hierarchy
     - Timeline data import

2. **PowerPoint Generation**
   - Tool: pptxgenjs
   - Purpose: Presentation creation
   - Location: `client/src/components/roadmap/DownloadPPT.tsx`
   - Features:
     - Timeline visualization
     - Hierarchy representation
     - Label integration