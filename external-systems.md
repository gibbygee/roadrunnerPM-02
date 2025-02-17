# RoadrunnerPM External System Integration

## File Format Integration

### Excel Integration
1. **Import Capabilities**
   - Format: .xlsx
   - Required columns:
     - Category
     - Area
     - Period
     - Group
     - Item Name
     - Description


### PowerPoint Integration
1. **Presentation Generation**
   - Format: .pptx
   - Generated content:
     - Timeline views
     - Category summaries
     - Item details
     - Label statistics


## API Integration Points

### REST API Endpoints
1. **Roadmap Management**
   ```
   GET    /api/roadmap
   POST   /api/roadmap
   GET    /api/versions
   GET    /api/labels
   ```

2. **Item Management**
   ```
   POST   /api/items
   PATCH  /api/items/:id
   DELETE /api/items/:id
   ```

3. **Category Management**
   ```
   GET    /api/categories
   POST   /api/categories
   PATCH  /api/categories/:id
   ```

### File Processing Endpoints
1. **Excel Operations**
   ```
   POST   /api/import/excel
   ```

2. **PowerPoint Operations**
   ```
   GET    /api/export/ppt
   ```
