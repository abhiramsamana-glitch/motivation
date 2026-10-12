# AI HealthMate: feature map and honest limitations

This project aims to combine symptom-information tools with a wider wellness dashboard. It is an educational student project, not a clinically validated medical product.

## Included in this source starter
- Email/password sign-up, sign-in, password reset, and protected pages through Firebase Authentication.
- Gemini-powered health information chat through the backend.
- Browser speech-to-text and text-to-speech where the browser supports them.
- Symptom information flow with basic emergency-keyword escalation and a non-diagnosis disclaimer.
- PDF/JPEG/PNG medical report explanation through Gemini; uploads are processed in memory and not saved as files by this starter.
- General nutrition and beginner-friendly fitness planning.
- BMI calculation without interpreting adult BMI categories for minors.
- Water, sleep, and activity entry persistence in Firestore, per authenticated user and date.
- User-scoped history entries with refresh and deletion.
- User profile API endpoints for preferences.
- English/Telugu language toggle for the core app interface and AI requests.

## Still needed for a stronger competition / production version
- Clinical expert review and validation of symptom pathways, safety, translations, and report interpretation.
- A vetted, maintained medical knowledge base with citations and update dates.
- A complete profile settings UI and consent/retention management UI.
- Weekly/monthly wellness trend charts, reminders that genuinely trigger, and export controls for stored data.
- Secure permanent report storage only if needed, with explicit consent, retention limits, and deletion.
- More comprehensive multilingual UI coverage and human review of Telugu medical terminology.
- End-to-end tests with a real Firebase project and Gemini API credentials.
- Security review, abuse testing, accessibility review, and privacy/legal review before public launch.

## Comparing with Ada Health fairly
Ada publicly describes a clinician-developed symptom assessment using probabilistic reasoning and a medical knowledge base, plus health information resources. This starter does not reproduce Ada's proprietary system, database, or clinical validation. It adds broader wellness modules, but more modules do not imply better clinical accuracy. Never advertise equivalent clinical accuracy or use unverified percentages.

## Safety rules
- Do not claim to diagnose, prescribe, or replace a clinician.
- Escalate possible emergency symptoms and do not delay urgent care.
- Do not tell users to start/stop medication or provide prescription dosing.
- Do not fabricate values from unreadable reports or fake medical history.
- For users under 18, avoid adult BMI categories and restrictive dieting advice.
- Keep Gemini secrets server-side and scope stored data to the authenticated user.
