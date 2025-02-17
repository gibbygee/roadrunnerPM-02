# RoadrunnerPM UI Patterns and Components

## UI Component Library
The application uses shadcn/ui components, customized for RoadrunnerPM's specific needs.

### Core Components

1. **Navigation**
   - Purpose: Application navigation and structure
   - Components:
     - Sidebar navigation (`client/src/components/ui/sidebar.tsx`)
     - Navigation menu (`client/src/components/ui/navigation-menu.tsx`)
     - Context menus (`client/src/components/ui/context-menu.tsx`)

2. **Data Display**
   - Purpose: Information visualization
   - Components:
     - Cards (`client/src/components/ui/card.tsx`)
     - Tables (`client/src/components/ui/table.tsx`)
     - Charts (`client/src/components/ui/chart.tsx`)

3. **Forms and Inputs**
   - Purpose: Data entry and editing
   - Components:
     - Form fields (`client/src/components/ui/form.tsx`)
     - Select dropdowns (`client/src/components/ui/select.tsx`)
     - Multi-select (`client/src/components/ui/multi-select.tsx`)

### Layout Patterns

1. **Page Layout**
   ```
   AppLayout (client/src/components/layout/AppLayout.tsx)
   ├── Sidebar Navigation (client/src/components/ui/sidebar.tsx)
   ├── Main Content Area
   │   ├── Page Header
   │   └── Content
   └── Context Panels
   ```

2. **Roadmap View Layout**
   ```
   RoadmapView (client/src/components/roadmap/RoadmapView.tsx)
   ├── Roadmap List (Home Page)
   │   ├── Create Roadmap Button
   │   └── Roadmap Table with Latest Version Links
   ├── Roadmap Detail View
   │   ├── Filters Bar
   │   ├── Version Controls
   │   ├── Download PowerPoint Button
   │   ├── Upload Excel Button
   │   ├── Category Headers
   │   ├── Item Grid
   │   └── Details Tray
   ```

### Interaction Patterns

1. **Item Management**
   - Click to edit item details (`client/src/components/roadmap/ItemEditor.tsx`)
   - Drag and drop for hierarchy management (`client/src/components/roadmap/DragDrop.tsx`)
   - Context menu for quick actions (`client/src/components/ui/context-menu.tsx`)

2. **Versions**
   - Version selector in header (`client/src/components/roadmap/VersionSelector.tsx`)
   - Version comparison view (`client/src/components/roadmap/VersionCompare.tsx`)
   - Version history timeline (`client/src/components/roadmap/VersionHistory.tsx`)

3. **Timeline Visualization**
   - Quarter-based layout (`client/src/components/roadmap/TimelineView.tsx`)
   - Collapsible hierarchy levels (`client/src/components/roadmap/HierarchyView.tsx`)
   - Filterable by lens attributes (`client/src/components/roadmap/LensFilter.tsx`)

4. **Lens System Interface**
   - Lens selector dropdown (`client/src/components/roadmap/LensSelector.tsx`)
   - Multi-select attribute filters (`client/src/components/roadmap/AttributeFilter.tsx`)
   - Tag-based item display (`client/src/components/roadmap/ItemTags.tsx`)

### Responsive Design

1. **Breakpoints**
   - Mobile: < 640px
   - Tablet: 640px - 1024px
   - Desktop: > 1024px

2. **Layout Adaptations**
   - Collapsible sidebar on mobile (`client/src/components/ui/sidebar.tsx`)
   - Scrollable timelines (`client/src/components/roadmap/TimelineScroll.tsx`)
   - Responsive grid system (`client/src/components/ui/grid.tsx`)