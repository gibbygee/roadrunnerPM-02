# RoadrunnerPM Implementation Patterns

## Frontend Patterns

### Component Organization
1. **Layout Components**
   - Main application layout
   -  Purpose: Consistent page structure and navigation
   - Sidebar

2. **Domain Components**
   - Purpose: Specific roadmap management functionality
   - Key Components:
     - RoadmapView: Main roadmap visualization
     - ItemDetailsTray: Item editing interface
     - CategorySelector: Category management
     - VersionSelector: Version control interface

3. **UI Components**
   - Purpose: Reusable UI elements
   - Based on shadcn/ui with custom styling
   - Key Components:
     - Form components and validation
     - Navigation structure
     - Collapsible sidebar interface

### State Management
1. **Server State**
   - Tool: TanStack Query
   - Pattern: Centralized query client
   - Key Queries:
     - Version fetching
     - Hierarchical data loading
     - Timeline data loading

2. **Form State**
   - Tool: react-hook-form with Zod
   - Pattern: Form validation schemas
   - Component-level form state
   - Validation for hierarchical data

### Navigation
1. **Routing**
   - Tool: wouter
   - Pattern: Page-based routing
   - Key Routes:
     - Home (Roadmap List)
     - Roadmap Detail View
     - Settings
     - Not Found (404)

## Backend Patterns

### API Organization
1. **Route Structure**
   - Pattern: Feature-based grouping
   - RESTful endpoint design
   - Key Endpoints:
     - /api/versions
     - /api/roadmap
     - /api/items
     - /api/labels

2. **Data Access**
   - Tool: Drizzle ORM
   - Pattern: Type-safe queries
   - Key Patterns:
     - Hierarchical queries
     - Timeline-based queries
     - Lens-based filtering

### File Processing
1. **Excel Integration**
   - Tool: xlsx library
   - Purpose: Import/export roadmap data
   - Features:
     - Category/Group/Area mapping
     - Item import with hierarchy
     - Timeline data import

2. **PowerPoint Generation**
   - Tool: pptxgenjs
   - Purpose: Presentation creation
   - Features:
     - Timeline visualization
     - Hierarchy representation
     - Label integration