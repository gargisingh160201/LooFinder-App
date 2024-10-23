# LooFinder-App
# LooFinder App: Firebase Integration

LooFinder is an app that helps users locate public washrooms and submit reviews and ratings. It is built with **React Native** for the frontend and **Node.js (Express)** for the backend. Firebase is used as the database to store user reviews and ratings.

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

### Prerequisites

To set up and run the LooFinder app, you will need:
- **Node.js** installed on your system (for backend development).
- **Expo CLI** installed globally (for frontend development).
- A **Firebase account** to set up the database.

---

## Firebase Setup
### Step 1: Create Firebase Project
- **Go to the Firebase Console.
- **Click Add Project and follow the setup process.
- **Name your project (e.g., LooFinder), configure project settings, and create the project.
### Step 2: Enable Realtime Database
- **In the Firebase Console, navigate to Build > Realtime Database.
- **Click Create Database and choose a database location.
- **Set your database rules to allow read and write access during development:


