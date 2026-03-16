# KeyStream

## Overview

Desktop bridge application — system tray app that brokers messages between the iPhone app and Epic EMR via keystroke injection. Built with Tauri 2 + Rust.

## Repository

- **Location:** medomatic-ai/InjectaVox-native/keystream/
- **Stack:** Tauri 2 + Rust 2021 edition
- **Build tool:** cargo
- **Release:** Git tags (keystream-v*)

## Commands

```bash
cd keystream/src-tauri
cargo build       # Build
cargo test        # Run tests
cargo build --release  # Release build
```

## Key Dependencies

- **tokio** — async runtime
- **tokio-tungstenite** — WebSocket server
- **tokio-rustls / rustls** — TLS
- **rcgen** — self-signed certificate generation
- **enigo** — OS-level keystroke injection
- **tauri 2** — desktop app shell, system tray

## Architecture

- System tray application (no main window)
- WebSocket server accepting connections from InjectaVox-native
- TLS with self-signed certificates (trust established via QR code)
- mDNS for LAN discovery
- enigo for keystroke injection into Epic EMR windows

## Pairing Flow

1. KeyStream generates self-signed TLS certificate (rcgen)
2. Certificate fingerprint encoded in QR code displayed on screen
3. iPhone scans QR → gets IP + port + cert fingerprint
4. WebSocket connection established with certificate pinning
5. Persistent connection maintained with heartbeat

## WebSocket Protocol

- **Message format:** JSON over TLS WebSocket
- **Commands:** pair, inject, status, heartbeat
- **Reconnection:** automatic with exponential backoff

## Keystroke Injection

- Uses enigo for OS-level input simulation
- Must verify target window is Epic EMR before injecting
- Field mapping: which injection data → which Epic field
- Tab/navigation sequences for Epic's field order
- Timing delays to account for Epic responsiveness

## Security Concerns (HIGHEST RISK COMPONENT)

- TLS certificate generation and validation
- WebSocket server must only accept pinned connections
- Keystroke injection MUST only target verified Epic windows
- QR-based trust model (one-time codes)
- Tauri capability permissions (macOS entitlements)
- Code signing (Apple notarization, Windows signing)

## Anti-Patterns

- Never inject keystrokes without verifying target window
- Never skip TLS — all WebSocket connections must be encrypted
- Never block the tokio event loop (all I/O must be async)
- Never accept WebSocket connections without certificate verification
