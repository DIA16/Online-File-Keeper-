# FileShelf — Setup Guide (10 Minutes, Free)

---

## WHAT YOU NEED
- A Google account (Gmail)
- A browser (Chrome, Firefox, Edge)
- This HTML file

---

## STEP 1 — Create Your Firebase Project

1. Open your browser and go to:
   👉 https://console.firebase.google.com

2. Sign in with your Google/Gmail account

3. Click **"Add project"**

4. Type any project name (e.g. "my-fileshelf") → Click **Continue**

5. On the next screen, you can turn OFF Google Analytics (not needed) → Click **Create project**

6. Wait ~10 seconds → Click **Continue**

---

## STEP 2 — Register a Web App & Get Your Config

1. Inside your project, look for the **Web icon: `</>`**
   (It's on the project overview page)

2. Click it → Give your app any name (e.g. "fileshelf") → Click **Register app**

3. You will see a block of code that looks like this:

   ```
   const firebaseConfig = {
     apiKey: "AIzaSy...",
     authDomain: "my-fileshelf.firebaseapp.com",
     projectId: "my-fileshelf",
     storageBucket: "my-fileshelf.appspot.com",
     messagingSenderId: "123456789",
     appId: "1:123456789:web:abc123"
   };
   ```

4. **Copy all 6 values** (the parts in quotes after each colon)

---

## STEP 3 — Paste Config Into the HTML File

1. Open `fileshelf.html` in a text editor
   - On phone: use any text editor app
   - On PC: use Notepad (Windows) or TextEdit (Mac)

2. Find this section near the top of the file:

   ```
   window.FIREBASE_CONFIG = {
     apiKey:            "PASTE_YOUR_apiKey_HERE",
     authDomain:        "PASTE_YOUR_authDomain_HERE",
     ...
   ```

3. Replace each `PASTE_YOUR_..._HERE` with your actual values from Step 2

4. Save the file

---

## STEP 4 — Enable Firebase Storage

1. Back in Firebase console, look in the left sidebar for **"Build"** → click **"Storage"**

2. Click **"Get started"**

3. Click **Next** → click **Done** (default settings are fine)

4. You will now see the Storage page. Click the **"Rules"** tab at the top

5. You will see some code. Replace ALL of it with this:

   ```
   rules_version = '2';
   service firebase.storage {
     match /b/{bucket}/o {
       match /{allPaths=**} {
         allow read, write: if true;
       }
     }
   }
   ```

6. Click **Publish**

---

## STEP 5 — Open and Use the App

### Option A — Open directly on your device (easiest)
Just double-click `fileshelf.html` in your file manager — it opens in your browser.
Works on phone and laptop.

### Option B — Host online so you can access from any device
1. Go to https://app.netlify.com → Sign up free
2. Click **"Add new site"** → **"Deploy manually"**
3. Drag your `fileshelf.html` file onto the page
4. Netlify gives you a free URL like `https://random-name.netlify.app`
5. Open that URL on any device, anywhere

---

## HOW TO USE

| Action | How |
|--------|-----|
| Upload | Tap the upload area or drag files onto it |
| View image | Tap the file card |
| Play audio | Tap the file card → press play |
| Read text | Tap the file card |
| Download | Open file → tap ⬇ Download |
| Copy link | Open file → tap 🔗 Copy Link |
| Delete | Open file → tap 🗑 Delete → confirm |
| Sort files | Tap "Newest first / Oldest first" |

---

## LIMITS (Free Firebase Tier)

| Item | Free Limit |
|------|-----------|
| Storage | 5 GB |
| Downloads per day | 1 GB |
| Max file size (this app) | 10 MB |

This is more than enough for personal use.

---

## CHANGE THE FILE SIZE LIMIT

Open `fileshelf.html` in a text editor and find:
```
const MAX = 10 * 1024 * 1024;
```
Change `10` to any number (in MB). Save the file.

---

## TROUBLESHOOTING

**"Could not load files" or blank screen?**
→ Make sure you pasted all 6 Firebase config values correctly.
→ Make sure there are no extra spaces or missing quote marks.

**Upload fails?**
→ Check that you set the Storage Rules to `allow read, write: if true;` and clicked Publish.

**File is too large?**
→ The app limits uploads to 10 MB. Reduce the limit in the code or compress the file first.

---

Questions? Open the HTML file — it has a built-in setup guide that shows when config is missing.
