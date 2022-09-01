# Web Push Notifications with Firebase

This is a small project I built to try out browser push notifications using Firebase Cloud Messaging (FCM).  
It lets you send notifications directly to the browser from a Node.js backend.

I used plain HTML, JavaScript, and a simple Node server to make everything work.

---

## What It Does

- The browser asks the user for notification permission
- Firebase gives the browser a unique token
- This token gets saved and used later to send push notifications
- A simple `/notify` endpoint sends the message to Firebase, which then delivers it to the browser

---

##How to Set It Up

### 1. Clone the project

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
2. Install the dependencies
bash
Copy
Edit
npm install
3. Firebase Setup
Go to Firebase Console and create a new project

Under Project Settings > Cloud Messaging, generate a new Web Push certificate (VAPID key)

Copy the public key and paste it in app.js (on the client)

Also get your Firebase config and paste it in firebase-config.js like this:

js

export const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "your-app.firebaseapp.com",
  projectId: "your-project-id",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
You also need to place your Firebase service worker script in firebase-messaging-sw.js.

4. Run the app

npm start
Then open your browser and go to:

arduino
http://localhost:3000
You’ll be asked for notification permission. Once allowed, a Firebase token will be generated and shown on the page.

Sending a Notification
You can use Postman or cURL to hit the /notify endpoint:

POST http://localhost:3000/notify
Content-Type: application/json

{
  "title": "Hey there!",
  "body": "This is a push notification from Firebase"
}
Once you send it, a browser notification should pop up instantly.