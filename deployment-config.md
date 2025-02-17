# RoadrunnerPM Deployment Configuration

## Replit Configuration
The deployment configuration is defined in `.replit` and sets up the necessary environment for both development and production.

### Environment Setup
```toml
modules = ["nodejs-20", "web", "postgresql-16"]
run = "npm run dev"
hidden = [".config", ".git", "generated-icon.png", "node_modules", "dist"]
```

### Deployment Configuration
```toml
[deployment]
deploymentTarget = "cloudrun"
build = ["npm", "run", "build"]
run = ["npm", "run", "start"]
```

### Port Configuration
```toml
[[ports]]
localPort = 5000
externalPort = 80
```

## Workflow Configuration

### Development Workflow
1. **Project Start**
   ```toml
   [workflows]
   runButton = "Project"

   [[workflows.workflow]]
   name = "Project"
   mode = "parallel"
   ```

2. **Application Start**
   ```toml
   [[workflows.workflow]]
   name = "Start application"

   [[workflows.workflow.tasks]]
   task = "packager.installForAll"

   [[workflows.workflow.tasks]]
   task = "shell.exec"
   args = "npm run dev"
   waitForPort = 5000
   ```

## Build Process
1. **Development Mode**
   - Uses Vite development server
   - Hot module replacement enabled
   - Serves on port 5000

2. **Production Build**
   - Builds optimized assets
   - Serves via Express.js
   - Configured for Cloud Run deployment

## Environment Variables
1. **Required Variables**
   - DATABASE_URL: PostgreSQL connection string
   - Additional secrets managed via Replit Secrets

2. **Optional Variables**
   - Environment-specific configurations
   - Feature flags
   - External service integrations

## Security Considerations
1. **Database Access**
   - Secured via environment variables
   - Connection pooling configured
   - SSL/TLS encryption enabled

2. **API Security**
   - Rate limiting implemented
   - CORS configured
   - Request validation