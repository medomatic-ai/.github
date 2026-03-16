# InjectaVox-native

## Overview

iPhone companion app for bedside injection documentation. Built with Expo 54 + React Native 0.81 + Clerk + Supabase.

## Repository

- **GitHub:** medomatic-ai/InjectaVox-native
- **Stack:** Expo 54 + React Native 0.81 + TypeScript + Clerk + Supabase
- **Package manager:** pnpm
- **Note:** Contains KeyStream as a subdirectory (keystream/)

## Commands

```bash
pnpm dev        # Start Expo dev server
pnpm build      # Build
pnpm test       # Run tests
eas build       # EAS cloud build for App Store
```

## Key Features

- Bedside injection documentation workflow
- QR-based pairing with KeyStream desktop bridge
- Clerk authentication (token handling, session management)
- Supabase data access (shared backend with web)
- EAS build pipeline for App Store distribution

## Architecture

- Expo Router for navigation
- Clerk for authentication (maps to Supabase users)
- WebSocket client connecting to KeyStream over TLS
- Expo secure storage for credentials

## Security Concerns

- Clerk token handling and session management
- Supabase anon key exposure (relies on RLS)
- WebSocket client TLS (certificate pinning to KeyStream)
- Expo secure storage for sensitive data
- Deep link handling security

## Anti-Patterns

- Never store credentials outside Expo secure storage
- Never skip TLS certificate validation with KeyStream
- Never use Supabase service role key in native app

## Integration Points

- **KeyStream:** WebSocket protocol (pair, inject, status, heartbeat commands)
- **Supabase:** Shared backend with InjectaVox-web (same DB, same RLS)
- **Clerk → Supabase:** Clerk users map to Supabase user records
