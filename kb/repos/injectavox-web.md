# InjectaVox-web

## Overview

Provider-facing PWA for injection documentation and template management. Built with Vite + React 19 + TypeScript + Radix UI + Supabase.

## Repository

- **GitHub:** medomatic-ai/InjectaVox-web
- **Stack:** Vite + React 19 + TypeScript 5 + Radix UI + Supabase
- **Package manager:** pnpm

## Commands

```bash
pnpm dev        # Development server
pnpm build      # Production build
pnpm test       # Run tests (Vitest)
pnpm lint       # ESLint
```

## Key Features

- CodeMirror-based template editing for injection documentation
- Supabase backend (PostgreSQL, Edge Functions, RLS)
- Supabase Auth for web authentication
- Radix UI component library

## Architecture

- Functional React components with hooks
- Zustand for state management
- Supabase JS SDK for data access (never raw SQL in client)
- Edge functions for server-side logic

## Security Concerns

- Supabase RLS policies must be airtight (shared with native)
- Edge function auth uses service role key (never expose to client)
- CSP headers and XSS prevention
- Input sanitization for template content

## Anti-Patterns

- Never use raw SQL in client code — use generated Supabase types
- Never expose service role key to the browser
- Never bypass RLS policies

## Integration Points

- Shared Supabase backend with InjectaVox-native
- Same RLS policies must work for both web and native auth methods
- Edge functions may serve both web and native clients
