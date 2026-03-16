# InjectaVox Ecosystem Overview

## What Is InjectaVox?

A clinical injection documentation system that streamlines how providers document injections directly into Epic EMR. Three components work together:

1. **InjectaVox-web** — Provider-facing PWA for template management and injection documentation
2. **InjectaVox-native** — iPhone companion app for bedside documentation
3. **KeyStream** — Desktop bridge that injects keystrokes into Epic EMR

## Architecture

```
iPhone (InjectaVox-native)
  ↕ WebSocket (TLS, self-signed certs)
KeyStream (Desktop Bridge, system tray)
  ↕ Keystroke injection (enigo)
Epic EMR (Desktop application)

InjectaVox-web (PWA)
  ↕ Supabase (PostgreSQL, Edge Functions, RLS)
Shared Backend
```

## Component Details

### InjectaVox-web (medomatic-ai/InjectaVox-web)
- **Stack:** Vite + React 19 + TypeScript 5 + Radix UI + Supabase
- **Purpose:** Provider-facing web app for injection documentation and template management
- **Key features:** CodeMirror template editing, Supabase edge functions, RLS policies
- **Build:** pnpm build / pnpm test / pnpm lint

### InjectaVox-native (medomatic-ai/InjectaVox-native)
- **Stack:** Expo 54 + React Native 0.81 + Clerk + Supabase
- **Purpose:** iPhone companion for bedside injection documentation
- **Key features:** QR pairing with KeyStream, EAS builds, Clerk auth
- **Build:** pnpm build / pnpm test / eas build

### KeyStream (medomatic-ai/InjectaVox-native/keystream/)
- **Stack:** Tauri 2 + Rust 2021 edition
- **Purpose:** System tray desktop bridge — message broker between iPhone and Epic
- **Key features:** WebSocket server (TLS), enigo keystroke injection, mDNS discovery
- **Build:** cargo build / cargo test (from keystream/src-tauri/)
- **Note:** Lives as a subdirectory inside InjectaVox-native, released via `keystream-v*` tags

## Cross-Component Integration Points

| Integration | Protocol | Key Concerns |
|-------------|----------|-------------|
| Native ↔ KeyStream | WebSocket (TLS) | Pairing QR, injection commands, heartbeat, reconnection |
| Native ↔ Web | Shared Supabase | Same DB, same RLS policies, consistent schemas |
| KeyStream ↔ Epic | Keystroke injection (enigo) | Field mapping, tab order, window verification |
| Auth | Clerk (native) + Supabase Auth (web) | Both map to same Supabase user records |

## Tech Stack

- **TypeScript 5** — web + native
- **Rust 2021** — KeyStream/Tauri
- **React 19** — web (Vite) + native (Expo/RN)
- **Supabase** — PostgreSQL, Edge Functions, RLS, Auth
- **Clerk** — native auth
- **Tauri 2** — desktop shell
- **Package managers:** pnpm (web + native), cargo (keystream)

## Dependency Graph

```
InjectaVox-native
  → KeyStream (WebSocket client → server)
  → Supabase (shared backend)

InjectaVox-web
  → Supabase (shared backend)

KeyStream
  → Epic EMR (keystroke injection)
```

## Deployment

- **Web:** Vercel or similar (PWA)
- **Native:** App Store via EAS
- **KeyStream:** Direct download (macOS/Windows), notarized
