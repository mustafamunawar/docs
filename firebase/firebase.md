# Firebase

1. Firebase main (console) page is `https://console.firebase.google.com/` go to it and create a `project`

- A `project` in Firebase is a container for our app. It lets us share data and analytics across platforms (e.g., Android, iOS, and web) so users have the same experience regardless of the device they’re on.

2. Navigate to the Cloud Firestore page by clicking its icon on left sidebar

3. Create a database by clicking Create Database button on Firebase's `Cloud Firestore` page

- Choose `Start in test mode` and click Next. Then, on the next screen, click `Enable`. Once these steps have been completed, an empty database will be created for us.

4. create a `collection` . Let's call it `users` to keep records of users.

## On React app side:

1. To integrate Firebase into our React app, we need to first get the web configuration object from ```Get started by adding Firebase to your app" ( select </> for we app) and then use it to initialize Firebase in our react app.

2. In React project install Firebase using `npm i firebase`
3. In React project create a file called ``firebase.js` (in same directory as App.js).

```js
import firebase from "firebase/compat/app";
import "firebase/compat/auth";
import "firebase/compat/firestore";
const firebaseConfig = {
  apiKey: "API_KEY",
  authDomain: "AUTH_DOMAIN",
  projectId: "PROJECT_ID",
  storageBucket: "STORAGE_BUCKET",
  messagingSenderId: "MESSAGING_SENDER_ID",
  appId: "APP_ID",
};
firebase.initializeApp(firebaseConfig);
const db = firebase.firestore();

export default db;
```

- Note that the firebaseConfig should be replaced by the firebaseConfig object from your Firebase project
