# CEO Executive Email Management Tool

An AI-powered knowledge base and training material generator that transforms company documents into department-specific SOPs and training materials.

## What this does

This tool takes your company's knowledge base documents and uses AI to generate customized training materials, SOPs, and documentation for different departments. It integrates with your existing CRM, communication tools, and automatically distributes materials to the right teams at the right time.

**Built for:** Internal teams and departments
**Template:** Dashboard-heavy interface for managing knowledge and training materials

## Tech Stack

- **Framework:** Next.js 15 with App Router
- **Database:** Supabase (PostgreSQL)
- **Language:** TypeScript
- **Styling:** Tailwind CSS
- **Deployment:** Vercel
- **Integrations:** HubSpot, Apollo, Twilio, ZoomInfo, GoHighLevel, Lemlist, Salesloft, Stripe, QuickBooks, Gmail, ChatGPT, Claude

## Prerequisites

- Node.js 18+
- npm or yarn
- Supabase CLI
- Git

## Local Setup

1. **Clone the repository**
   bash
   git clone <repository-url>
   cd ceo-executive-email-management-tool
   

2. **Install dependencies**
   bash
   npm install
   

3. **Set up environment variables**
   bash
   cp .env.example .env.local
   # Edit .env.local with your values
   

4. **Start Supabase locally**
   bash
   supabase start
   

5. **Run the development server**
   bash
   npm run dev
   

6. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000)

## Environment Variables

| Variable | Description | Required |
|----------|-------------|---------|
| `NEXT_PUBLIC_SUPABASE_URL` | Your Supabase project URL | Yes |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Your Supabase anonymous key | Yes |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase service role key for server operations | Yes |
| `HUBSPOT_CLIENT_ID` | HubSpot OAuth client ID | Yes |
| `HUBSPOT_CLIENT_SECRET` | HubSpot OAuth client secret | Yes |
| `APOLLO_API_KEY` | Apollo.io API key | Yes |
| `TWILIO_ACCOUNT_SID` | Twilio account SID | Yes |
| `TWILIO_AUTH_TOKEN` | Twilio authentication token | Yes |
| `ZOOMINFO_API_KEY` | ZoomInfo API key | Yes |
| `GOHIGHLEVEL_API_KEY` | GoHighLevel API key | Yes |
| `LEMLIST_API_KEY` | Lemlist API key | Yes |
| `SALESLOFT_API_KEY` | Salesloft API key | Yes |
| `STRIPE_SECRET_KEY` | Stripe secret key | Yes |
| `QUICKBOOKS_CLIENT_ID` | QuickBooks OAuth client ID | Yes |
| `QUICKBOOKS_CLIENT_SECRET` | QuickBooks OAuth client secret | Yes |
| `GOOGLE_CLIENT_ID` | Google OAuth client ID (for Gmail/Sheets) | Yes |
| `GOOGLE_CLIENT_SECRET` | Google OAuth client secret | Yes |
| `OPENAI_API_KEY` | OpenAI API key for ChatGPT | Yes |
| `ANTHROPIC_API_KEY` | Anthropic API key for Claude | Yes |
| `SLACK_BOT_TOKEN` | Slack bot token for notifications | Yes |
| `SLACK_SIGNING_SECRET` | Slack signing secret | Yes |

## Database Setup

1. **Apply migrations**
   bash
   supabase db reset
   

2. **Seed the database** (optional)
   bash
   npm run db:seed
   

## Deploy to Vercel

1. **Connect to Vercel**
   bash
   npm i -g vercel
   vercel
   

2. **Set environment variables**
   - Go to your Vercel dashboard
   - Navigate to Settings > Environment Variables
   - Add all required environment variables

3. **Deploy**
   bash
   vercel --prod
   

## Project Structure


├── app/                    # Next.js 15 app router
│   ├── (auth)/            # Authentication pages
│   ├── (dashboard)/       # Protected dashboard pages
│   └── api/               # API routes
├── components/            # React components
│   ├── ui/                # Reusable UI components
│   └── dashboard/         # Dashboard-specific components
├── lib/                   # Business logic and utilities
├── db/                    # Database access layer
├── actions/               # Server actions
├── types/                 # TypeScript type definitions
├── supabase/              # Supabase configuration and migrations
└── public/                # Static assets


## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint
- `npm run type-check` - Run TypeScript checks
- `npm run db:generate-types` - Generate TypeScript types from Supabase schema

## Contributing

1. Read `CLAUDE.md` for AI coding session guidelines
2. Follow conventional commit messages
3. Run `npm run build` before committing
4. Keep commits small and focused
5. Document any technical debt in `TECHNICAL_DEBT.md`