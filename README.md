# dashy-dist

Compiled Windows release artifacts and the auto-update manifest for
[**dashy**](https://github.com/jordanderpdeederr/dashy) — a local-first
dashboard for markdown folders.

**This repo contains build artifacts only. No source code lives here.** It is
public so that installed copies of dashy can check for and download updates
with no login or token.

## Contents

- **Releases** — each tagged `vX.Y.Z` release attaches the installer
  `dashy-setup-X.Y.Z.exe`.
- **`latest.json`** — the update manifest the app polls. Shape:

  ```json
  {
    "version": "0.1.0",
    "url": "https://github.com/jordanderpdeederr/dashy-dist/releases/download/v0.1.0/dashy-setup-0.1.0.exe",
    "sha256": "<hex>",
    "notes": ""
  }
  ```

The app verifies each download's SHA-256 against this manifest before running
it, and only trusts installer URLs served from this repository.

## How releases get here

Automatically. Pushing a `vX.Y.Z` tag on the private source repo triggers a
Windows CI build that publishes the release and updates `latest.json` here. See
`packaging/windows/BUILD.md` in the source repo for the full pipeline.
