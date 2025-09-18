# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is `@onhive.io/astro-loader`, an Astro Content Layer loader package for the Hive blockchain. It provides TypeScript loaders that allow Astro projects to fetch and integrate Hive blockchain content (blog posts and account data) through Astro's Content Layer API.

The package exports two main loaders:

- `hiveBlogLoader(author)` - Fetches blog posts from a specific Hive account
- `hiveAccountsLoader(usernames)` - Fetches account information from one or more Hive accounts

## Architecture

The codebase follows a layered architecture:

```
src/
├── index.ts              # Main entry point, exports public API
├── loaders/              # Astro loader implementations
│   ├── blogLoader.ts     # Blog posts loader
│   └── accountsLoader.ts # Account information loader
├── api/                  # Hive blockchain API clients
│   ├── common.ts         # Shared Hive client configuration
│   ├── posts.ts          # Posts API calls
│   └── accounts.ts       # Accounts API calls
├── adapters/             # Data transformation layer
│   ├── posts.ts          # Transforms Hive posts to package schema
│   └── accounts.ts       # Transforms Hive accounts to package schema
├── schema/               # TypeScript types and Zod schemas
│   ├── posts.ts          # Post type definitions
│   ├── accounts.ts       # Account type definitions
│   ├── communities.ts    # Community type definitions
│   └── utils.ts          # Schema utilities
└── tests/                # Test files mirroring source structure
```

### Data Flow

1. Loaders call API functions to fetch raw data from Hive blockchain
2. API functions use `@hiveio/dhive` client to connect to multiple Hive nodes
3. Adapters transform raw Hive data into the package's TypeScript schema
4. Loaders store transformed data in Astro's content store

## Development Commands

### Build and Development

```bash
# Build the package for distribution
bun run build

# Watch mode for development (rebuilds on file changes)
bun run dev

# Install dependencies
bun install
```

### Code Quality

```bash
# Lint and fix code issues
bun run lint

# Format code with Prettier
bun run pretty

# Both linting and formatting are run automatically on git commit via husky
```

### Testing

```bash
# Run all tests
bun test

# Run tests with coverage (configured to require 90% coverage)
bun test --coverage

# Run specific test file
bun test src/tests/adapters/posts.test.ts
```

### Pre-commit Hooks

The project uses Husky with lint-staged to automatically run linting and formatting on staged files before commits. This is set up automatically with:

```bash
bun run prepare
```

## Build Configuration

- **TypeScript**: Uses Astro's strict TypeScript configuration with path aliases (`~/*` maps to `src/*`)
- **Bundling**: tsup with ESM output, TypeScript declarations, and source maps
- **Package Manager**: Bun (lockfile: `bun.lockb`)
- **Output**: Single ESM module at `dist/index.mjs` with TypeScript declarations

## Key Dependencies

- `@hiveio/dhive`: Hive blockchain JavaScript client
- `astro`: Peer dependency for Astro Content Layer API
- Development tools: ESLint, Prettier, TypeScript, tsup, Husky

## Testing Strategy

Tests use Bun's built-in test runner and are organized to mirror the source structure. The project includes:

- Unit tests for adapters (data transformation)
- API integration tests
- Mock data generators for consistent testing
- 90% code coverage requirement

## Package Distribution

The package is published as an ESM-only module to NPM under the `@onhive.io` scope with public access. The build outputs:

- `dist/index.mjs` - Main ESM bundle
- `dist/index.d.mts` - TypeScript declarations
- Source maps for debugging

## Hive API Integration

The package connects to multiple Hive API nodes for reliability:

- api.hive.blog (primary)
- api.hivekings.com
- anyx.io
- api.openhive.network

API calls use the Hivemind API for fetching posts and account data, with automatic failover between nodes.
