# Quantix AI Academy

A free-first AI curriculum website for kids with:
- Student accounts
- Saved profile per account
- Saved lesson reflections
- Completed lesson tracking
- Audio lesson narration
- Copy-ready AI prompts
- Explorer and Builder learning tracks

## Files

Upload these files to your GitHub repository:

- `index.html`
- `README.md`

## Required setup before it works

This version uses Firebase for separate child accounts and saved progress.

### 1. Create a Firebase project

Go to Firebase Console and create a new project.

### 2. Enable Authentication

In Firebase:
- Go to Authentication
- Click Get Started
- Enable Email/Password sign-in

### 3. Enable Firestore Database

In Firebase:
- Go to Firestore Database
- Create database
- Start in test mode while setting up

### 4. Copy your Firebase config

In Firebase:
- Project Settings
- Your apps
- Web app
- Copy the firebaseConfig object

Replace this section inside `index.html`:

```js
const firebaseConfig = {
  apiKey: "PASTE_FIREBASE_API_KEY_HERE",
  authDomain: "PASTE_PROJECT_ID.firebaseapp.com",
  projectId: "PASTE_PROJECT_ID",
  storageBucket: "PASTE_PROJECT_ID.appspot.com",
  messagingSenderId: "PASTE_SENDER_ID",
  appId: "PASTE_APP_ID"
};
```

### 5. Firestore rules

Use these rules so each user can only access their own saved data:

```txt
rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

### 6. Publish with GitHub Pages

In GitHub:
- Open your repository
- Go to Settings
- Pages
- Source: Deploy from branch
- Branch: main
- Folder: /root
- Save

Your site will publish as a GitHub Pages link.

## Notes

This website does not connect to paid AI APIs. It uses external free AI tools through prompt-copying and links.
