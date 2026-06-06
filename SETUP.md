# 🔥 Firebase Setup Guide / Guía de Configuración Firebase

Complete step-by-step guide to connect the WUCC 2026 Predictor to Firebase.  
Guía completa paso a paso para conectar el Predictor WUCC 2026 a Firebase.

---

## Part 1 — Create Firebase Project / Parte 1 — Crear el Proyecto Firebase

### English

1. Go to **[console.firebase.google.com](https://console.firebase.google.com)**
2. Click **"Add project"**
3. Enter a project name, e.g. `wucc2026-predictor`
4. **Disable** Google Analytics (not needed) → click **Create project**
5. Wait ~30 seconds for the project to be ready

### Español

1. Ve a **[console.firebase.google.com](https://console.firebase.google.com)**
2. Haz clic en **"Agregar proyecto"**
3. Escribe un nombre, por ejemplo `wucc2026-predictor`
4. **Desactiva** Google Analytics (no lo necesitamos) → clic en **Crear proyecto**
5. Espera ~30 segundos hasta que el proyecto esté listo

---

## Part 2 — Create Firestore Database / Parte 2 — Crear la Base de Datos Firestore

### English

1. In the left sidebar, click **"Firestore Database"**
2. Click **"Create database"**
3. Select **"Start in test mode"** *(allows read/write for 30 days — we'll set permanent rules next)*
4. Choose a region: **`nam5 (us-central)`** is recommended for global access
5. Click **Enable** — database is ready in ~10 seconds

### Español

1. En el menú lateral, haz clic en **"Firestore Database"**
2. Clic en **"Crear base de datos"**
3. Selecciona **"Comenzar en modo de prueba"** *(permite lectura/escritura por 30 días — luego configuramos reglas permanentes)*
4. Elige una región: **`nam5 (us-central)`** es recomendada para acceso global
5. Clic en **Habilitar** — la base de datos estará lista en ~10 segundos

---

## Part 3 — Get Your App Credentials / Parte 3 — Obtener las Credenciales

### English

1. Click the **⚙️ gear icon** (top left, next to "Project Overview")
2. Click **"Project settings"**
3. Scroll down to **"Your apps"**
4. Click the **`</>`** (Web) icon
5. Enter any app nickname (e.g. `wucc2026-web`) → click **"Register app"**
6. You'll see a code block like this — **copy the 6 values**:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "wucc2026.firebaseapp.com",
  projectId: "wucc2026",
  storageBucket: "wucc2026.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

### Español

1. Haz clic en el **ícono ⚙️** (arriba a la izquierda, junto a "Descripción general del proyecto")
2. Clic en **"Configuración del proyecto"**
3. Baja hasta **"Tus apps"**
4. Haz clic en el ícono **`</>`** (Web)
5. Escribe cualquier nombre (ej. `wucc2026-web`) → clic en **"Registrar app"**
6. Verás un bloque de código como este — **copia los 6 valores**:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "wucc2026.firebaseapp.com",
  projectId: "wucc2026",
  storageBucket: "wucc2026.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

---

## Part 4 — Set Security Rules / Parte 4 — Configurar Reglas de Seguridad

### English

1. In the Firebase console, go to **Firestore Database → Rules** tab
2. Delete everything in the editor and paste the following:

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

3. Click **"Publish"**

> ⚠️ **Note:** These rules allow anyone to read and write. This is intentional for a public tournament predictor. If you want to restrict writing to authenticated users in the future, see [Firebase Auth docs](https://firebase.google.com/docs/auth).

### Español

1. En la consola de Firebase, ve a **Firestore Database → pestaña Reglas**
2. Borra todo lo que hay en el editor y pega lo siguiente:

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

3. Haz clic en **"Publicar"**

> ⚠️ **Nota:** Estas reglas permiten que cualquier persona lea y escriba. Esto es intencional para un predictor de torneo público. Si quieres restringir escritura a usuarios autenticados en el futuro, consulta [Firebase Auth docs](https://firebase.google.com/docs/auth).

---

## Part 5 — Connect Firebase in the App / Parte 5 — Conectar Firebase en la App

### English

1. Open your published app URL
2. You'll see a green setup panel at the top of **"Mis Picks"**
3. Paste each value from your `firebaseConfig` into the corresponding field:
   - **API Key** → `apiKey`
   - **Auth Domain** → `authDomain`
   - **Project ID** → `projectId`
   - **Storage Bucket** → `storageBucket`
   - **Messaging Sender ID** → `messagingSenderId`
   - **App ID** → `appId`
4. Click **"💾 Guardar y conectar"**
5. The status indicator in the header turns 🟢 **Conectado**
6. The config is saved in your browser — you only need to do this **once per device**

### Español

1. Abre la URL de tu app publicada
2. Verás un panel verde de configuración al inicio de **"Mis Picks"**
3. Pega cada valor de tu `firebaseConfig` en el campo correspondiente:
   - **API Key** → `apiKey`
   - **Auth Domain** → `authDomain`
   - **Project ID** → `projectId`
   - **Storage Bucket** → `storageBucket`
   - **Messaging Sender ID** → `messagingSenderId`
   - **App ID** → `appId`
4. Haz clic en **"💾 Guardar y conectar"**
5. El indicador en el header cambia a 🟢 **Conectado**
6. La configuración queda guardada en tu navegador — solo necesitas hacerlo **una vez por dispositivo**

---

## Part 6 — Share with Participants / Parte 6 — Compartir con Participantes

### English

Share your app URL with friends. They will:
1. Enter the URL → the app loads with the Firebase config panel
2. **They also need to paste the Firebase config once** (same 6 values)
3. Enter their name → make picks → click **"☁️ Guardar en leaderboard"**
4. They appear on the live leaderboard instantly

> 💡 **Tip:** Consider creating a short link with [bit.ly](https://bit.ly) or similar for easy sharing.

### Español

Comparte la URL de tu app con los participantes. Ellos deberán:
1. Abrir la URL → la app carga con el panel de configuración Firebase
2. **También deben pegar la config de Firebase una vez** (los mismos 6 valores)
3. Escribir su nombre → hacer picks → clic en **"☁️ Guardar en leaderboard"**
4. Aparecen en el leaderboard en vivo instantáneamente

> 💡 **Tip:** Considera crear un enlace corto con [bit.ly](https://bit.ly) para compartir más fácilmente.

---

## 🗂️ Firestore Data Structure / Estructura de Datos en Firestore

```
firestore/
├── picks/                     # Collection — one doc per participant
│   ├── {nombre_sanitizado}/   # Document ID = sanitized name
│   │   ├── v: 2               # Version
│   │   ├── n: "Juan"          # Display name
│   │   ├── ts: 1720000000000  # Timestamp
│   │   └── p: { Open, Mixed, Women }  # Full picks state
│
└── config/                    # Collection — app configuration
    └── results/               # Document — official tournament results
        ├── ts: 1720000000000
        └── results: { Open, Mixed, Women }  # Admin-entered results
```

---

## ❓ Troubleshooting / Solución de Problemas

| Problem / Problema | Solution / Solución |
|---|---|
| "Firebase no conectó" after saving config | Double-check all 6 values — no extra spaces / Verifica los 6 valores — sin espacios extra |
| Leaderboard shows 0 participants | Firebase not connected on this device — paste config again / Firebase no conectado — pega config de nuevo |
| "Permission denied" error in console | Check Firestore Rules are published correctly / Verifica que las reglas estén publicadas |
| Config panel keeps showing | Clear browser localStorage: DevTools → Application → Local Storage → Clear all / Limpia el localStorage del navegador |
| Two entries with same name | Names are case-insensitive but must be identical — "Juan" and "juan" merge / Los nombres se unifican, deben ser idénticos |

---

## 📞 Support / Soporte

📧 **desdelalinea.tv@gmail.com**
