# 🛠️ SETUP.md — Guía de configuración / Setup Guide

> **Solo para el admin (Desde La Línea).** Los participantes no necesitan hacer nada — simplemente abren la URL.
> **Admin-only guide.** Participants just open the URL — zero configuration needed on their end.

---

## Paso 1 / Step 1 — Crear proyecto Firebase

1. Ve a **[console.firebase.google.com](https://console.firebase.google.com)**
2. **Agregar proyecto** → nombre (ej. `wucc2026-predictor`) → desactiva Analytics → **Crear**
3. Menú lateral: **Firestore Database → Crear base de datos → Modo de prueba → Región: `nam5 (us-central)`** → Habilitar

---

## Paso 2 / Step 2 — Obtener credenciales

1. ⚙️ **Configuración del proyecto → Tus apps → `</>`** (Web)
2. Registra la app con cualquier nombre
3. Copia el bloque `firebaseConfig`:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "tu-proyecto.firebaseapp.com",
  projectId: "tu-proyecto",
  storageBucket: "tu-proyecto.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

---

## Paso 3 / Step 3 — Pegar credenciales en index.html

Abre `index.html` en cualquier editor de texto y busca este bloque (cerca del final del archivo):

```javascript
const FIREBASE_CONFIG = {
  apiKey:            "REEMPLAZA_CON_TU_API_KEY",
  authDomain:        "REEMPLAZA_CON_TU_AUTH_DOMAIN",
  projectId:         "REEMPLAZA_CON_TU_PROJECT_ID",
  storageBucket:     "REEMPLAZA_CON_TU_STORAGE_BUCKET",
  messagingSenderId: "REEMPLAZA_CON_TU_SENDER_ID",
  appId:             "REEMPLAZA_CON_TU_APP_ID"
};
```

Reemplaza cada valor con el tuyo. **Los usuarios nunca ven estas credenciales** — están embebidas en el archivo que tú controlas.

---

## Paso 4 / Step 4 — Configurar reglas de seguridad Firestore

En Firebase Console → Firestore → **Reglas**, pega exactamente esto y haz clic en **Publicar**:

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

---

## Paso 5 / Step 5 — Cambiar la contraseña admin

La contraseña por defecto es `desdelalinea2026`. Para cambiarla:

1. Abre la consola del navegador (F12) en cualquier página
2. Pega y ejecuta esto con tu nueva contraseña:

```javascript
crypto.subtle.digest("SHA-1", new TextEncoder().encode("TU_NUEVA_CONTRASEÑA"))
  .then(b => Array.from(new Uint8Array(b)).map(x=>x.toString(16).padStart(2,"0")).join(""))
  .then(console.log)
```

3. Copia el hash que aparece (40 caracteres hexadecimales)
4. En `index.html`, busca `ADMIN_PWD_HASH` y reemplaza el valor entre comillas

---

## Paso 6 / Step 6 — Publicar en GitHub Pages

1. Crea un repo en GitHub: `tu-usuario/wucc2026-predictor` → **Public**
2. Sube todos los archivos (`index.html`, `README.md`, `SETUP.md`, `HOW-TO-PLAY.html`, `LICENSE`, `CONTRIBUTING.md`, `.nojekyll`)
3. **Settings → Pages → Source: main branch / (root)** → **Save**
4. En ~1 minuto tu app vive en: `https://tu-usuario.github.io/wucc2026-predictor/`

> Para Desde La Línea: `https://desdelalinea.github.io/wucc2026-predictor/`

---

## Flujo del admin durante el torneo

### Ingresar resultados
1. Pestaña **⚙️ Admin** → contraseña `desdelalinea2026`
2. Selecciona la división (Open / Mixed / Women's)
3. Pestaña **Grupos** → haz clic en el equipo ganador de cada partido
4. Cuando los grupos terminen → pestaña **Fase intermedia** → ingresa resultados del Play-in o Cross-Pools
5. Cuando avance → pestaña **Championship** → ingresa resultados del bracket
6. Clic en **💾 Guardar y publicar** → el leaderboard se actualiza en tiempo real para todos

### Controlar cierre de picks
- Los picks se cierran automáticamente el **15 agosto 2026 a las 9:00 AM hora Irlanda**
- Puedes forzar cierre manual desde Admin → sección **"Control de cierre"**
- También puedes reabrir si es necesario (ej. corrección de horario)

### Subir sponsors
1. Admin → sección **"Sponsors & Aliados"**
2. Clic en **"+ Agregar logo"** → sube PNG/JPG/SVG (máx 300KB)
3. Escribe el nombre opcional debajo de cada logo
4. Clic en **💾 Guardar y publicar** → aparece para todos en segundos

---

## Estructura de datos en Firestore

```
firestore/
├── picks/
│   └── {nombre_usuario}/      # Un documento por participante
│       ├── n: "Juan"          # Nombre para mostrar
│       ├── p: { Open, Mixed, Women }  # Todos los picks
│       ├── ts: 1720000000000  # Timestamp
│       └── v: 4               # Versión del formato
│
└── config/
    ├── results/               # Resultados oficiales (admin)
    │   ├── results: { Open, Mixed, Women }
    │   └── ts: 1720000000000
    ├── settings/              # Control de picks
    │   ├── forceClosed: false
    │   └── ts: 1720000000000
    └── sponsors/              # Logos de sponsors
        ├── sponsors: [{id, name, data}]
        ├── label: "SPONSORS & ALIADOS"
        └── ts: 1720000000000
```

---

## Solución de problemas / Troubleshooting

| Problema | Solución |
|---|---|
| `🔴 Sin configurar` en el header | Abre `index.html`, busca `REEMPLAZA_CON_TU_API_KEY` y pega tus credenciales |
| `🔴 Error Firebase` | Verifica que los 6 valores sean correctos y que Firestore esté habilitado |
| "Contraseña incorrecta" en Admin | La contraseña por defecto es `desdelalinea2026` — si la cambiaste, verifica el hash |
| Los picks de alguien aparecen como 0 pts | Normal hasta que el admin ingrese resultados reales |
| Los sponsors no aparecen | Ve a Admin → Sponsors y haz clic en "Guardar y publicar" de nuevo |
| La app no carga en GitHub Pages | Verifica que el archivo se llame `index.html` y que `.nojekyll` esté en el repo |

---

## Deadline — cambiar la fecha

Si los horarios del torneo cambian, edita esta línea en `index.html`:

```javascript
const DEADLINE = new Date("2026-08-15T08:00:00Z"); // UTC = 09:00 Dublin
```

La fecha está en **UTC** — hora de Irlanda en agosto es UTC+1, así que 09:00 Irlanda = 08:00 UTC.

---

📧 **desdelalinea.tv@gmail.com**
