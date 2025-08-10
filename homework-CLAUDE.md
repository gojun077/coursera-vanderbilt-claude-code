Expense Tracker Web Application
===========================================

# Summary

Using `next.js` and `nextUI` we will build a complete web application
for tracking expenses that should render well on both desktop and mobile
browsers.

## Development Workflow

1. Before making any changes, create and checkout a feature branch named
   `feature-[brief-description]`
2. Write comprehensive tests for all new functionality
3. Compile code and run all tests before committing
   - use custom command `/test` to run all tests
4. Write detailed commit messages explaining the changes and rationale
5. In the `docs` folder, generate documentation for each new feature
   - use custom command `/document-feature` to generate docs
   - in `docs/dev/` generate developer documentation
   - in `docs/user/` generate user documentation
6. Commit all changes to the feature branch
7. Update `session_notes.md` with a summary of the new feature
   - use custom command `/session-end` to update `session_notes.md`
   - files created/modified during session
   - summarize completed work and pending items

## Architecture Overview

- **Frontend**: Next.js 15 with TypeScript and Tailwind CSS
- **State Management**: Zustand for client state, React Query for server
  state
- **Backend**: Node.js with Express and Prisma ORM
- **Database**: PostgreSQL
- **Testing**: Jest for unit tests, Playwright for E2E

## Code Standards

- Use TypeScript for all new code with strict type checking
- Use Prisma schema definitions for all database operations
- CSS classes should use Tailwind utilities; custom CSS only when necessary

## Quality Gates

- All code must compile without warnings
- Test coverage must remain above 80%
- All tests must pass before committing
- ESLint and Prettier must pass without errors

## File Organization

- Components: `/src/components/[feature]/[ComponentName].tsx`
- Pages: `/src/pages/[route].tsx`
- Utilities: `/src/lib/[category]/[utility].ts`
- Types: `/src/types/[domain].ts`


## Good UI Examples

- https://github.com/Tanq16/ExpenseOwl
- https://github.com/rarfell/dimeApp
