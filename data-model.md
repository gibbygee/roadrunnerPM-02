# RoadrunnerPM Database Schema

## Core Tables
The database schema is defined and managed through Drizzle ORM.

### Hierarchical Data Model
The core of RoadrunnerPM's data model is a strict hierarchical structure:

Roadmap
└── Version
    └── Category
        └── Group
            └── Area
                └── Item

Each Roadmap can have multiple versions, allowing for historical tracking and version comparison.

Each level is implemented as a separate table with foreign key constraints.

## Relationships

### Core Relationship Implementation
The hierarchical relationships are enforced through Drizzle ORM relations:

1. **Version-Category Relationship**
- Versions have many categories
- Categories belong to one version

2. **Category-Group Relationship**
- Categories have many groups
- Groups belong to one category

3. **Group-Area Relationship**
- Groups have many areas
- Areas belong to one group

4. **Area-Item Relationship**
- Areas have many items
- Items belong to one area

### Timeline Management
Items are organized by periods:
- Direct storage in quarter field
- Items are queried by their quarter for timeline views

## Data Constraints and Validation

### Hierarchical Constraints
1. **Foreign Key Constraints**
   - Enforced at the database level through Drizzle relations
   - Maintains referential integrity between levels

2. **Cascading Deletes**
   - Configured to maintain referential integrity
   - Deleting a parent item removes all children

3. **Required Fields**
   - Names and labels are required at all levels
   - Quarter assignment required for items

## Query Patterns

1. **Hierarchical Queries**
- Support for full tree traversal
- Efficient nested relationship loading
- Support for partial tree loading

2. **Timeline Queries**
- Quarter-based item retrieval
- Support for hierarchical context
- Ordered by quarter and creation time