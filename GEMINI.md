# Discord Username Claimer - Project Instructions

This project is a high-performance Discord username "sniper" designed to monitor and claim specific usernames the moment they become available.

## Project Overview

- **Tech Stack:** Node.js (v16+ recommended), ESM, [CycleTLS](https://github.com/CycleTLS/CycleTLS).
- **Architecture:** 
  - **Entry Point:** `index.js` initializes the `CycleTLS` instance and manages the parallel monitoring loop.
  - **Utilities:** 
    - `utils/check.js`: Concurrent availability checking using `CycleTLS` with JA3 fingerprinting.
    - `utils/claim.js`: Immediate claim logic using `CycleTLS` with JA3 fingerprinting and proper TLS spoofing.
  - **Data:** `tokens.txt` (credentials), `usernames.txt` (targets), `config.json` (API metadata).

## Building and Running

### Installation
```bash
npm install
```

### Execution
```bash
npm start
```
*Note: The script uses `Promise.all` to check all targets simultaneously at every 5-second interval.*

## Development Conventions

- **Standard:** ES Modules (ESM) only.
- **Networking:** Use the centralized `cycleTLS` instance passed from `index.js` to utilities.
- **Security:** CycleTLS provides JA3 fingerprinting (spoofing a real Chrome browser) to bypass Discord's anti-bot detection.
- **Graceful Shutdown:** The process handles `SIGINT` to cleanly close the CycleTLS Go background process.

## Performance Optimizations

1. **Parallel Monitoring:** Every username listed in `usernames.txt` is checked simultaneously, eliminating sequential delay.
2. **CycleTLS + Go:** Request handling is offloaded to a high-speed Go-based TLS engine, reducing latency in the "check-to-claim" window.
3. **JA3 Spoofing:** Requests are significantly less likely to be flagged or rate-limited compared to standard Node.js HTTPS.

## Configuration Guide

- **`tokens.txt`**: Format is `TOKEN:PASSWORD` per line.
- **`usernames.txt`**: One username per line.
- **`config.json`**: Contains API URLs and telemetry metadata.

