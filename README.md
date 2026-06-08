<div align="center">

# 🥏 WUCC 2026 — Predictor & Leaderboard

**Desde La Línea** · Limerick, Irlanda · 15–22 Agosto 2026

[![App en vivo](https://img.shields.io/badge/🌐_App_en_vivo-desdelalinea.github.io-C4F135?style=for-the-badge&labelColor=07080C)](https://desdelalinea.github.io/wucc2026-predictor/)

</div>

---

## ¿Qué es? / What is it?

App de pronósticos en tiempo real para el **WUCC 2026** con leaderboard en vivo. Elige ganadores en las 3 divisiones — grupos, fase intermedia y bracket championship — y compite contra la comunidad.

Real-time bracket prediction app for **WUCC 2026** with a live leaderboard. Pick winners across 3 divisions and compete for points.

---

## 🌐 [desdelalinea.github.io/wucc2026-predictor](https://desdelalinea.github.io/wucc2026-predictor/)

---

## ✨ Funcionalidades / Features

| | |
|---|---|
| 🥏 | Open (48 eq.) · Mixed (48 eq.) · Women's (40 eq.) con formato real WUCC |
| 🔄 | Cross-Pools, Play-ins y brackets correctos por división |
| ☁️ | Leaderboard en tiempo real con Firebase — sin registro para usuarios |
| 📊 | Mis Picks vs Resultados — compara partido a partido con ✅/❌ |
| 📤 | Compartir predicción — genera imagen 1080×1080 descargable |
| 🔒 | Picks se bloquean automáticamente el 15 agosto 9AM hora Irlanda |
| 🏆 | Leaderboard con conteo de picks y estado previo a resultados |
| ⚠️ | Detección de nombre duplicado al registrarse |
| 💾 | Modal de confirmación antes de guardar |
| 🤝 | Sección de sponsors sincronizada en la nube |
| 🌙☀️ | Modo oscuro / claro |
| 📱 | Responsive — funciona en cualquier dispositivo |
| ⬇️ | Exportar datos (resultados JSON, picks CSV, leaderboard CSV) |
| 🔐 | Panel admin protegido con contraseña |

---

## 🔄 Formato por división / Tournament Format

### Open & Mixed — 48 equipos

```
8 grupos de 6  →  4°vs5° Play-in  →  Round of 32  →  R16  →  QF  →  SF  →  Final 🏆
                                       1°/2°/3° con bye   6° → Consolación
```

### Women's — 40 equipos

```
8 grupos de 5  →  10 Cross-Pools I–R (4 equipos c/u)
   Pools I-L (Top): 1°/2° → Pre-QF · 3°/4° → 16 Play-in
   Pools M-P (Mid): 1°/2° → 16 Play-in · 3°/4° → Consolación
   Pools Q-R (Bot): todos → Consolación
→  16 Play-in (8 partidos)  →  Pre-QF  →  QF  →  SF  →  Final 🏆
```

---

## 📊 Sistema de puntaje / Scoring

| Evento | Pts |
|---|---|
| Partido correcto (grupo / play-in / cross-pool) | +1 |
| Equipo avanza a siguiente fase | +2 |
| Round of 16 / Pre-Cuartos | +3 |
| Cuartos de Final | +5 |
| Semifinal | +8 |
| Campeón | +13 |
| **Máximo total** | **635** |

---

## ⏰ Fecha límite / Deadline

**15 agosto 2026 · 9:00 AM hora Irlanda (UTC+1)**
Picks bloqueados automáticamente. El admin también puede forzar cierre/apertura manual.

---

## 🚀 Para participantes / For participants

1. Abre la URL → escribe tu nombre
2. Selecciona división (🔵 Open / 🟣 Mixed / 🌸 Women's)
3. Grupos → Fase intermedia → Championship
4. Repite en las 3 divisiones
5. **☁️ Guardar en leaderboard** → apareces en el ranking en vivo
6. Pestaña **📊 Mis vs Resultados** para seguir tu score durante el torneo
7. Botón **📤 Compartir** para generar imagen de tu predicción

---

## 🛠️ Setup para el admin

Ver **[SETUP.md](SETUP.md)** — guía completa paso a paso.

**Resumen:** abre `index.html`, busca `REEMPLAZA_CON_TU_API_KEY` y pega tus 6 credenciales de Firebase. Sube a GitHub → activa GitHub Pages. Los usuarios no configuran nada.

---

## 📁 Archivos del repo

```
wucc2026-predictor/
├── index.html        ← App completa (todo en uno)
├── README.md         ← Este archivo
├── SETUP.md          ← Guía de configuración admin
├── HOW-TO-PLAY.html  ← Instrucciones para compartir con participantes
├── CONTRIBUTING.md   ← Reportar bugs
├── LICENSE           ← MIT
└── .nojekyll         ← Necesario para GitHub Pages
```

---

## 📞 Contacto

**Desde La Línea** — Medio de Ultimate Frisbee en español
📧 [desdelalinea.tv@gmail.com](mailto:desdelalinea.tv@gmail.com)
🌐 [desdelalinea.github.io/wucc2026-predictor](https://desdelalinea.github.io/wucc2026-predictor/)

Resultados oficiales: **results.wucc2026.com** — 22 agosto 2026

---

MIT License · Desde La Línea 2026
