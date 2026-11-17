# Biopharma Assessment — Frontend

React frontend for the Biopharma assessment API.

> **Implementation note:** This repository is a setup/documentation scaffold. The supplied materials contain Postman API collections, but no React source code, `package.json`, UI specification, or confirmed frontend build tool. Commands below describe a Vite-based React setup as a recommended baseline; align them with the actual implementation before submission.

## 1. Technology

- React
- JavaScript or TypeScript (choose one consistently)
- Vite (recommended development/build tool)
- Fetch or Axios for HTTP requests
- Vitest + React Testing Library (recommended test stack)

## 2. Prerequisites

- Node.js LTS and npm
- Git
- Backend API running and reachable
- API credentials supplied by the API owner

Check versions:

```bash
node --version
npm --version
git --version
```

## 3. Installation

Clone the private repository:

```bash
git clone https://github.com/<GITHUB_OWNER>/biopharma-frontend.git
cd biopharma-frontend
npm install
```

For a new Vite React app (only if source code has not yet been created):

```bash
npm create vite@latest . -- --template react
npm install
```

## 4. Environment configuration

Create a local `.env` file from the example:

```bash
cp .env.example .env
```

Set `VITE_API_BASE_URL` to the backend origin, for example `http://localhost:3000`.

Only public configuration belongs in a React environment file. **Never put `APP_KEY`, passwords, private API keys, database credentials, or GitHub access tokens in frontend variables**; Vite variables are bundled into browser code.

## 5. Development

```bash
npm run dev
```

Open the URL printed by Vite (normally `http://localhost:5173`).

## 6. Build

```bash
npm run build
```

Vite writes production assets to `dist/`. Preview the production build locally:

```bash
npm run preview
```

## 7. Tests and quality checks

Recommended scripts (must exist in `package.json` before running):

```bash
npm run test
npm run lint
```

Test coverage should include:
- Authentication form validation and error states.
- API client behavior for success, unauthorized, forbidden, validation, and server-error responses.
- Requests, trackers, and trackings list/detail views.
- Pagination, empty states, loading states, and network failures.
- Create/update/delete flows and confirmation handling.

## 8. API integration

The API reference is based on the supplied Postman collections:

- `API | Authentication`: login, logout, token refresh, authorization.
- `API | Feature`: requests, trackers, trackings, paging and lookup routes.

The Postman collections are stored in the backend repository under `docs/postman/`. Import them into Postman and configure the required variables in a local environment.

The collections refer to `BASE_URL`, `PATH_AUTHENTICATION` / `PATH_AUTH` / `PATH_FEATURE`, `APP_ID`, `APP_KEY`, and `token`. The exact deployed base URL and path-prefix values were not provided. Confirm these with the API owner.

## 9. Workflow

1. Create a feature branch from `main`.
2. Implement the UI and API integration.
3. Run tests and lint checks.
4. Run `npm run build`.
5. Review changes and open a pull request.
6. Merge only after review and passing checks.

Suggested branch names: `feature/<short-name>`, `fix/<short-name>`.

## 10. Deployment

Build with `npm run build`, then publish the `dist/` directory to the selected static hosting service. Configure the API base URL for the target environment and ensure backend CORS permits the frontend origin.

No hosting provider or deployment pipeline was specified, so deployment commands are intentionally provider-neutral.

## 11. Repository security

- Keep `.env` out of Git.
- Commit only `.env.example` with placeholder values.
- Do not expose server-side credentials in browser code.
- Give reviewers least-privilege access.
- Create a fine-grained GitHub token scoped only to this repository, with an expiry and minimum permissions. Share it through a secure channel, never in this README or a commit.
