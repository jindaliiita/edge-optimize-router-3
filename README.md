# edge-optimize-router-3

A Cloudflare Worker that acts as an edge-side optimization router for the Tokowaka platform. It intercepts requests at the edge and routes them to the appropriate optimization services before serving responses to end users.

## Overview

This worker sits in front of origin servers and applies edge-level optimizations — including request routing, response transformation, and performance enhancements — without adding latency to the critical path.

## Prerequisites

- [Node.js](https://nodejs.org/) >= 20
- [Wrangler CLI](https://developers.cloudflare.com/workers/wrangler/) for local development and deployment
- A Cloudflare account with Workers enabled

## Configuration

The worker is configured via `wrangler.toml`:

| Variable | Description |
|---|---|
| `EDGE_OPTIMIZE_TARGET_HOST` | The origin host to proxy and optimize requests for |

### Environments

| Environment | Worker Name | Purpose |
|---|---|---|
| `dev` | `edge-optimize-router-3-dev` | Development testing |
| `staging` | `edge-optimize-router-3-staging` | Pre-production validation |
| production | `edge-optimize-router-3` | Live traffic |

## Development

```bash
# Install dependencies
npm install

# Start local dev server
npx wrangler dev

# Deploy to specific environment
npx wrangler deploy --env dev
npx wrangler deploy --env staging
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

## Contributing

All changes must go through a pull request. Direct pushes to `main` are not allowed.

## License

Apache-2.0
