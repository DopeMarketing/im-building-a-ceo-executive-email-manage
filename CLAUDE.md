# CLAUDE.md - AI Development Brief

> **CRITICAL:** Always read this file completely before starting any coding session on this project.

## Project Overview

CEO Executive Email Management Tool — An AI-powered platform that transforms company knowledge base documents into department-specific training materials, SOPs, and automated workflows. The system integrates with HubSpot CRM, Slack, Google Sheets, and multiple AI services to streamline internal documentation and training processes.

## Tech Stack
- **Framework:** Next.js 15 (App Router)
- **Database:** Supabase (PostgreSQL)
- **Language:** TypeScript (strict mode)
- **Styling:** Tailwind CSS
- **Deployment:** Vercel
- **AI Services:** ChatGPT, Claude
- **Integrations:** HubSpot, Apollo, Twilio, ZoomInfo, GoHighLevel, Lemlist, Salesloft, Stripe, QuickBooks, Gmail, Slack

## Folder Structure


app/
├── (auth)/                 # Public auth pages (login, signup)
├── (dashboard)/            # Protected dashboard pages
│   ├── dashboard/          # Main dashboard
│   ├── knowledge-base/     # Knowledge base management
│   ├── training/           # Training material generation
│   ├── sops/              # SOP creation and management
│   ├── integrations/      # Integration settings
│   ├── notifications/     # Notification center
│   ├── recommendations/   # Document recommendations
│   └── settings/          # User settings
├── api/                   # API routes and webhooks
└── globals.css           # Global styles

components/
├── ui/                   # Shadcn/ui components
├── dashboard/            # Dashboard-specific components
├── auth/                # Authentication components
└── integrations/        # Integration-specific components

lib/
├── utils.ts             # Utility functions
├── validations.ts       # Zod schemas
├── ai/                  # AI service integrations
├── integrations/        # Third-party API clients
└── constants.ts         # App constants

db/
├── queries/             # Database queries (server-side only)
├── mutations/           # Database mutations (server-side only)
└── types.ts             # Generated Supabase types

actions/
├── auth.ts              # Authentication server actions
├── knowledge-base.ts    # Knowledge base server actions
├── training.ts          # Training material server actions
├── sops.ts              # SOP server actions
└── integrations.ts      # Integration server actions

supabase/
├── migrations/          # Database migrations
└── config.ts            # Supabase client configuration


## Coding Conventions

### TypeScript Rules
- **Strict mode enabled** — no `any` types allowed
- All functions must have explicit return types
- Use proper TypeScript interfaces for all data structures
- Import types with `import type { ... }`

### Component Architecture
- **Server Components by default** — use "use client" only when necessary
- Client components only for interactivity (forms, state management)
- Keep server components in the app directory
- Reusable components go in /components

### Data Access Rules
- **All database queries only in /db directory**
- Use Supabase client with proper RLS policies
- Server actions in /actions directory only
- Never expose database queries to client components

### Business Logic Rules
- **Pure functions in /lib directory**
- Server actions handle form submissions and mutations
- No business logic in component files
- API integrations isolated in /lib/integrations

### Security Rules
- **No secrets in client components** — use server actions
- All environment variables prefixed appropriately
- Authentication required for all dashboard routes
- Validate all inputs with Zod schemas

## Current State: Generated Scaffold

### ✅ What's Built
- Complete database schema with 13 tables
- Authentication system with role-based access (Owner, Researcher)
- Route structure for all 19 pages from site map
- Integration stubs for all 12 third-party services
- Basic UI components and dashboard layout
- Environment variable configuration
- Supabase RLS policies for data security

### 📊 Database Tables
- `users` — User authentication and profiles
- `knowledge_base_documents` — Uploaded company documents
- `departments` — Company department structure
- `training_materials` — Generated training content
- `sop_templates` — SOP templates and formats
- `sops` — Generated standard operating procedures
- `crm_integrations` — HubSpot integration settings
- `crm_records` — Synced CRM data
- `slack_configurations` — Slack workspace settings
- `slack_notifications` — Notification history
- `document_recommendations` — AI recommendations
- `export_jobs` — Document export tracking
- `ai_api_configurations` — AI service settings

## 🚀 What to Build Next: v1 Features

### 1. Knowledge Base Document Parser
**Goal:** Extract and categorize content from uploaded PDFs, Word docs, and spreadsheets into structured Google Sheets format
**Files to work on:**
- `/app/knowledge-base/page.tsx` — Upload interface
- `/actions/knowledge-base.ts` — Document processing server actions
- `/lib/parsers/` — Document parsing utilities
- `/components/dashboard/document-upload.tsx` — Upload component

