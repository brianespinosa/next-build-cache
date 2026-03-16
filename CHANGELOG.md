# Changelog

## v3

### Changes

- **Upgraded `actions/cache` to v5** — resolves Node.js 20 deprecation warnings ahead of the GitHub Actions runner migration to Node.js 24 (June 2, 2026)
- **Added Dependabot config** — weekly automated updates for GitHub Actions dependencies with `chore:` conventional commit prefix and auto-rebase enabled

## v2

### Changes

- **Cache key no longer tied to Yarn** — lockfile hash now covers all major package managers automatically (`yarn.lock`, `package-lock.json`, `npm-shrinkwrap.json`, `pnpm-lock.yaml`, `bun.lockb`, `bun.lock`); whichever is present gets hashed with no configuration required
- **Cache always saved per run** — primary key now uses `github.run_id` instead of source file hashes, ensuring `actions/cache` never skips the post-job save step
- **Improved restore-key fallback** — added a second restore-key (`nextjs-build-cache-${{ runner.os }}-`) so builds start warm even after a lockfile change rather than from cold

## v1

### Changes

- **Cache path broadened** — path glob updated from `.next/cache` to `**/.next/cache` to support monorepos and nested Next.js projects
