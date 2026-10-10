# Setup: real maps, accounts and shared reports

## A. Google Maps (required for real maps)
1. Open Google Cloud Console and create/select a project.
2. Enable billing and enable **Maps JavaScript API**, **Places API**, and **Directions API** (the API names/availability shown in your console may vary by account/Google's current Maps platform rollout).
3. Create a browser API key. Restrict it to `http://localhost:5173/*` for development, your deployed domain for production, and only the APIs you use. Do not use a server key in frontend code.
4. Copy `.env.example` to `.env`, then set `VITE_GOOGLE_MAPS_API_KEY=your_key`.
5. Restart the Vite server after changing `.env`.
6. Google Maps usage is metered and may cost money after applicable free monthly usage/credits. Check current Google Maps Platform pricing before publishing.

The map centers on Tirupati; the Tirumala button moves the same real map to the hill area. Google Places autocomplete returns actual matching place suggestions as the user types. Nearby service categories are searched live from Google Places.

## B. Firebase Authentication (free-tier friendly)
1. Create a Firebase project at Firebase Console.
2. Go to Authentication → Sign-in method → enable Email/Password.
3. In Project settings → General → Your apps, register a Web app and copy its config values into `.env`:
   - `VITE_FIREBASE_API_KEY`
   - `VITE_FIREBASE_AUTH_DOMAIN`
   - `VITE_FIREBASE_PROJECT_ID`
   - `VITE_FIREBASE_APP_ID`
4. Create a Realtime Database and copy its URL into `VITE_FIREBASE_DATABASE_URL`.
5. Restart `npm run dev`. Signup and sign-in then use Firebase Authentication (passwords are not stored by this app).

## C. Shared community hazard reports
The app writes reports to `publicHazards` in Firebase Realtime Database. Configure database rules before testing. For development, require an authenticated user for writes and allow appropriate reads; do not deploy open read/write rules. A production implementation should also validate report fields in trusted backend code, rate-limit submissions, and moderate abuse. The demo permits local session-only reports if Firebase is not configured.

Example policy direction (adapt to your app and validate it before use): require `auth != null` for writes; limit report text length and required fields; keep user identity private; and avoid storing precise live location unless needed and consented to. Firebase security rules are not a replacement for server-side abuse controls.

## D. Shared traffic and real-time congestion — important limitation
Google's traffic layer and traffic-aware route estimates are the real baseline here. This starter does **not** claim to calculate live citywide congestion from all app users. To add that feature responsibly, build a trusted backend that receives opt-in, short-lived, coarse location/speed samples, filters spoofed or stale samples, aggregates speeds by road segment and direction, and only labels congestion when sample confidence is adequate. Do not store continuous precise user tracks. Re-route only when an alternative route is meaningfully better, and avoid distracting users while driving.

MongoDB is not required for this starter. Firebase's free tier is the simpler option for authentication and small real-time reports. If you later need complex analytics or server-side traffic aggregation, a MongoDB Atlas free cluster can be considered, but it requires a backend API and its free-tier limits can change.

## E. Emergency behavior
The SOS button opens `tel:112`, India's emergency number. This app does not automatically contact police, share location with responders, or guarantee emergency response. Do not represent it as a dispatch system unless an authorized emergency integration exists.
