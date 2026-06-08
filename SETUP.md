# 🛠️ SETUP.md — Guía de configuración / Setup Guide

> **Solo para el admin (Desde La Línea).** Los participantes abren la URL y listo — no configuran nada.

---

## Paso 1 — Firebase: crear el proyecto

1. Ve a **[console.firebase.google.com](https://console.firebase.google.com)**
2. **Agregar proyecto** → nombre (ej. `wucc2026-predictor`) → desactiva Analytics → **Crear**
3. Menú lateral: **Firestore Database → Crear base de datos → Modo de prueba → Región: `nam5`** → Habilitar

---

## Paso 2 — Obtener credenciales

1. ⚙️ **Configuración del proyecto → Tus apps → `</>`** (Web)
2. Registra la app → copia el bloque `firebaseConfig`:
```javascript
{ apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId }
```

---

## Paso 3 — Pegar credenciales en index.html ⭐ ÚNICO PASO TÉCNICO

Abre `index.html` en cualquier editor de texto. Busca:
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
Reemplaza cada valor. Guarda. Listo.

---

## Paso 4 — Reglas de seguridad Firestore

Firebase → Firestore → **Reglas** → pega y publica:
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

## Paso 5 — Cambiar contraseña admin (opcional)

Contraseña por defecto: `desdelalinea2026`

Para cambiarla — ejecuta en consola del navegador (F12):
```javascript
crypto.subtle.digest("SHA-1", new TextEncoder().encode("TU_NUEVA_CONTRASEÑA"))
  .then(b => Array.from(new Uint8Array(b)).map(x=>x.toString(16).padStart(2,"0")).join(""))
  .then(console.log)
```
Copia el hash → busca `ADMIN_PWD_HASH` en `index.html` → reemplaza.

---

## Paso 6 — Publicar en GitHub Pages

1. Repo: `desdelalinea/wucc2026-predictor` → **Public**
2. Sube todos los archivos (incluido `.nojekyll`)
3. **Settings → Pages → Source: main / (root)** → **Save**
4. URL: `https://desdelalinea.github.io/wucc2026-predictor/`

---

## Durante el torneo — guía del admin

### Ingresar resultados
1. **⚙️ Admin** → contraseña
2. División → **Grupos** → clic en ganador de cada partido
3. Cuando terminen grupos → **Fase intermedia** (Play-in o Cross-Pools)
4. Cuando avance → **Bracket** → resultados del championship
5. **💾 Guardar y publicar** → leaderboard actualizado en vivo para todos

### Exports / Backup (en Admin → Resultados)
- **⬇️ Exportar resultados JSON** — backup de todos los resultados
- **⬇️ Exportar picks CSV** — todos los picks de todos los participantes
- **⬇️ Exportar leaderboard CSV** — ranking con puntos

### Control de picks
- Cierre automático: **15 agosto 2026 · 9:00 AM Irlanda (UTC+1)**
- Para cambiar la fecha, edita en `index.html`:
  ```javascript
  const DEADLINE = new Date("2026-08-15T08:00:00Z");
  ```
- Cierre/apertura manual: Admin → sección "Control de cierre"

### Sponsors
- Admin → **Sponsors & Aliados** → **+ Agregar logo**
- Sube PNG/JPG/SVG (máx 300KB), nombre opcional
- **💾 Guardar y publicar** → visible para todos en tiempo real

---

## Estructura de datos Firestore

```
firestore/
├── picks/{docId}          ← Un documento por participante
│   ├── n: "Nombre"
│   ├── p: { Open, Mixed, Women }  ← Todos los picks
│   ├── ts: timestamp
│   └── v: 4
└── config/
    ├── results/           ← Resultados oficiales (admin)
    ├── settings/          ← forceClosed: true/false
    └── sponsors/          ← Logos de sponsors
```

---

## Solución de problemas

| Problema | Solución |
|---|---|
| `🔴 Sin configurar` en header | Pega las credenciales Firebase en `index.html` |
| `🔴 Error Firebase` | Verifica los 6 valores y que Firestore esté habilitado |
| "Contraseña incorrecta" | Por defecto: `desdelalinea2026` |
| Picks muestran 0 pts | Normal — el admin debe ingresar resultados primero |
| App no carga en GitHub | Verifica que el archivo se llame `index.html` y que `.nojekyll` esté en el repo |

---

📧 desdelalinea.tv@gmail.com
