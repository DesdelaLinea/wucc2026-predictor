<div align="center">

# 🥏 WUCC 2026 — Predictor & Leaderboard

**Desde La Línea** · Limerick, Ireland · August 15–22, 2026

[![Live App](https://img.shields.io/badge/🌐_App_en_vivo-desdelalinea.github.io-C4F135?style=for-the-badge&labelColor=07080C)](https://desdelalinea.github.io/wucc2026-predictor/)

</div>

---

## ¿Qué es? / What is it?

Una app de pronósticos en tiempo real para el **WUCC 2026** con leaderboard en vivo. Los participantes eligen ganadores en las 3 divisiones — grupos, fase intermedia y bracket championship — y compiten entre sí por puntos.

A real-time bracket prediction app for **WUCC 2026** with a live leaderboard. Participants pick winners across 3 divisions — groups, intermediate round, and championship bracket — and compete for points.

---

## 🌐 App en vivo / Live App

### 👉 [desdelalinea.github.io/wucc2026-predictor](https://desdelalinea.github.io/wucc2026-predictor/)

---

## ✨ Funcionalidades / Features

| | Español | English |
|---|---|---|
| 🥏 | 3 divisiones: Open (48), Mixed (48), Women's (40) | 3 divisions with correct team counts |
| 🎯 | Picks en grupos, fase intermedia y bracket | Group, intermediate & bracket picks |
| 🔄 | Formato real WUCC con Cross-Pools y Play-in | Accurate WUCC format with Cross-Pools & Play-ins |
| ☁️ | Leaderboard en vivo con Firebase | Real-time leaderboard powered by Firebase |
| 🔒 | Picks se bloquean al inicio del torneo | Picks locked automatically at tournament start |
| 🏆 | Sistema de puntaje progresivo | Progressive scoring system |
| 🌙 | Modo oscuro / claro | Dark / Light mode |
| 📱 | Responsive, funciona en cualquier dispositivo | Works on any device |
| 🤝 | Sección de sponsors sincronizada | Synchronized sponsors section |
| 🔐 | Panel admin protegido con contraseña | Password-protected admin panel |

---

## 🔄 Formato del torneo / Tournament Format

### Open & Mixed — 48 equipos / teams

```
8 grupos de 6 equipos
        ↓
4° vs 5° Play-in (8 partidos)       →  Perdedor: 33°–40°
1°/2°/3° + ganador play-in           →  Round of 32 (16 partidos)
        ↓
Round of 16 → Cuartos → Semis → Final 🏆
        ↓ (perdedores)
6° directo a Consolación 41°–48°
```

### Women's — 40 equipos / teams

```
8 grupos de 5 equipos
        ↓
10 Cross-Pools I–R (round-robin de 4 equipos)
  Pools I-L (Top):  1°/2° → Pre-QF bye   |  3°/4° → 16 Play-in
  Pools M-P (Mid):  1°/2° → 16 Play-in   |  3°/4° → Consolación
  Pools Q-R (Bot):  todos → Consolación
        ↓
16 Play-in (8 partidos)  →  Pre-Cuartos → Cuartos → Semis → Final 🏆
```

---

## 📊 Sistema de puntaje / Scoring System

| Evento | Puntos |
|---|---|
| Partido correcto (grupo / play-in / cross-pool) | +1 pt |
| Equipo avanza a siguiente fase | +2 pts |
| Round of 16 / Pre-Cuartos correcto | +3 pts |
| Cuartos de Final correcto | +5 pts |
| Semifinal correcta | +8 pts |
| Campeón correcto | +13 pts |
| **Máximo total** | **635 pts** |

---

## ⏰ Fecha límite / Deadline

Los picks se cierran automáticamente el **15 de agosto de 2026 a las 9:00 AM hora de Irlanda (UTC+1)** — al inicio del primer partido del torneo.

Picks auto-close on **August 15, 2026 at 9:00 AM Ireland time (UTC+1)** — when the first match begins.

---

## 🚀 Cómo usar / How to use

### Para participantes / For participants

1. Abre la app → escribe tu nombre
2. Selecciona una división (Open 🔵 / Mixed 🟣 / Women's 🌸)
3. Elige ganadores en Grupos → Fase intermedia → Championship
4. Repite para las 3 divisiones
5. Haz clic en **☁️ Guardar en leaderboard**
6. ¡Apareces en el ranking en tiempo real!

### Para el admin / For the admin

1. Pestaña **⚙️ Admin** → contraseña
2. Ingresa resultados partido a partido
3. Guarda → el leaderboard se actualiza para todos en vivo
4. Gestiona sponsors desde el panel Admin
5. Controla el cierre de picks manualmente si es necesario

---

## 📁 Estructura del repositorio / Repo structure

```
wucc2026-predictor/
├── index.html          ← App completa (todo en un archivo)
├── README.md           ← Este archivo
├── SETUP.md            ← Guía de configuración para el admin
├── HOW-TO-PLAY.html    ← Página de instrucciones para compartir
├── CONTRIBUTING.md     ← Cómo reportar bugs
├── LICENSE             ← MIT
└── .nojekyll           ← Necesario para GitHub Pages
```

---

## 📞 Contacto / Contact

**Desde La Línea** — Medio de Ultimate Frisbee en español

📧 [desdelalinea.tv@gmail.com](mailto:desdelalinea.tv@gmail.com)
🌐 [desdelalinea.github.io/wucc2026-predictor](https://desdelalinea.github.io/wucc2026-predictor/)

Resultados oficiales / Official results: **results.wucc2026.com** — 22 agosto / August 22, 2026

---

## 📄 Licencia / License

MIT — libre para usar y adaptar / free to use and adapt.
