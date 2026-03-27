# L.I.F.E | Smart Emergency Response

L.I.F.E is a real-time emergency coordination platform designed for the Hyderabad urban area. It connects patients, ambulance drivers, hospital staff, and blood banks to minimize response times and optimize resource allocation.

## Prerequisites

- **Node.js**: Version 18.17.0 or higher.
- **npm**: Version 9 or higher.
- **Firebase CLI**: Install globally via `npm install -g firebase-tools`.
- **Google Cloud Project**: With billing enabled (required for Gemini/Genkit models).

## Local Development Setup

1. **Clone the project** to your local machine.
2. **Install dependencies**:
   ```bash
   npm install
   ```
3. **Configure Environment Variables**:
   Create a `.env` file in the root directory and add your keys:
   ```env
   GEMINI_API_KEY=your_google_ai_api_key
   # Firebase config (found in your Firebase Console)
   NEXT_PUBLIC_FIREBASE_API_KEY=...
   NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=...
   NEXT_PUBLIC_FIREBASE_PROJECT_ID=...
   ```
4. **Run the Development Server**:
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:9002`.

5. **Start Genkit UI** (for AI flow testing):
   ```bash
   npm run genkit:dev
   ```

## Firebase Setup

1. **Create a Firebase Project** in the [Firebase Console](https://console.firebase.google.com/).
2. **Enable Services**:
   - **Authentication**: Enable Anonymous and Email/Password providers.
   - **Firestore**: Create a database in "Production" or "Test" mode.
3. **Initialize Firebase** locally:
   ```bash
   firebase login
   firebase init
   ```
   *Select Hosting, Firestore, and Emulators if needed.*

## Deployment

### 1. Web Deployment (Firebase Hosting)
Build the static site and deploy:
```bash
npm run build
firebase deploy
```

### 2. Android Deployment (Capacitor)
If you wish to build the Android app:
```bash
npm run static
npx cap add android
npx cap open android
```
*Requires Android Studio installed.*

## Architecture

This project uses:
- **Next.js 15 (App Router)**: For the web interface.
- **Firebase Authentication**: Anonymous and password-based login for roles.
- **Firebase Cloud Firestore**: For the real-time state machine.
- **Genkit**: AI flows for hospital and blood bank recommendations.
- **Shadcn UI**: For the component library.
- **Capacitor**: To wrap the web app as a native Android application.

## How to use the Demo

1. **Patient**: Go to `/dashboard/patient` and press the **SOS** button.
2. **Ambulance**: Open `/dashboard/ambulance` to accept the alert and navigate.
3. **Nurse**: Open `/dashboard/nurse` to prepare the ER.
4. **Blood Bank**: Open `/dashboard/blood-bank` to fulfill urgent requests.

Use the "Reset Active Emergency" button on the home page to clear the state.
