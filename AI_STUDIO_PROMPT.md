# Google AI Studio Build prompt for AI HealthMate

Use this prompt in Google AI Studio Build after importing this repository (Build mode → Add files (+) → Import from GitHub), or paste it into the chat of the AI Studio project you already generated. Keep the project name **AI HealthMate**.

---

Inspect the entire existing AI HealthMate codebase before editing. Do not replace the project with a new mockup. Preserve working features and make the existing code compile and run in Google AI Studio's full-stack web environment.

1. Run available checks and fix real TypeScript, dependency, runtime, and routing errors. Do not claim a test passed unless you ran it.
2. Adapt the current frontend and API to the AI Studio full-stack runtime. Ensure API requests use the correct same-origin server routes or a configured API base URL. Do not leave localhost URLs in the deployed build.
3. Connect Gemini calls through server-side code only. Use AI Studio's Secrets panel for `GEMINI_API_KEY`; never expose it to browser code or a `VITE_` variable.
4. Use the Google AI Studio Firebase integration to provision Firebase Authentication and Cloud Firestore. When prompted, click **Enable Firebase** and select a project and database location carefully. Do not claim Firebase is connected until the integration is enabled and a test record can be saved and read.
5. Support secure authentication, user-owned history, persistent daily wellness records, profile preferences, symptom assessment, report explanation, English/Telugu assistant, and general nutrition/fitness planning. Add missing UI screens and connect every control to real functionality.
6. Review and test Firebase Security Rules. Use owner-scoped access, authentication checks, input validation, safe upload limits, and deletion controls. Never expose service-account credentials.
7. For symptom assessment, show uncertainty, do not diagnose or prescribe, and provide urgent-care guidance for possible emergencies. Do not claim clinical equivalence to Ada Health or a validated medical accuracy rate.
8. For reports, never invent unreadable values; explain that AI can make mistakes and users should review results with a clinician. Do not store uploaded files permanently without explicit user consent and secure storage.
9. Keep all features mobile-responsive and accessible. Keep Telugu and English labels and responses. Voice input/output should fail gracefully when the browser does not support it.
10. Add tests for core utilities, auth failures, user ownership, API errors, wellness persistence, and upload validation. Fix the issues found. If a test cannot run because a credential or service is unavailable, state that explicitly and provide the exact setup step.
11. Provide a short setup checklist listing the actual files changed, required secrets, Firebase services enabled, tests run and their results, and any remaining limitations.

Do not fabricate sample medical history, database success, API responses, or deployment status. Build a functioning educational health-and-wellness app, not a static demo. AI HealthMate is not a medical device and does not replace professional care.
