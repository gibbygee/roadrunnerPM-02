# RoadrunnerPM Deployment Configuration


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