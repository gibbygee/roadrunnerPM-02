# RoadrunnerPM UI Patterns and Components

## UI Component Library
The application uses shadcn/ui components, customized for RoadrunnerPM's specific needs.

### Core Components

1. **Navigation**
   - Purpose: Application navigation and structure
   - Components:
     - Navigation menu
     - Context menus

2. **Data Display**
   - Purpose: Information visualization
   - Components:
     - Cards
     - Tables
     - Charts

3. **Forms and Inputs**
   - Purpose: Data entry and editing
   - Components:
     - Form fields
     - Select dropdowns
     - Multi-select

### Layout Patterns

1. **Page Layout**
   AppLayout
   ├── Main Content Area (flex-grow: 1)
   │   ├── Page Header
   │   └── Content
   └── [Optional] Slide-in Panel Area (width: 360px)

2. **Roadmap View Layout**
   RoadmapView (within Main Content Area)
   ├── Roadmap List (Home Page)
   │   ├── Create Roadmap Button
   │   └── Roadmap Table with Latest Version Links
   └── Roadmap Detail View
       ├── Version Controls
       ├── Download PowerPoint Button
       ├── Upload Excel Button
       ├── Category Headers
       └── Item Grid (onClick → opens RoadmapItemPanel)

   RoadmapItemPanel (within Slide-in Panel Area)
   ├── Panel Header
   │   ├── Item Title
   │   └── Close Button
   ├── Item Details
   └── Item Actions

### Interaction Patterns

1. **Item Management**
   - Click to edit item details
   - Context menu for quick actions

2. **Versions**
   - Version selector in header

3. **Timeline Visualization**
   - Period-based layout

### Responsive Design

1. **Breakpoints**
   - Mobile: < 640px
   - Tablet: 640px - 1024px
   - Desktop: > 1024px

2. **Layout Adaptations**
   - Scrollable timelines
   - Responsive grid system