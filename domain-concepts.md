# RoadrunnerPM Domain Concepts

## Core Domain Objects
Implementation: See the database schema for implementation of these concepts.

### Domain Terminology
- **Roadmap**: A strategic planning document that outlines the planned development and release of features over time
- **Version**: A snapshot of a roadmap at a specific point in time
- **Timeline**: The temporal organization of items, typically divided into quarters or specific time periods


### Roadmap Hierarchy
The application follows a strict hierarchical structure:

Roadmap 
└── Roadmap Version (example: Version 1)
   └── Category (example: Product Lines/Solutions)
      └── Group (example: Products/Capabilities)
         └── Area (example: Modules/Functions)
               └── Item (example: Features/Epics)

Each level is implemented in the database schema with specific tables and relationships:
- Roadmap Version - The top-level container for all roadmap data.
- Category - Logical groupings of Groups. A Category can have one or more Groups.
- Group - Logical grouping of Areas. A Group has one or more Areas.
- Area - Logical grouping of Items. An Area can have one or more Items.
- Period - Time period in which the Item is released.
- Items - Specific features or releasable capabilities of the roadmap.
- Item Descriptions - Descriptions of the Items.

### Category
Logical groupings within a roadmap that help organize the Groups beneath it. Categories represent high-level organization such as, for example:
- Product Lines (e.g., Enterprise Suite, Cloud Platform)
- Solutions (e.g., Security Solutions, Analytics Platform)
- Strategic Initiatives (e.g., Digital Transformation, Platform Modernization)

### Group
Logical groupings within a Category that help organize Areas. Groups typically represent, for example:
- Products (e.g., Mobile App, Web Portal)
- Capabilities (e.g., Authentication, Data Processing)
- Feature Sets (e.g., User Management, Reporting)

### Area
Logical groupings within a Group that help organize Items. Areas commonly represent, for example:
- Modules (e.g., Admin Interface, API Gateway)
- Functions (e.g., User Authentication, Data Export)
- Components (e.g., Dashboard Widgets, Search Engine)

### Item
The fundamental unit of delivery in the roadmap. Items are individual elements representing, for example:
- Features (e.g., Single Sign-On, Dark Mode)
- Epics (e.g., Payment Processing System)
- User Stories (e.g., Password Reset Flow)

### Timeline Management

Items are organized temporally through:

- **Periods**: Defined time segments (for example,quarters or months)

## Business Rules

1. **Version Management**
   - Each version represents a complete roadmap snapshot
   - Versions are created upon Excel file upload
   - Only one version can be active at a time
   - Historical versions are preserved for reference and comparison

2. **Hierarchical Rules**
   All relationships are enforced through foreign key constraints:
   - Items must belong to an Area
   - Areas must belong to a Group
   - Groups must belong to a Category
   - Categories must belong to a Version

3. **Timeline Rules**
   - All items must be assigned to a specific Period
   - Items cannot span multiple periods
   - All items must have a Period assigned

4. **Access Control**
   - Only authorized users can create new versions
   - Version comparison requires appropriate permissions
   - Historical versions are read-only