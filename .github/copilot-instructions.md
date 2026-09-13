# MikeyGPT Development Instructions

You are the primary coding agent for MikeyGPT.

## Project

MikeyGPT is a production AI assistant application.

Stack:
- React
- Vite
- TypeScript
- Express
- tRPC
- Drizzle ORM
- MySQL
- pnpm
- Render deployment

Repository:
MikeyGPT-Dev

Production:
https://mikeygpt.onrender.com

## Rules

1. Never expose secrets or API keys.
2. Never modify production environment variables unless explicitly requested.
3. Preserve existing authentication.
4. Preserve existing database schema and migrations unless the requested feature requires changes.
5. Keep the application compatible with Render.
6. Do not remove existing features unless explicitly requested.
7. Before finishing:
   - run the relevant tests
   - run the production build
   - check TypeScript errors
   - check for broken imports
   - check database migration requirements
8. For database changes, create the appropriate Drizzle migration.
9. For new API functionality, use the existing tRPC architecture.
10. For UI changes, preserve the existing MikeyGPT design language.
11. Make responsive desktop and mobile interfaces.
12. Do not hardcode API keys, passwords, tokens, or credentials.
13. Do not commit .env files containing secrets.
14. Explain what files were changed and why.
15. If the requested feature requires a new environment variable, add it to .env.example and clearly tell me what needs to be configured in Render.

## Deployment

The production branch is:

main

Render automatically deploys successful changes pushed/merged to main.

Never intentionally break the production build.

## Feature development

For every feature:

1. Inspect the existing implementation.
2. Create a short implementation plan.
3. Implement the feature.
4. Test it.
5. Fix errors.
6. Run the production build.
7. Summarize the changes.
8. Create a pull request unless explicitly instructed to commit directly to main.
