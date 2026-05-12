# Discord Username Sniper

A high-performance Discord username sniper designed to monitor and claim usernames the moment they become available.

## Optimizations
- **Parallel Monitoring:** Checks all usernames simultaneously using `Promise.all`.
- **CycleTLS Engine:** Uses a high-speed Go-powered TLS engine with browser-like JA3 fingerprinting to bypass anti-bot detection.
- **Graceful Shutdown:** Cleans up background processes automatically on exit.

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/your-friend-repo/discord-username-sniper.git
   cd discord-username-sniper
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

## Configuration

1. Edit `tokens.txt` (Format: `TOKEN:PASSWORD` per line).
2. Add target username(s) to `usernames.txt` (one per line).
3. Ensure `config.json` contains your API URLs and telemetry metadata.

## Usage

```bash
npm start
```

## Should I commit `package-lock.json`?
**Yes.** Committing `package-lock.json` is best practice for any Node.js project. It ensures that your friend (and anyone else who runs this) uses the exact same dependency versions as you. Without it, `npm install` might download newer versions of a library that could break your optimized code.
