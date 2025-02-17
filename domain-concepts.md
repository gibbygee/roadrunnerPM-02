# RoadrunnerPM Domain Concepts

## Core Domain Objects
Implementation: See the database schema for implementation of these concepts.

### Roadmap Hierarchy
The application follows a strict hierarchical structure:

Version
└── Category (Product Lines/Solutions)
    └── Group (Products/Capabilities)
        └── Area (Modules/Functions)
            └── Item (Features/Epics)

Each level is implemented in the database schema with specific tables and relationships:
- Version - The top-level container for all roadmap data.
- Category - Logical groupings of Groups. A Category can have one or more Groups.
- Group - Logical grouping of Areas. A Group has one or more Areas.
- Area - Logical grouping of Items. An Area can have one or more Items.
- Period - Time period in which the Item is released.
- Items - Specific features or releasable capabilities of the roadmap.
- Item Descriptions - Descriptions of the Items.

### Category
Logical groupings within a roadmap that help organize the Groups beneath it. Categories represent high-level organization such as:
- Product Lines
- Solutions
- Strategic Initiatives

### Group
Logical groupings within a Category that help organize Areas. Groups typically represent:
- Products
- Capabilities
- Feature Sets

### Area
Logical groupings within a Group that help organize Items. Areas commonly represent:
- Modules
- Functions
- Components

### Item
The leaf node of the hierarchy. Items are individual elements representing:
- Features
- Epics
- User Stories

### Roadmaps and Versioning
Roadmaps are managed through versions, enabling:
- Historical tracking
- Version comparison
- Planning scenarios and what-if analysis

## Business Rules

1. **Version Management**
   - Versions correspond to roadmaps that have been uploaded from Excel
   - Each version represents one upload
   - Only one version can be active at a time
   - Previous versions are preserved for historical reference

2. **Hierarchical Rules**
   All relationships are enforced through foreign key constraints:
   - Items must belong to an Area
   - Areas must belong to a Group
   - Groups must belong to a Category
   - Categories must belong to a Version

3. **Timeline Management**
   Items are organized temporally:
   - Items organized by quarters
   - Quarter assignments for release timing
   - Creation timestamps for history