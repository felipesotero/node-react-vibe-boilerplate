# AGENTS.md

## Mission
You are operating in a production-oriented Node.js + React monorepo with AI-assisted development.
Prioritize maintainability, testability, and clean architecture over speed hacks.

## Architecture Rules
- Respect layers: `domain`, `application`, `infrastructure`, `interface`.
- Keep business logic out of controllers, routes, and UI.
- Side effects must be isolated behind adapters/services.
- Dependencies must point inward.
- Prefer composition over inheritance.
- Avoid premature abstractions.

## Engineering Standards
- Apply KISS and DRY pragmatically.
- Make small, focused changes.
- Do not invent scope not requested by task.
- Keep code readable without excessive comments.

## Monorepo + Dependency Hygiene
- Use `pnpm` as the package manager.
- Respect workspace boundaries.
- Do not rely on transitive dependencies.
- Declare dependencies at the correct package level.

## Git and PR Discipline
- No direct commit to `main`/`develop`.
- Branch patterns:
  - `epic/*`
  - `feature/*`
  - `fix/*`
  - `chore/*`
  - `refactor/*`
  - `docs/*`
- PR must have a single clear objective and match diff reality.

## Testing Guidance
- Prioritize tests for critical flows.
- Prefer meaningful unit/integration tests over inflated coverage goals.
- E2E should cover top user journeys in a dedicated suite.
