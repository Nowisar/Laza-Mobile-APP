Project Overview

Laza is a cross-platform Flutter e-commerce MVP for Android and iOS.
It uses Firebase Authentication, Cloud Firestore (cart & favorites only), and the Platzi Fake Store API for products.
End-to-end testing is implemented using Appium.

Installation & Dependencies
flutter doctor
git clone <repo-url>
cd laza
flutter pub get

Firebase Setup

Create a Firebase project

Enable Email/Password Authentication

Add Android & iOS apps

Place:

google-services.json → android/app/

GoogleService-Info.plist → ios/Runner/

Firestore Rules
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{collection}/{userId} {
      allow read, write: if request.auth != null
        && request.auth.uid == userId;
    }
  }
}

Run the App

Android / iOS

flutter run

Appium Tests
npm install -g appium
appium
cd appium-tests
npm test
