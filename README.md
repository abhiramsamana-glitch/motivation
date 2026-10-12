# AI HealthMate

A full-stack educational health and wellness app starter: React + TypeScript + Vite frontend, Express + TypeScript backend, Gemini API, Firebase Authentication, and Cloud Firestore history.

## Included modules
- Email/password registration, sign-in, password reset, protected routes
- English/Telugu language toggle
- AI health-information chat with browser speech input/output where supported
- Cautious symptom information with emergency keyword escalation
- PDF/JPEG/PNG medical report explanation (in-memory processing; files are not permanently stored)
- General nutrition and activity planning
- BMI calculator without adult-category interpretation for teens
- Daily water, sleep, and activity logging with Firestore persistence through the backend
- User-specific saved AI history with delete support
- User-scoped profile API endpoints
- Input validation, rate limiting, security headers, server-side Gemini API key, and default-deny Firestore rules

## Important honesty note
This is a starter project, not a clinically validated medical device and not proven equivalent to Ada Health. AI output can be wrong. It must not be used to diagnose conditions, prescribe medication, or replace professional care. Some advanced production features (clinician-reviewed medical knowledge, clinical validation, full profile-management UI, long-term trend charts, and permanent file storage) require additional implementation and testing.

## Run locally (Node.js 20+)
1. Install dependencies from the project root: `npm install`
2. Copy `backend/.env.example` to `backend/.env` and configure `GEMINI_API_KEY`, `CORS_ORIGIN`, and Firebase Admin credentials securely.
3. Copy `frontend/.env.example` to `frontend/.env` and fill in your Firebase web app configuration and `VITE_API_BASE_URL=http://localhost:3001/api`.
4. Enable Firebase Authentication → Email/Password and create a Cloud Firestore database.
5. In one root terminal run `npm run dev` to start frontend and backend together.
6. Frontend: http://localhost:5173. Backend health check: http://localhost:3001/api/health.
7. Before deployment run `npm run build` and `npm test` and fix any errors.

If root workspace install is not supported in your environment, install each workspace separately with `cd frontend && npm install` and `cd backend && npm install`, then run their `npm run dev` commands in separate terminals.

## Environment variables
Backend (`backend/.env`):
- `PORT=3001`
- `GEMINI_API_KEY=...` (server secret; never put in frontend)
- `GEMINI_MODEL=gemini-2.5-flash` (use a model available to your account)
- `CORS_ORIGIN=http://localhost:5173`
- `MAX_UPLOAD_SIZE_MB=10`
- Firebase Admin Application Default Credentials / `GOOGLE_APPLICATION_CREDENTIALS` for local use. Do not commit service-account JSON.

Frontend (`frontend/.env`):
- `VITE_API_BASE_URL=http://localhost:3001/api`
- `VITE_FIREBASE_API_KEY=...`
- `VITE_FIREBASE_AUTH_DOMAIN=...`
- `VITE_FIREBASE_PROJECT_ID=...`
- `VITE_FIREBASE_APP_ID=...`

Firebase web config is intended for browser initialization; restrict the browser API key to the Firebase APIs you use. Never expose Gemini keys or Firebase Admin credentials in frontend variables.

## Google AI Studio
See `AI_STUDIO_PROMPT.md`. Current AI Studio Build documentation supports importing a repository from GitHub and provisioning Firebase Authentication/Firestore after the user enables the integration. The ZIP itself may not be directly importable into Build mode: extract it, push the project to GitHub, then use Build → Add files (+) → Import from GitHub, or paste the prompt into an existing AI Studio project. See the official guide: https://ai.google.dev/gemini-api/docs/aistudio-build-mode

## Deployment
The code is structured as separate frontend and backend workspaces. Deploying them separately is the straightforward route; configure the frontend API base URL, backend CORS origin, Gemini secret, and Firebase Admin identity for the actual hosting provider. This ZIP does not contain deployed credentials and has not been deployed for you.

## Medical privacy
Medical report uploads are sent to the configured AI backend for processing and are not stored as files by this starter. Saved summaries and daily wellness entries are stored under the signed-in user's own Firestore path. Review privacy, retention, and security settings before sharing the app with other people.
