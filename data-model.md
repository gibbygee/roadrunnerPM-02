# RoadrunnerPM Database Schema

## Core Tables
The database schema is defined in `db/schema.ts` and managed through Drizzle ORM. Database connection is handled in `db/index.ts`.

### Hierarchical Data Model
The core of RoadrunnerPM's data model is a strict hierarchical structure:

```
Roadmap
└── Version
    └── Category
        └── Group
            └── Area
                └── Item
```

Each Roadmap can have multiple versions, allowing for historical tracking and version comparison.

Each level is implemented as a separate table with foreign key constraints:

```sql
CREATE TABLE versions (
  id UUID PRIMARY KEY,
  name TEXT NOT NULL,
  description TEXT,
  created_at TIMESTAMP NOT NULL DEFAULT NOW()
);

CREATE TABLE categories (
  id UUID PRIMARY KEY,
  name TEXT NOT NULL,
  label TEXT NOT NULL,
  version_id UUID REFERENCES versions(id)
);

CREATE TABLE groups (
  id UUID PRIMARY KEY,
  name TEXT NOT NULL,
  label TEXT NOT NULL,
  category_id UUID REFERENCES categories(id)
);

CREATE TABLE areas (
  id UUID PRIMARY KEY,
  name TEXT NOT NULL,
  label TEXT NOT NULL,
  group_id UUID REFERENCES groups(id)
);

CREATE TABLE items (
  id UUID PRIMARY KEY,
  name TEXT NOT NULL,
  description TEXT,
  quarter TEXT NOT NULL,
  area_id UUID REFERENCES areas(id),
  created_at TIMESTAMP NOT NULL DEFAULT NOW()
);
```

## Relationships

### Core Relationship Implementation
The hierarchical relationships are enforced through Drizzle ORM relations in `db/schema.ts`:

1. **Version-Category Relationship**
```typescript
// From db/schema.ts
export const versionsRelations = relations(versions, ({ many }) => ({
  categories: many(categories),
}));

export const categoriesRelations = relations(categories, ({ one, many }) => ({
  version: one(versions, {
    fields: [categories.versionId],
    references: [versions.id],
  }),
  groups: many(groups),
}));
```

2. **Category-Group Relationship**
```typescript
export const groupsRelations = relations(groups, ({ one, many }) => ({
  category: one(categories, {
    fields: [groups.categoryId],
    references: [categories.id],
  }),
  areas: many(areas),
}));
```

3. **Group-Area Relationship**
```typescript
export const areasRelations = relations(areas, ({ one, many }) => ({
  group: one(groups, {
    fields: [areas.groupId],
    references: [groups.id],
  }),
  items: many(items),
}));
```

4. **Area-Item Relationship**
```typescript
export const itemsRelations = relations(items, ({ one }) => ({
  area: one(areas, {
    fields: [items.areaId],
    references: [areas.id],
  }),
}));
```

### Timeline Management
Items are organized by periods:
- Direct storage in `items.quarter` field
- Implementation in `db/schema.ts`
- Items are queried by their quarter for timeline views

Example query:
```typescript
const getItemsByQuarter = async (versionId: string) => {
  return db.query.items.findMany({
    where: eq(items.versionId, versionId),
    with: {
      area: {
        with: {
          group: {
            with: {
              category: true
            }
          }
        }
      }
    },
    orderBy: [items.quarter, items.createdAt]
  });
};
```

## Data Constraints and Validation

### Hierarchical Constraints
1. **Foreign Key Constraints**
   Enforced at the database level through Drizzle relations:
   ```typescript
   export const categories = pgTable("categories", {
     id: uuid("id").defaultRandom().primaryKey(),
     name: text("name").notNull(),
     label: text("label").notNull(),
     versionId: uuid("version_id")
       .notNull()
       .references(() => versions.id, { onDelete: "cascade" }),
   });
   ```

2. **Cascading Deletes**
   - Configured to maintain referential integrity
   - Deleting a parent item removes all children
   - Implemented via `onDelete: "cascade"` in foreign key references

3. **Required Fields**
   - Names and labels are required at all levels
   - Quarter assignment required for items
   - Implemented via `notNull()` constraints

## Query Patterns

1. **Hierarchical Queries**
```typescript
const getHierarchy = async (versionId: string) => {
  return db.query.categories.findMany({
    where: eq(categories.versionId, versionId),
    with: {
      groups: {
        with: {
          areas: {
            with: {
              items: true
            }
          }
        }
      }
    }
  });
};
```

2. **Timeline Queries**
```typescript
const getItemsByQuarter = async (versionId: string) => {
  return db.query.items.findMany({
    where: eq(items.versionId, versionId),
    with: {
      area: {
        with: {
          group: {
            with: {
              category: true
            }
          }
        }
      }
    },
    orderBy: [items.quarter, items.createdAt]
  });
};