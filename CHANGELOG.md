# Changelog

## v2

### Changes

- **Cache key no longer tied to Yarn** — lockfile hash now covers all major package managers automatically (`yarn.lock`, `package-lock.json`, `npm-shrinkwrap.json`, `pnpm-lock.yaml`, `bun.lockb`, `bun.lock`); whichever is present gets hashed with no configuration required
- **Cache always saved per run** — primary key now uses `github.run_id` instead of source file hashes, ensuring `actions/cache` never skips the post-job save step
- **Improved restore-key fallback** — added a second restore-key (`nextjs-build-cache-${{ runner.os }}-`) so builds start warm even after a lockfile change rather than from cold

## v1

### Changes

- **Cache path broadened** — path glob updated from `.next/cache` to `**/.next/cache` to support monorepos and nested Next.js projects
