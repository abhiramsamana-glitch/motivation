# AI HealthMate: GitHub + Vercel deployment

## 1. Push to GitHub
1. Extract this ZIP.
2. Create an empty repository on GitHub named `AI-HealthMate` (do not add a README if you plan to push this folder).
3. Open a terminal in the extracted `AI-HealthMate` folder and run:

```bash
git init
git add .
git status
git commit -m "Prepare AI HealthMate for deployment"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/AI-HealthMate.git
git push -u origin main
```

Replace `YOUR_USERNAME`. If the folder is already a Git repository, do not run `git init` or add a second remote. Review `git status` and ensure `.env` files and service-account JSON files are not staged.

## 2. Deploy the backend first
1. In Vercel, add a new project and import the GitHub repository.
2. Set **Root Directory** to `backend`.
3. Add these environment variables in Vercel Project Settings → Environment Variables:
   - `GEMINI_API_KEY` = your Gemini API key
   - `GEMINI_MODEL` = `gemini-2.5-flash`
   - `FIREBASE_SERVICE_ACCOUNT_JSON` = the full JSON contents of a Firebase service-account key (keep private; never commit it)
   - `CORS_ORIGIN` = your eventual frontend URL, e.g. `https://your-frontend.vercel.app`
   - `MAX_UPLOAD_SIZE_MB` = `10`
4. Deploy and test `https://YOUR-BACKEND-URL.vercel.app/api/health`. Expected JSON includes `"ok":true`.

In Firebase Console, enable the authentication sign-in method used by the app and create/enable Firestore. The service account must belong to the same Firebase project as the frontend configuration.

## 3. Deploy the frontend
1. Create a second Vercel project from the same GitHub repository.
2. Set **Root Directory** to `frontend`.
3. Add:
   - `VITE_API_BASE_URL` = `https://YOUR-BACKEND-URL.vercel.app/api`
   - `VITE_FIREBASE_API_KEY` = Firebase web app API key
   - `VITE_FIREBASE_AUTH_DOMAIN` = Firebase auth domain
   - `VITE_FIREBASE_PROJECT_ID` = Firebase project ID
   - `VITE_FIREBASE_APP_ID` = Firebase web app app ID
4. Deploy. Copy the frontend's exact URL into the backend's `CORS_ORIGIN` value and redeploy the backend.

## 4. Troubleshooting
- Check Vercel deployment build logs if either project fails to build.
- If API calls fail, confirm the frontend's `VITE_API_BASE_URL`, backend `CORS_ORIGIN`, and both deployments' environment variables; redeploy after changing variables.
- If Firebase requests fail, verify the web app config, service-account JSON, enabled Firebase Authentication provider, and Firestore setup.
- Test the backend health URL before debugging the AI assistant. A healthy API does not by itself prove Gemini or Firebase features work.

## Important
This archive is prepared for deployment, but you must complete configuration and test it in Vercel. A successful production build and live deployment have not been confirmed in this environment. Health guidance is educational and not a medical diagnosis or substitute for a clinician.
