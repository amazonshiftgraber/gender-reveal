# Gender Reveal Party Setup Guide
### Rusita & Tejash · 30th May 2026

---

## What you'll set up
- **Firebase** (free) — stores all predictions in real-time
- **Netlify** (free) — hosts the website so guests can open it via QR code

Total time: ~15 minutes

---

## STEP 1 — Create a Firebase Project

1. Go to **https://console.firebase.google.com**
2. Click **"Add project"** → name it `gender-reveal` → click through and hit **Create project**
3. Once inside the project, click the **Web icon `</>`** to add a web app
4. Give it any nickname (e.g. `reveal-app`) → click **Register app**
5. You'll see a block of code like this — **copy the values inside the curly braces:**

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "gender-reveal-xxxxx.firebaseapp.com",
  projectId: "gender-reveal-xxxxx",
  storageBucket: "gender-reveal-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456:web:abcdef"
};
```

6. Open **`index.html`** and **`results.html`** in a text editor (Notepad on Windows, TextEdit on Mac)
7. Find the `firebaseConfig` section near the bottom of each file and replace the `"YOUR_..."` placeholders with your real values (do this in BOTH files)

---

## STEP 2 — Set Up Firestore Database

1. In Firebase Console, click **"Firestore Database"** in the left menu
2. Click **"Create database"**
3. Choose **"Start in test mode"** → select any location → click **Enable**
4. Click the **"Rules"** tab and replace the rules with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /predictions/{doc} {
      allow read, write: if true;
    }
  }
}
```

5. Click **Publish**

---

## STEP 3 — Deploy to Netlify (Free Hosting)

1. Go to **https://app.netlify.com/drop**
2. Simply **drag and drop** the entire `gender-reveal` folder onto the page
3. Netlify gives you a free URL like `https://amazing-name-12345.netlify.app`
4. Optional: click **"Site settings → Change site name"** to get something nicer like `rusita-tejash-baby.netlify.app`

---

## STEP 4 — Generate QR Codes

1. Go to **https://www.qr-code-generator.com** (free)
2. Paste your Netlify URL → download the QR code image
3. Print it and place on each table!

---

## At the Party

- **Guest form**: `https://your-site.netlify.app/index.html`  
  *(This is what the QR code links to)*

- **Live results screen**: `https://your-site.netlify.app/results.html`  
  *(Open this on a laptop/TV at the party — it updates live as guests submit!)*

---

## Done! 🎉

The results page updates in real-time — no refresh needed.
