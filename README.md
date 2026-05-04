# LIAN Mobile Web

Static mobile web frontend for LIAN.

This repository contains only the frontend static app and local frontend rehearsal scripts. Backend APIs, runtime data, authentication, uploads, image proxy, and NodeBB integration live in the backend server repository.

## Frontend modes

This repo currently has two frontend entry modes during migration:

- Legacy static mobile frontend under `public/`, served by `npm run start:frontend-static`.
- Vue 3 + Vite + TypeScript shell from root `index.html`, served by `npm run dev`.

The Vue entry is the long-term UI architecture direction. Legacy pages remain active until each feature is migrated and validated.

## Install dependencies

```bash
npm install
```

The repository does not yet include a committed lockfile. After the first successful local install and build validation, commit `package-lock.json` so CI can switch from `npm install` to `npm ci`.

## Run Vue development server

```bash
npm run dev
```

Default Vite port: 5173.

## Build Vue entry

```bash
npm run build
```

This runs `vue-tsc --noEmit` and `vite build`.

## Run legacy frontend static rehearsal

Start the backend server separately, then run:

```bash
npm run start:frontend-static
```

Default ports:

```txt
frontend static rehearsal: 4300
backend API: 4200
image proxy: 4201
```

## Validate

```bash
npm run check
npm test
```

`npm run check` validates required project files and checks for encoding contamination.

`npm test` runs the legacy static smoke test against `http://127.0.0.1:4300`, so start `npm run start:frontend-static` first.
