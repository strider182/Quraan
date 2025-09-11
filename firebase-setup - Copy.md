# Firebase Setup Guide for Reading Coordination Project

## 1. Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Create a project"
3. Enter project name (e.g., "reading-coordination")
4. Disable Google Analytics (optional for this project)
5. Click "Create project"

## 2. Enable Firestore Database

1. In your Firebase project, go to "Firestore Database"
2. Click "Create database"
3. Choose "Start in test mode" (for development)
4. Select a location close to your users
5. Click "Done"

## 3. Get Firebase Configuration

1. Go to Project Settings (gear icon)
2. Scroll down to "Your apps"
3. Click "Web" icon (</>) to add a web app
4. Enter app nickname (e.g., "reading-coordination-web")
5. Don't check "Firebase Hosting" for now
6. Click "Register app"
7. Copy the firebaseConfig object

## 4. Update HTML File

Replace the firebaseConfig in `coordination.html` with your actual config:

```javascript
const firebaseConfig = {
  apiKey: "your-actual-api-key",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-actual-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef123456"
};
```

## 5. Security Rules (Optional - for production)

In Firestore Database > Rules, you can set up basic security:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Allow read/write access to the reading coordination project
    match /projects/reading-coordination {
      allow read, write: if true; // Change this for production security
    }
  }
}
```

## 6. Test the Application

1. Open `coordination.html` in a web browser
2. Try claiming a reading portion
3. Open the same page in another browser/tab to see real-time updates

## Features Added

- **Real-time synchronization**: Multiple users see updates instantly
- **Conflict prevention**: Warns if someone else claims a portion while you're selecting
- **Offline fallback**: Uses localStorage if Firebase is unavailable
- **Loading indicators**: Shows when data is being synced
- **Error handling**: Graceful fallbacks and user-friendly error messages

## Firestore Data Structure

The app stores data in a single document:
- Collection: `projects`
- Document: `reading-coordination`
- Fields:
  - `portions`: Array of 30 elements (null or {reader, date, done})
  - `readers`: Object mapping reader names to their assignments
  - `lastUpdated`: Timestamp for conflict detection

## Cost Considerations

Firebase free tier includes:
- 1 GiB storage
- 50,000 reads per day
- 20,000 writes per day
- 20,000 deletes per day

This should be more than sufficient for a reading coordination project with moderate usage.