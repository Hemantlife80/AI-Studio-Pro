# AI Studio Pro - Replit Configuration

## Overview

AI Studio Pro is a full-stack web application that provides AI-powered content generation tools. The application offers text generation, image generation, code generation, and business idea generation capabilities using OpenAI's APIs. Built with a modern React frontend and Express.js backend, it features a clean, professional interface with dark/light theme support.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: Radix UI components with shadcn/ui styling system
- **Styling**: Tailwind CSS with CSS custom properties for theming
- **State Management**: TanStack Query (React Query) for server state management
- **Forms**: React Hook Form with Zod validation
- **Theme System**: Custom theme provider with dark/light mode support

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **API Pattern**: RESTful API design
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon serverless PostgreSQL
- **AI Integration**: OpenAI API for content generation
- **Session Management**: PostgreSQL session store

## Key Components

### Frontend Components
1. **AI Studio Main App** (`ai-studio.tsx`): Central orchestrator component managing view navigation
2. **Generation Tools**: Specialized components for each AI generation type
   - Text Generation with tone, length, and style controls
   - Image Generation with style and size options
   - Code Generation with language and complexity settings
   - Business Ideas Generation with industry and audience targeting
3. **Sidebar Navigation**: Clean navigation with visual indicators
4. **Settings Management**: API key configuration and theme controls
5. **UI Components**: Comprehensive set of accessible components from Radix UI

### Backend Services
1. **OpenAI Integration** (`server/lib/openai.ts`): Handles all AI generation requests
2. **Database Storage** (`server/storage.ts`): Manages user data, generation history, and prompt templates
3. **Route Handlers** (`server/routes.ts`): RESTful API endpoints for generation services
4. **Database Connection** (`server/db.ts`): Neon PostgreSQL connection with Drizzle ORM

### Database Schema
- **Users**: Basic user authentication and profile data
- **Generation History**: Stores all AI generation results with metadata
- **Prompt Templates**: User-created and default prompt templates

## Data Flow

1. **Client Request**: User interacts with generation forms in React components
2. **API Call**: Frontend makes HTTP requests to Express.js backend endpoints
3. **OpenAI Processing**: Backend forwards requests to OpenAI API with enhanced prompts
4. **Database Storage**: Results are optionally stored in PostgreSQL for history
5. **Response**: Generated content is returned to frontend and displayed
6. **Error Handling**: Comprehensive error handling with user-friendly messages

## External Dependencies

### Core Dependencies
- **OpenAI**: Primary AI service for all generation capabilities
- **Neon Database**: Serverless PostgreSQL hosting
- **Drizzle ORM**: Type-safe database interactions
- **TanStack Query**: Server state management and caching
- **Radix UI**: Accessible component primitives
- **Tailwind CSS**: Utility-first styling framework

### Development Dependencies
- **Vite**: Fast build tool and development server
- **TypeScript**: Static type checking
- **ESBuild**: Fast JavaScript bundler for production
- **Replit Integration**: Development environment plugins

## Deployment Strategy

### Development Environment
- **Local Development**: `npm run dev` starts both frontend and backend in development mode
- **Hot Reload**: Vite provides instant hot module replacement
- **Type Checking**: Continuous TypeScript validation
- **Database**: Drizzle Kit for schema management and migrations

### Production Build
- **Frontend Build**: Vite builds optimized static assets
- **Backend Build**: ESBuild bundles server code with external dependencies
- **Asset Serving**: Express serves static files in production
- **Environment Variables**: DATABASE_URL and OPENAI_API_KEY required

### Database Management
- **Schema Definition**: Centralized in `shared/schema.ts`
- **Migrations**: Generated and managed through Drizzle Kit
- **Connection Pooling**: Neon's built-in connection management

## Production Features for Long-Term Use

### Database Integration
- **Persistent Storage**: PostgreSQL database with Drizzle ORM for all user data
- **Generation History**: Automatic saving of all AI generations with metadata
- **Prompt Templates**: User-created and shareable prompt libraries
- **Analytics Tracking**: Comprehensive usage statistics and performance metrics

### Rate Limiting & Quota Management
- **Text Generation**: 30 requests per hour per IP
- **Image Generation**: 10 requests per hour per IP  
- **Code Generation**: 20 requests per hour per IP
- **Business Ideas**: 15 requests per hour per IP
- **Rate Limit Headers**: Clear feedback on remaining quotas and reset times

### Production-Ready Infrastructure
- **Error Handling**: Comprehensive error states with user-friendly messages
- **OpenAI Rate Limit Management**: Graceful handling of API quotas with informative feedback
- **Performance Analytics**: Real-time usage statistics and popular prompt tracking
- **Database Backup**: All generations stored for historical analysis

### Long-Term Deployment Considerations
1. **Environment Variables Required**:
   - `DATABASE_URL`: PostgreSQL connection string
   - `OPENAI_API_KEY`: OpenAI API key for content generation
   
2. **Scaling Considerations**:
   - Rate limiters can be upgraded to Redis for multi-instance deployments
   - Database can handle thousands of concurrent users
   - Analytics dashboard provides insights for usage patterns

3. **Cost Management**:
   - Built-in rate limiting prevents API quota overages
   - Usage analytics help monitor and optimize costs
   - Efficient prompt engineering reduces token usage

4. **User Management**:
   - Ready for user authentication integration
   - Anonymous usage supported with IP-based rate limiting
   - History and templates can be tied to user accounts

## Deployment Guide

### Step 1: Environment Setup
1. Set up PostgreSQL database (Neon recommended for serverless)
2. Configure `DATABASE_URL` environment variable
3. Set `OPENAI_API_KEY` with sufficient quota for expected usage

### Step 2: Database Migration
```bash
npm run db:push
```

### Step 3: Production Build
```bash
npm run build
npm start
```

### Step 4: Monitoring & Maintenance
- Monitor analytics dashboard for usage patterns
- Track OpenAI API costs through usage statistics
- Regular database backups recommended
- Update rate limits based on usage patterns

## Changelog

- June 30, 2025. Initial setup with basic AI generation tools
- June 30, 2025. Added production-ready features: PostgreSQL integration, rate limiting, analytics dashboard, comprehensive error handling, and deployment infrastructure

## User Preferences

Preferred communication style: Simple, everyday language.