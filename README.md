# RouteGuard Premium — Tirupati & Tirumala

A React + Vite navigation UI starter with Google Maps, live Places autocomplete, route alternatives, traffic layer, nearby essentials, optional Firebase email/password authentication, and community hazard reports.

## What is real and what needs configuration?
- Google Maps, place autocomplete, route calculation, traffic overlay and nearby service search work only after configuring a Google Maps API key and enabling the required APIs/billing in Google Cloud.
- Email/password signup and login work only after configuring Firebase Authentication.
- Cross-user community hazard reports work only after configuring Firebase Realtime Database and its security rules.
- Without configuration, the premium login screen and demo dashboard are available, but live map/auth/shared data are not simulated as real.
- The SOS control opens the phone's emergency dialer for 112; it does not automatically dispatch emergency services or send your location.
- The Google Maps browser Directions API does not provide a dedicated motorcycle mode in this implementation; Bike is currently an explicitly disclosed driving-route approximation. Bus/transit availability depends on Google route coverage.

## Start locally
1. Install Node.js 20+.
2. Extract this folder and open it in VS Code.
3. In a terminal in this folder, run `npm install`.
4. Copy `.env.example` to `.env`.
5. Configure Google Maps and/or Firebase using `SETUP.md`.
6. Run `npm run dev` and open the localhost URL shown by Vite.

## Security
- Never commit `.env` or private service-account credentials.
- A Maps browser key is visible to users by design: restrict it by HTTP referrer and API.
- Configure Firebase Authentication and database rules before public deployment. Do not use public write access for production.
- Before launch, add abuse protection, report moderation, privacy/retention policy, and rate limits.
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/2a70010a-ec49-4cad-a792-4296d542e48b" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/cbb3c3f3-31c9-4218-819c-274af982cea8" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/c52446a0-2f3b-4bee-a7dc-b0eb52194795" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/bf608336-1ea6-4265-ad7b-160b7ffb93d0" />
