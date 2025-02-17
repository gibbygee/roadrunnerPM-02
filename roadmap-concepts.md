# RoadrunnerPM Domain Concepts

## Core Domain Objects
Implementation: See `db/schema.ts` for the database schema implementation of these concepts.

### Roadmap Hierarchy
The application follows a strict hierarchical structure:
```
Version
└── Category (Product Lines/Solutions)
    └── Group (Products/Capabilities)
        └── Area (Modules/Functions)
            └── Item (Features/Epics)
```

Each level is implemented in the database schema with specific tables and relationships:
- Version (`versions` table) - The top-level container for all roadmap data.
- Category (`categories` table) - Logical groupings of Groups. A Category can have one or more Groups.
- Group (`groups` table) - Logical grouping of Areas. A Group has one or more Areas.
- Area (`areas` table) - Logical grouping of Items. An Area can have one or more Items.
- Period (stored in `items.quarter`) - Time period in which the Item is released.
- Items (`items` table) - Specific features or releasable capabilities of the roadmap.
- Item Descriptions (stored in `items.description`) - Descriptions of the Items.

### Category
Logical groupings within a roadmap that help organize the Groups beneath it. Categories represent high-level organization such as:
- Product Lines
- Solutions
- Strategic Initiatives

Implementation:
- Schema: `db/schema.ts` categories table
- API: `server/routes/categories.ts` for category management endpoints
- UI: `client/src/components/roadmap/CategorySelector.tsx`

### Group
Logical groupings within a Category that help organize Areas. Groups typically represent:
- Products
- Capabilities
- Feature Sets

Implementation:
- Schema: `db/schema.ts` groups table
- API: `server/routes/groups.ts` for group management endpoints
- UI: `client/src/components/roadmap/GroupSelector.tsx`

### Area
Logical groupings within a Group that help organize Items. Areas commonly represent:
- Modules
- Functions
- Components

Implementation:
- Schema: `db/schema.ts` areas table
- API: `server/routes/areas.ts` for area management endpoints
- UI: `client/src/components/roadmap/AreaSelector.tsx`

### Item
The leaf node of the hierarchy. Items are individual elements representing:
- Features
- Epics
- User Stories

Implementation:
- Schema: `db/schema.ts` items table
- API: `server/routes/items.ts` for item management endpoints
- UI: `client/src/components/roadmap/ItemEditor.tsx`

### Roadmaps and Versioning
Roadmaps are managed through versions, enabling:
- Historical tracking through `versions` table
- Version comparison (implementation in `client/src/components/roadmap/VersionCompare.tsx`)
- Planning scenarios and what-if analysis

## Business Rules

1. **Version Management**
   - Versions correspond to roadmaps that have been uploaded from Excel
   - Each version represents one upload
   - Only one version can be active at a time
   - Previous versions are preserved for historical reference

   Implementation:
   - Version selection: `client/src/components/roadmap/VersionSelector.tsx`
   - Version storage: `db/schema.ts` versions table
   - Version comparison: `client/src/components/roadmap/VersionCompare.tsx`

2. **Hierarchical Rules**
   All relationships are enforced through foreign key constraints in `db/schema.ts`:
   - Items must belong to an Area
   - Areas must belong to a Group
   - Groups must belong to a Category
   - Categories must belong to a Version

   Implementation:
   - Data model: `db/schema.ts` with enforced foreign keys
   - UI validation: `client/src/components/roadmap/ItemEditor.tsx`
   - API validation: `server/routes/items.ts`

3. **Timeline Management**
   Items are organized temporally:
   - Items organized by quarters (`items.quarter`)
   - Quarter assignments for release timing
   - Creation timestamps for history

   Implementation:
   - Timeline view: `client/src/components/roadmap/TimelineView.tsx`
   - Quarter editor: `client/src/components/roadmap/QuarterEditor.tsx`
   - Timeline queries: `server/routes/timeline.ts`