### 2. Department-Specific Training Material Generator
**Goal:** Use AI to create customized training documents based on filtered knowledge base content and department roles
**Files to work on:**
- `/app/training/generate/page.tsx` — Training generation interface
- `/actions/training.ts` — AI training generation server actions
- `/lib/ai/training-generator.ts` — AI training logic
- `/components/dashboard/training-generator.tsx` — Generation UI

### 3. Automated SOP Template Creation System
**Goal:** Generate step-by-step procedures for new feature rollouts using predefined company formatting
**Files to work on:**
- `/app/sops/create/page.tsx` — SOP creation interface
- `/actions/sops.ts` — SOP generation server actions
- `/lib/templates/sop-templates.ts` — SOP template engine
- `/components/dashboard/sop-creator.tsx` — SOP creation UI

### 4. HubSpot CRM Integration
**Goal:** Automatically link generated training materials and SOPs to relevant company records, contacts, and deal stages
**Files to work on:**
- `/app/integrations/hubspot/page.tsx` — HubSpot settings
- `/lib/integrations/hubspot.ts` — HubSpot API client
- `/actions/integrations.ts` — CRM sync server actions
- `/components/integrations/hubspot-sync.tsx` — Sync UI

### 5. Advanced Slack Workflow Automation
**Goal:** Send contextual notifications with document previews, approval requests, and completion tracking
**Files to work on:**
- `/app/integrations/slack/page.tsx` — Slack settings
- `/lib/integrations/slack.ts` — Slack API client
- `/actions/notifications.ts` — Notification server actions
- `/components/integrations/slack-workflows.tsx` — Workflow UI

### 6. Smart Document Recommendation Engine
**Goal:** Suggest relevant SOPs and training materials based on CRM activity patterns and deal stages
**Files to work on:**
- `/app/recommendations/page.tsx` — Recommendations dashboard
- `/lib/ai/recommendation-engine.ts` — AI recommendation logic
- `/actions/recommendations.ts` — Recommendation server actions
- `/components/dashboard/recommendation-panel.tsx` — Recommendation UI

## ❌ Never Touch Without Explicit Instruction

1. **Environment files** (`.env*`) — These contain secrets
2. **Migration files** (`supabase/migrations/*`) — Can break database
3. **RLS policies** — Security-critical, needs review
4. **Authentication flow** — Already working, don't break
5. **Supabase configuration** — Core infrastructure

## 🎯 How to Work on This Project

### Before Every Session
1. **Read this file completely**
2. Check `TECHNICAL_DEBT.md` for known issues
3. Review the specific feature you're building
4. Understand which files need to be created/modified

### During Development
1. **Follow the folder structure exactly**
2. **Use TypeScript strictly** — no any types
3. **Keep server and client logic separate**
4. **Write tests for business logic**
5. **Update documentation as you go**

### Before Committing
1. **Run `npm run build`** — must pass without errors
2. **Run `npm run lint`** — fix all warnings
3. **Test the feature manually**
4. **Use conventional commit messages**
5. **Update `TECHNICAL_DEBT.md` if taking shortcuts**

### Commit Message Format

feat: add document parser for PDF extraction
fix: resolve HubSpot authentication timeout
docs: update integration setup guide
refactor: extract common validation logic
test: add training generator unit tests


### When Stuck
1. Check existing patterns in the codebase
2. Look at similar features for reference
3. Refer to integration documentation
4. Document the blocker in technical debt
5. Ask for specific guidance on the issue

## 🔧 Development Workflow

1. **Pick one v1 feature** from the list above
2. **Create a branch** with descriptive name
3. **Build incrementally** — small commits
4. **Test thoroughly** before moving to next feature
5. **Update documentation** as you build
6. **Mark technical debt** for any shortcuts

## 🎨 UI/UX Guidelines

- Use Shadcn/ui components consistently
- Follow dashboard-heavy design patterns
- Ensure responsive design (mobile-friendly)
- Maintain consistent spacing and typography
- Use proper loading states and error handling
- Follow accessibility best practices

## 📊 Performance Considerations

- Use Next.js Image component for all images
- Implement proper caching strategies
- Optimize database queries with proper indexing
- Use streaming for large document processing
- Implement rate limiting for AI API calls

---

**Remember:** This is a production-grade application. Write code that's maintainable, secure, and scalable. When in doubt, prefer explicit over clever, and maintainable over fast.