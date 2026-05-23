# edge-optimize-router-3

A Cloudflare Worker that acts as an edge-side optimization router for the Tokowaka platform. It intercepts requests at the edge and routes them to the appropriate optimization services before serving responses to end users.

## Overview

This worker sits in front of origin servers and applies edge-level optimizations — including request routing, response transformation, and performance enhancements — without adding latency to the critical path.

## Prerequisites

- [Node.js](https://nodejs.org/) >= 20
- [Wrangler CLI](https://developers.cloudflare.com/workers/wrangler/) for local development and deployment

## Configuration

The worker is configured via `wrangler.toml`:

| Variable | Description |
|---|---|
| `EDGE_OPTIMIZE_TARGET_HOST` | The origin host to proxy and optimize requests for |

## Development

```bash
# Install dependencies
npm install

# Start local dev server
npx wrangler dev

# Deploy to Cloudflare Workers
npx wrangler deploy
```

## Releases

Releases are automated via [semantic-release](https://semantic-release.gitbook.io/semantic-release/). Every PR merged to `main` with a conventional commit triggers a new versioned GitHub Release and updates the `CHANGELOG.md`.

### Commit conventions

| Prefix | Release type |
|---|---|
| `feat:` | Minor release |
| `fix:` | Patch release |
| `chore:`, `docs:`, `style:` | No release |
| `BREAKING CHANGE` | Major release |

## License

Apache-2.0
