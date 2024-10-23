# LooFinder-App
# LooFinder App: Firebase Integration

LooFinder is an app that helps users locate public washrooms and submit reviews and ratings. It is built with **React Native** for the frontend and **Node.js (Express)** for the backend. Firebase is used as the database to store user reviews and ratings.

## Table of Contents

- [Project Overview](#project-overview)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Clone the Repo](#clone-the-repo)
- [Firebase Setup](#firebase-setup)
  - [Step 1: Create Firebase Project](#step-1-create-firebase-project)
  - [Step 2: Enable Realtime Database](#step-2-enable-realtime-database)
  - [Step 3: Set Up Firebase Admin SDK for Backend](#step-3-set-up-firebase-admin-sdk-for-backend)
  - [Step 4: Firebase Web SDK for React Native (Frontend)](#step-4-firebase-web-sdk-for-react-native-frontend)
- [Backend Integration](#backend-integration)
  - [Install Dependencies](#install-dependencies)
  - [Set Up Firebase Admin SDK](#set-up-firebase-admin-sdk)
  - [Create API Endpoints](#create-api-endpoints)
- [Frontend Integration](#frontend-integration)
  - [Install Dependencies](#install-dependencies-frontend)
  - [Firebase Web SDK Configuration](#firebase-web-sdk-configuration)
  - [Submit and Display Reviews](#submit-and-display-reviews)
- [Running the App](#running-the-app)
- [Deploying the Backend on Glitch](#deploying-the-backend-on-glitch)

---

## Project Overview

The LooFinder app allows users to:
- Find nearby public washrooms using Google Maps.
- Submit reviews and ratings for washrooms.
- View other users' reviews and ratings for washrooms.

The app uses Firebase to store the review and rating data in real-time, ensuring that data persists even after app refreshes.

---

## Technologies Used

- **Frontend**: React Native (Expo), Google Maps API
- **Backend**: Node.js (Express) hosted on Glitch
- **Database**: Firebase Realtime Database
- **Firebase SDK**: Firebase Admin SDK (for backend), Firebase Web SDK (for frontend)

---

## Getting Started

### Prerequisites

To set up and run the LooFinder app, you will need:
- **Node.js** installed on your system (for backend development).
- **Expo CLI** installed globally (for frontend development).
- A **Firebase account** to set up the database.

Firebase Setup
Step 1: Create Firebase Project
Go to the Firebase Console.
Click Add Project and follow the setup process.
Name your project (e.g., LooFinder), configure project settings, and create the project.
Step 2: Enable Realtime Database
In the Firebase Console, navigate to Build > Realtime Database.

Click Create Database and choose a database location.

Set your database rules to allow read and write access during development:

Development Rules:

json
Copy code
{
  "rules": {
    ".read": "true",
    ".write": "true"
  }
}
Remember to secure these rules for production use.

Step 3: Set Up Firebase Admin SDK for Backend
In the Firebase Console, go to Project Settings > Service Accounts.

Click Generate New Private Key, and a JSON file with your Firebase credentials will be downloaded.

Rename the file to firebase-credentials.json and place it in the root of your backend project.

Initialize Firebase Admin SDK in your backend (server.js or app.js):

javascript
Copy code
const admin = require('firebase-admin');
const serviceAccount = require('./firebase-credentials.json');

admin.initializeApp({
  credential: admin.credential.cert(serviceAccount),
  databaseURL: 'https://<YOUR_FIREBASE_PROJECT_ID>.firebaseio.com',
});

const db = admin.database();
Step 4: Firebase Web SDK for React Native (Frontend)
In the Firebase Console, go to Project Settings and scroll down to the Firebase SDK snippet.

Copy the Web API configuration. It will look like this:

javascript
Copy code
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
Install Firebase SDK in your React Native project:

bash
Copy code
expo install firebase
Add Firebase initialization in your App.js:

javascript
Copy code
import firebase from 'firebase/app';
import 'firebase/database'; // Import Firebase services as needed

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  databaseURL: "https://<YOUR_FIREBASE_PROJECT_ID>.firebaseio.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

if (!firebase.apps.length) {
  firebase.initializeApp(firebaseConfig);
}
Backend Integration
Install Dependencies
In your backend project, install the necessary dependencies:

bash
Copy code
npm install express body-parser cors firebase-admin
Set Up Firebase Admin SDK
Make sure your firebase-credentials.json file is in place, and initialize Firebase Admin SDK as described in Step 3.

Create API Endpoints
Submit Review:

Create an API to submit user reviews:

javascript
Copy code
app.post('/submit-review', async (req, res) => {
  const { toiletId, review, rating } = req.body;
  try {
    const reviewRef = db.ref(`reviews/${toiletId}`).push();
    await reviewRef.set({ review, rating });
    res.status(200).send('Review submitted successfully');
  } catch (error) {
    console.error('Error submitting review:', error);
    res.status(500).send('Error submitting review');
  }
});
Get Reviews:

Create an API to fetch reviews for a particular washroom:

javascript
Copy code
app.get('/reviews/:toiletId', async (req, res) => {
  const { toiletId } = req.params;
  try {
    const snapshot = await db.ref(`reviews/${toiletId}`).once('value');
    const reviews = snapshot.val();
    res.status(200).json(reviews);
  } catch (error) {
    console.error('Error fetching reviews:', error);
    res.status(500).send('Error fetching reviews');
  }
});
Frontend Integration
Install Dependencies (Frontend)
In your React Native project, install Firebase:

bash
Copy code
expo install firebase
Firebase Web SDK Configuration
Ensure your frontend is properly configured with the Firebase Web SDK as described in Step 4.

Submit and Display Reviews
Use the backend API to submit and fetch reviews in your frontend.

Running the App
Backend
To run the backend locally:

bash
Copy code
node server.js
Frontend
To run the React Native frontend:

bash
Copy code
expo start
Deploying the Backend on Glitch
Remix the backend project on Glitch.
Upload your firebase-credentials.json file via the Tools menu in Glitch.
Ensure that Firebase Admin SDK is correctly configured in Glitch, and the project starts automatically.
