# KisanSahayak - Agricultural Advisory Platform

## Overview

KisanSahayak is an AI-powered agricultural advisory platform designed to empower rural farmers with timely crop guidance, weather information, pest management, and resource optimization. The application provides a mobile-first, bilingual (English/Hindi) interface optimized for low-bandwidth environments and outdoor visibility.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React 18 with TypeScript for type-safe component development
- Vite as the build tool and development server for fast hot module replacement
- Wouter for lightweight client-side routing
- TanStack Query (React Query) for server state management and caching

**UI Component System**
- shadcn/ui component library (New York style variant) built on Radix UI primitives
- Tailwind CSS for utility-first styling with custom design tokens
- Class Variance Authority (CVA) for type-safe component variants
- Framer Motion for animations and transitions
- Material Design principles adapted with nature-inspired elements for agricultural context

**Design Philosophy**
- Mobile-first responsive design with low-bandwidth optimization
- High contrast color schemes for outdoor visibility
- Large touch targets for diverse user comfort levels
- System-based approach prioritizing clarity over cleverness
- Bilingual support (English/Hindi) with language context provider

**State Management**
- React Context API for global state (Language, Theme)
- TanStack Query for server-side data synchronization
- React Hook Form with Zod validation for form state

### Backend Architecture

**Server Framework**
- Express.js for REST API endpoints
- Node.js HTTP server with WebSocket support via Neon serverless
- Development and production build configurations separated

**API Design**
- RESTful endpoints organized by feature domain:
  - `/api/weather/*` - Current weather data
  - `/api/crops/*` - Crop recommendations and information
  - `/api/advisories/*` - Agricultural advisories
  - `/api/chat/*` - AI chatbot interactions
  - `/api/soil-analysis/*` - Soil testing and recommendations
  - `/api/pests-diseases/*` - Pest and disease management
  - `/api/resources/*` - Resource tracking

**Development Environment**
- Development server with Vite middleware integration for HMR
- Production server serves static built assets
- TypeScript compilation with strict mode enabled

### Data Storage

**Database**
- PostgreSQL via Neon serverless platform
- Drizzle ORM for type-safe database operations and migrations
- Schema-first approach with shared types between client and server

**Data Models**
- `farmers` - User profiles with location and language preferences
- `crops` - Crop catalog with growing requirements and profitability data
- `advisories` - Time-sensitive agricultural advisories by category and severity
- `soilAnalyses` - Soil test results with AI-generated recommendations
- `weatherData` - Current and historical weather information
- `chatMessages` - Conversation history for AI chatbot
- `pestsAndDiseases` - Pest/disease identification and treatment guides
- `resources` - Farm resource tracking (water, fertilizer, etc.)

### External Dependencies

**AI Services**
- OpenAI GPT-5 API for agricultural advisory chatbot
- System prompts customized for Hindi and English agricultural contexts
- Specialized endpoints for soil analysis recommendations

**Third-Party UI Libraries**
- Radix UI for accessible, unstyled component primitives
- Lucide React for consistent iconography
- date-fns for date formatting and manipulation
- Embla Carousel for mobile-optimized image carousels

**Development Tools**
- Replit-specific plugins for development experience (cartographer, dev banner, runtime error overlay)
- drizzle-kit for database migrations
- ESBuild for production bundling

**Session Management**
- connect-pg-simple for PostgreSQL-backed session storage
- Express session middleware (implied by connect-pg-simple dependency)

**Font Strategy**
- Google Fonts integration for typography hierarchy:
  - Inter for body text (high legibility)
  - Poppins for headings (friendly, approachable)
  - JetBrains Mono for technical data display

### Architectural Decisions

**Monorepo Structure**
- Shared TypeScript types between client and server via `@shared` alias
- Single build process producing both API server and static frontend
- Path aliases configured for clean imports (`@/`, `@shared/`, `@assets/`)

**Mobile-First Responsive Design**
- Breakpoint-driven layouts with Tailwind's responsive utilities
- Touch-optimized interactions with minimum 44px touch targets
- Simplified navigation for mobile with hamburger menu

**Offline & Low-Bandwidth Considerations**
- Aggressive query caching via TanStack Query (infinite stale time by default)
- No automatic refetch on window focus to minimize data usage
- Optimized image assets in attached_assets directory

**Internationalization Strategy**
- Language context provider with translation function
- Language preference stored per-farmer in database
- Bilingual AI prompts with language-specific system instructions

**Authentication Approach**
- Default farmer ID system for demo purposes
- In-memory user storage with interface for future database integration
- Session-based authentication ready (connect-pg-simple installed)

**Type Safety**
- End-to-end type safety from database schema to React components
- Drizzle-zod integration for runtime validation
- Strict TypeScript compilation settings