# Thakarshi Fab Textile Inquiry

A single‑page website for textile product inquiries powered by Firebase Firestore.

## Features

- Responsive product grid with “Add to Inquiry” selection
- Contact form that stores submissions in Firestore
- Firebase Hosting ready (static site)

## Setup

1. **Create a Firebase project** (if you haven’t already) at https://console.firebase.google.com/
2. **Add a Web app** to the project and copy the config object (`apiKey`, `authDomain`, …).
3. Replace the placeholder values in `index.html`:

   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT_ID.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

4. (Optional) **Adjust Firestore rules** for testing:
   - Go to Firestore → Rules
   - Use:
     ```
     rules_version = '2';
     service cloud.firestore {
       match /databases/{database}/documents {
         match /inquiries/{doc} {
           allow read, write: if true; // ← testing only
         }
       }
     }
     ```
   - Remember to tighten rules before production.

5. **Install Firebase CLI** (if you don’t have it):
   ```bash
   npm install -g firebase-tools
   firebase login
   ```

6. **Initialize hosting** (run once inside this folder):
   ```bash
   firebase init hosting
   ```
   - Select your Firebase project
   - Public directory: `.` (press Enter)
   - Configure as a single‑page app? `N`
   - File `index.html` already exists? `Y`

7. **Deploy**:
   ```bash
   firebase deploy --only hosting
   ```

   Your site will be live at `https://<YOUR_PROJECT_ID>.web.app/`.

## Development

- Edit `index.html` directly; changes are reflected instantly when you reload.
- No build step required.

## License

Feel free to use and modify for your business.