# 🔥 Setup Guide — WUCC 2026 Predictor v2
## desdelalinea.github.io/wucc2026-predictor

---

## Step 1 — Replace Firebase credentials in index.html

Open `index.html` and find this block near line 620:

```javascript
const FIREBASE_CONFIG = {
  apiKey:            "REPLACE_API_KEY",
  authDomain:        "REPLACE_AUTH_DOMAIN",
  projectId:         "REPLACE_PROJECT_ID",
  storageBucket:     "REPLACE_STORAGE_BUCKET",
  messagingSenderId: "REPLACE_SENDER_ID",
  appId:             "REPLACE_APP_ID"
};
```

Replace each value with your Firebase project credentials.  
**Users never see this — it's hardcoded and hidden in the file.**

---

## Step 2 — Set your admin password

The default admin password hash in the file corresponds to `"desdelalinea2026"`.

**To set your own password:**

1. Open the browser console (F12) on any page
2. Run: `crypto.subtle.digest("SHA-1", new TextEncoder().encode("tu_contraseña")).then(b=>Array.from(new Uint8Array(b)).map(x=>x.toString(16).padStart(2,"0")).join("")).then(console.log)`
3. Copy the resulting hash
4. In `index.html`, find `const ADMIN_PWD_HASH = "..."` and replace the value

---

## Step 3 — Firestore Security Rules

In Firebase Console → Firestore → **Rules**:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /picks/{userId} {
      allow read: if true;
      allow write: if true;
    }
    match /config/{doc} {
      allow read: if true;
      allow write: if true;
    }
  }
}
```

Click **Publish**.

---

## Step 4 — Deploy to GitHub Pages

1. Rename the file to `index.html`
2. Push to `main` branch of `desdelalinea/wucc2026-predictor`
3. Settings → Pages → Source: main / (root) → Save
4. Live at: **https://desdelalinea.github.io/wucc2026-predictor/**

---

## Tournament Format — Power Pools

```
Grupos A-H (5-6 equipos)
    ↓
Top 2 de cada grupo → Power Pools
  Power Pool A: 1°A, 1°B, 1°C, 1°D + 2°E, 2°F, 2°G, 2°H
  Power Pool B: 1°E, 1°F, 1°G, 1°H + 2°A, 2°B, 2°C, 2°D
    ↓
Power Pool standings (round-robin entre 8 equipos)
  Top 4 de PP-A + Top 4 de PP-B → Cuartos de Final (8 equipos)
  5°-8° de cada PP → Pre-Cuartos
    ↓
Cuartos → Semis → Gran Final → 🏆
```

---

## Picks Deadline / Cierre de picks

Picks auto-close on **August 15, 2026 at 09:00 AM Ireland time (UTC+1)**.  
To change the date, edit this line in `index.html`:

```javascript
const DEADLINE = new Date("2026-08-15T08:00:00Z"); // UTC = 09:00 Dublin
```

You can also **force close/reopen** from the Admin panel at any time.

---

## Admin Access

The ⚙️ Admin tab requires a password. Default: `desdelalinea2026`  
Change it following Step 2 above.

Admin capabilities:
- Enter official results match by match (Groups → Power Pools → Bracket)
- Force close or reopen picks before deadline
- Results publish to Firestore and update the leaderboard in real-time for everyone

