# MikeyGPT external deployment

## Target

- App: `https://mikeygpt.ai`
- Host: Render Web Service
- Database: managed MySQL-compatible database
- Auth: Google OAuth
- AI: OpenAI server-side streaming

## Render

Build command:

```bash
corepack enable && pnpm install --frozen-lockfile && pnpm build
```

Start command:

```bash
pnpm start
```

Health check:

```text
/api/health
```

Render supplies `PORT`; the production server binds to `0.0.0.0` and uses that port.

## Required environment variables

Copy `.env.render.example` into Render's Environment settings and replace every placeholder. Never commit real secrets.

## Google OAuth

Add this authorized redirect URI in Google Cloud:

```text
https://mikeygpt.ai/api/auth/google/callback
```

For local development also add:

```text
http://localhost:3000/api/auth/google/callback
```

## Database

Run the initial schema migration once from a trusted machine or Render Shell:

```bash
pnpm install --frozen-lockfile
pnpm db:generate
pnpm db:migrate
```

Do not run `db:generate` on every deployment.

## Domain

Add `mikeygpt.ai` to the Render service under Settings > Custom Domains. Render will provide the DNS target and automatically provision HTTPS after DNS verification.

## Remaining Manus-dependent features

The first external release covers the core chat, Google auth, MySQL persistence, admin controls, and OpenAI/Anthropic text streaming. Image generation, voice transcription, S3/file storage, Maps, and heartbeat/media services still require their separate external-provider migrations.
