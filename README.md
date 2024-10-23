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

### Clone the Repo

```bash
git clone <YOUR_REPO_URL>
cd <YOUR_PROJECT_FOLDER>
