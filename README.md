# AlgoBridge UI

A modern Next.js web application for discovering, managing, and composing algorithmic trading strategies. AlgoBridge enables traders to explore a curated collection of strategies, receive email notifications, and save their favorite trading strategies.

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Development](#development)
- [Building for Production](#building-for-production)
- [Environment Variables](#environment-variables)
- [Contributing](#contributing)
- [License](#license)

## Features

- Browse and search algorithmic trading strategies
- View detailed strategy information and performance metrics
- User authentication via Clerk
- Save favorite strategies to personal collection
- Email notification system for strategy updates
- Create and compose custom trading strategies
- Responsive design with dark theme support
- Real-time data table with pagination
- Strategy search with filtering capabilities
- User profile management

## Tech Stack

- **Framework**: Next.js 15.5.9 with App Router
- **UI Libraries**: React 19.1.0, Radix UI, shadcn/ui
- **Styling**: Tailwind CSS 4
- **Form Handling**: React Hook Form with Zod validation
- **Data Management**: TanStack React Query 5.89.0, TanStack React Table 8.21.3
- **Authentication**: Clerk NextAuth
- **HTTP Client**: Axios
- **Theme**: Next Themes
- **Icons**: Tabler Icons, Lucide React
- **Visualization**: Mermaid diagrams, Viewer.js
- **Notifications**: Sonner toast notifications
- **Analytics**: Vercel Analytics
- **Linting**: ESLint

## Prerequisites

Before you begin, ensure you have the following installed:

- Node.js 20.x or higher
- npm or pnpm package manager
- Clerk account for authentication
- Environment variables configured (see [Configuration](#configuration))

## Installation

1. Clone the repository:

```bash
git clone https://github.com/TueeNguyen/algobridge-ui.git
cd algobridge-ui
```

2. Install dependencies using pnpm (recommended) or npm:

```bash
pnpm install
```

or

```bash
npm install
```

## Getting Started

1. Set up your environment variables (see [Environment Variables](#environment-variables) section)

2. Start the development server:

```bash
pnpm run dev
```

or

```bash
npm run dev
```

The application will be available at `http://localhost:3000`

## Project Structure

```
src/
├── app/                          # Next.js App Router
│   ├── api/                      # API routes
│   │   └── external/             # External service proxies
│   ├── (home)/                   # Landing page route
│   ├── providers/                # React providers
│   ├── saved/                    # Saved strategies page
│   ├── strategies/               # Strategies listing and details
│   │   └── [id]/                 # Individual strategy page
│   ├── types/                    # API and domain types
│   └── layout.tsx                # Root layout
├── components/                   # React components
│   ├── ui/                       # Base UI components (shadcn/ui)
│   │   └── app/                  # Application-specific components
│   ├── landingPageUi/            # Landing page components
│   ├── layouts/                  # Layout components
│   └── SignInOrOutButton.tsx     # Authentication button
├── contexts/                     # React contexts
│   └── SearchContext.tsx         # Search state management
├── hooks/                        # Custom React hooks
│   ├── useCreateStrategy.tsx     # Strategy creation hook
│   └── useGetSavedStrategies.tsx # Saved strategies hook
├── lib/                          # Utility functions and configs
│   ├── axios.ts                  # Axios client configuration
│   ├── utils.ts                  # Helper functions
│   ├── getRegisteredEmailStrategyList.ts
│   └── registerDailyEmail.ts
└── middleware.ts                 # Next.js middleware
```

## Configuration

### Clerk Authentication Setup

1. Create a Clerk account at https://clerk.com
2. Set up a new application in Clerk dashboard
3. Add your Clerk keys to environment variables

### Ngrok for Webhook Development

For local development with Clerk webhooks:

1. Install ngrok: `npm install -g ngrok`
2. Get auth token from https://dashboard.ngrok.com/get-started/your-authtoken
3. Configure ngrok: `ngrok config add-authtoken YOUR_AUTH_TOKEN_HERE`
4. Start ngrok tunnel: `ngrok http 3000`
5. Update your Clerk webhook URL with the ngrok URL

## Environment Variables

Create a `.env.local` file in the root directory with the following variables:

```
# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

# Application URLs
NEXT_PUBLIC_BASE_URL=http://localhost:3000

# API Configuration
NEXT_PUBLIC_API_BASE_URL=your_api_base_url
```

Replace the placeholder values with your actual configuration.

## Development

### Running the Development Server

```bash
pnpm run dev
```

The development server runs with Turbopack for faster builds and Hot Module Replacement (HMR).

### Running Linter

```bash
pnpm run lint
```

### Code Standards

- TypeScript for type safety
- ESLint for code consistency
- Tailwind CSS for styling
- Shadcn/ui component library

## Building for Production

Build the application for production:

```bash
pnpm run build
```

Start the production server:

```bash
pnpm run start
```

The production build includes optimizations for performance and bundle size.

## Key Features Explained

### Strategy Search and Discovery

Users can search for trading strategies by name and view them in a paginated table. The search functionality is powered by server-side rendering for optimal performance.

### Authentication Flow

Clerk provides seamless authentication. Users can sign in to access exclusive features like saving strategies and receiving email notifications.

### Email Notifications

Authenticated users can register for daily email notifications about their favorite strategies. This feature integrates with the backend email service.

### Strategy Composition

Users can create custom strategies using the strategy composer. The interface provides an intuitive way to build and validate trading logic.

### Saved Strategies

Users can save strategies to their personal collection for quick access. Saved strategies are stored and can be managed through the saved strategies page.

## Troubleshooting

### Port Already in Use

If port 3000 is already in use, specify a different port:

```bash
pnpm run dev -- -p 3001
```

### Module Not Found Errors

Ensure all dependencies are installed:

```bash
pnpm install
```

Clear cache and rebuild:

```bash
pnpm run build
```

### Environment Variables Not Loading

Verify that your `.env.local` file is in the root directory and has the correct format. Restart the development server after making changes.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For issues, feature requests, or questions, please open an issue on the GitHub repository.
