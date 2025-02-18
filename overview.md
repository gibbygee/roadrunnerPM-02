# RoadrunnerPM Architecture Overview

## System Purpose

RoadrunnerPM is a roadmap visualization application designed to help teams visualize product development timelines and understand the hierarchy of features in visual form. 

The application is not meant to be used for managing roadmaps, but rather for visualizing them. Roadmap hierarchy is built in an Excel file, and the application allows for upload of this file, and then the subsequent generation of presentation-quality materials in PowerPoint.

## Technology Stack

- **Frontend**: Next.js 14 with TypeScript
- **Build System**: Node.js and npm/yarn
- **Type Safety**: TypeScript for enhanced developer experience and code reliability
- **Backend**: Express.js
- **Database**: PostgreSQL with Drizzle ORM
- **UI Framework**: shadcn/ui components
- **State Management**: TanStack Query with react-hook-form for forms
- **Routing**: wouter
- **File Processing**: xlsx for Excel, pptxgenjs for PowerPoint
- **Form Validation**: Zod

## Core Architecture Patterns

1. **Component-Based UI Architecture**
   - Reusable UI Components
     - Form components and validation
     - Navigation structure
     - Slide-in panel interface
   - Layout Components
     - Main application layout
     - Page Header
     - Content Area
     - Slide-in Panel Area (360px width)
   - Domain-Specific Components
     - RoadmapView (main roadmap visualization)
     - ItemDetailsTray (item editing interface)
     - CategorySelector (category management)
     - VersionSelector (version control interface)
   - Data Display Components
     - Cards
     - Tables
     - Charts

2. **Data Flow Architecture**
   - REST API endpoints for data operations
   - React Query for server state management
   - Custom hooks for data management
     - Roadmap data
     - Version control
     - Label management

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