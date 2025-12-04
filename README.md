# 👥 My Friends

An aesthetic, interactive web app to share memories and photos of your friends with Firebase cloud storage and Firestore real-time database integration.

## Features

- ✨ **Beautiful UI** with gradient background and glassmorphism cards
- 📸 **Photo & Memory Upload** — add multiple photos per friend
- 🔐 **Private Entries** — protect friends with access codes (hashed)
- ☁️ **Cloud Storage** — photos stored in Firebase Storage, data in Firestore
- 💾 **Fallback Storage** — uses localStorage if Firebase is unavailable
- 🎨 **Responsive Design** — works on desktop and mobile

## Quick Start

1. Open `friends.html` in a web browser
2. Click "➕ Add Friend" to add a new friend
3. Upload photos and add memories
4. Mark entries as private with an access code
5. Share the link with friends!

## Firebase Setup

To enable cloud features:

1. Create a Firebase project at [firebase.google.com](https://firebase.google.com)
2. Enable Firestore Database and Cloud Storage
3. Copy your Firebase web config
4. Paste the config into `friends.html` (search for `firebaseConfig`)

**Note:** The app currently uses permissive Firebase rules for testing. For production, secure your rules:

```
Firestore:
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /friends/{document=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}

Storage:
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /photos/{allPaths=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```

## File Structure

```
Random/
├── friends.html          # Main app (HTML + CSS + JS, single file)
├── README.md             # This file
└── .gitignore            # Git ignore rules
```

## Technologies

- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **Database:** Firebase Firestore
- **Storage:** Firebase Cloud Storage
- **Auth:** Firebase (optional for production)

## License

Made with ❤️ by Dylan | 2025
