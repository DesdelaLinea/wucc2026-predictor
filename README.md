# 🥏 WUCC 2026 — Predictor & Apuestas / Bracket Predictor

> **Desde La Línea** · Limerick, Ireland · August 15–22, 2026

A real-time bracket prediction app for WUCC 2026 with a live leaderboard. Pick group stage winners, build your championship bracket, and compete against friends.

Una app de pronósticos en tiempo real para el WUCC 2026 con leaderboard en vivo. Elige ganadores en la fase de grupos, arma tu bracket y compite contra amigos.

---

## 🌐 Live App / App en Vivo

👉 **[tu-usuario.github.io/wucc2026](https://tu-usuario.github.io/wucc2026)**

---

## ✨ Features / Funcionalidades

| Feature | Descripción |
|---|---|
| 🎯 Group stage picks | Pick winners for every round-robin match / Elige ganadores en fase de grupos |
| 🏆 Championship bracket | Full 16-team knockout bracket / Bracket eliminatorio de 16 equipos |
| ☁️ Real-time leaderboard | Powered by Firebase — updates live for everyone / En vivo para todos |
| 📊 Scoring system | Points for correct picks, advancement, and deep runs / Puntos por aciertos y avance |
| 📱 Mobile-friendly | Works on any device / Funciona en cualquier dispositivo |
| 3️⃣ Divisions | Open (48), Mixed (48), Women (40) |

---

## 🎯 Scoring System / Sistema de Puntaje

| Event | Points |
|---|---|
| Correct group match result | +1 pt |
| Team advances to Championship | +2 pts |
| Correct Round of 16 winner | +3 pts |
| Correct Quarterfinal winner | +5 pts |
| Correct Semifinal winner | +8 pts |
| Correct Champion | +13 pts |
| **Max total** | **635 pts** |

---

## 🚀 How to Use / Cómo Usar

### For Players / Para Participantes

1. **Open the app** at the link above / Abre la app en el enlace de arriba
2. **Enter your name** — this is your leaderboard ID / Escribe tu nombre — es tu ID en el leaderboard
3. **Make your picks** for all 3 divisions (groups + bracket) / Haz tus picks en las 3 divisiones
4. **Click "☁️ Guardar en leaderboard"** — you appear live on the leaderboard / Apareces en vivo en el leaderboard
5. **Watch the results** update in real time as the tournament progresses / Sigue los resultados en tiempo real

### For the Admin / Para el Organizador

1. Open the **⚙️ Admin** tab / Abre la pestaña Admin
2. Enter official results match by match / Ingresa los resultados oficiales partido a partido
3. Click **"💾 Guardar y publicar resultados"** — scores recalculate automatically for everyone / Los puntajes se recalculan para todos automáticamente

---

## 🔧 Setup for Developers / Instalación para Desarrolladores

### Prerequisites / Requisitos
- A [Firebase](https://firebase.google.com) account (free) / Cuenta en Firebase (gratis)
- A [GitHub](https://github.com) account (free) / Cuenta en GitHub (gratis)

### Step 1 — Fork or clone this repo

```bash
git clone https://github.com/tu-usuario/wucc2026.git
cd wucc2026
```

### Step 2 — Create Firebase project

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. **Add project** → name it (e.g. `wucc2026`) → disable Analytics → **Create**
3. Left menu: **Firestore Database → Create database → Test mode → Select region** → Enable
4. **Project settings ⚙️ → Your apps → `</>` (Web)** → Register app → copy the `firebaseConfig` values

### Step 3 — Deploy to GitHub Pages

1. Push `index.html` to your repo's `main` branch
2. Go to **Settings → Pages → Source: main branch / (root)** → **Save**
3. Your app is live at `https://tu-usuario.github.io/wucc2026/`

### Step 4 — Connect Firebase in the app

1. Open your live URL
2. Fill in the Firebase config fields shown in the setup panel
3. Click **"Guardar y conectar"** — the leaderboard goes live instantly

### Step 5 — Firestore Security Rules

In Firebase Console → Firestore → **Rules**, paste:

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

## 📁 Repository Structure / Estructura del Repositorio

```
wucc2026/
├── index.html          # Main app / App principal
├── README.md           # This file / Este archivo
├── SETUP.md            # Detailed Firebase setup guide / Guía detallada Firebase
└── .github/
    └── CODEOWNERS      # Repo ownership
```

---

## 🏅 About / Acerca de

Built by **Desde La Línea** for the WUCC 2026 community.  
Construido por **Desde La Línea** para la comunidad del WUCC 2026.

- 📺 [desdelalinea.tv](https://desdelalinea.tv)
- 📧 desdelalinea.tv@gmail.com

Official tournament results published at **results.wucc2026.com** after finals on August 22.  
Los resultados oficiales se publican en **results.wucc2026.com** después de las finales el 22 de agosto.

---

## 📄 License

MIT — free to use and adapt / Libre para usar y adaptar.
