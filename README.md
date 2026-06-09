<div align="center">

# 🥏 WUCC 2026 — Predictor & Leaderboard

**Desde La Línea** · Limerick, Irlanda · 15–22 Agosto 2026

[![App en vivo](https://img.shields.io/badge/🌐_App_en_vivo-desdelalinea.github.io-C4F135?style=for-the-badge&labelColor=07080C)](https://desdelalinea.github.io/wucc2026-predictor/)
[![Ko-fi](https://img.shields.io/badge/☕_Ko--fi-Apoya_al_equipo-FF5E5B?style=for-the-badge&labelColor=07080C)](https://ko-fi.com/desdelalinea)

</div>

---

## ¿Qué es? / What is it?

App de pronósticos en tiempo real para el **WUCC 2026** con leaderboard en vivo. Participantes de todo el mundo eligen ganadores en 3 divisiones — grupos, fase intermedia y championship bracket — y compiten por puntos.

Real-time bracket prediction app for **WUCC 2026** with a live global leaderboard. Participants worldwide pick winners across 3 divisions and compete for points.

---

## 🌐 [desdelalinea.github.io/wucc2026-predictor](https://desdelalinea.github.io/wucc2026-predictor/)

---

## ✨ Funcionalidades completas / Full Feature List

### Para participantes / For participants
| | |
|---|---|
| 🥏 | Open (48 eq.) · Mixed (48 eq.) · Women's (40 eq.) |
| 🔄 | Formato real WUCC — Cross-Pools, Play-ins y Championship bracket |
| 📊 | Grupos → Fase intermedia → Championship → 🕊️ Spirit — 4 fases por división |
| 🕊️ | **Spirit of the Game** — predicción extra: elige al equipo más espiritual de cada división (todos los equipos visibles) |
| ☁️ | Leaderboard en tiempo real — sin registro, solo nombre + email + país |
| 📊 | **Mis Picks vs Resultados** — compara partido a partido con ✅/❌ durante el torneo |
| 📤 | **Compartir predicción** — imagen 1080×1080 descargable para redes sociales |
| 🏳️ | **Leaderboard por filtros**: General · Por país · LATAM · Open · Mixed · Women's |
| 🌎 | **Ranking LATAM** — ¿qué país latinoamericano conoce más el Ultimate? |
| 🏅 | **Badges automáticas**: 👑 Elite · 🔥 Hot · ⭐ On fire · Especialistas por división · 🌎 LATAM |
| 🔒 | Picks bloqueados automáticamente el 15 agosto 9AM hora Irlanda |
| ⚠️ | Detección de nombre duplicado en tiempo real |
| 💾 | Modal de confirmación antes de guardar — muestra resumen por división |
| 🌙☀️ | Modo oscuro / claro |
| 📱 | Responsive — funciona en cualquier dispositivo |
| ☕ | Ko-fi — apoya al equipo periodístico directamente desde la app |

### Para el admin / For the admin
| | |
|---|---|
| 🔐 | Panel admin protegido con contraseña |
| 📋 | Ingreso de resultados por fase — Grupos · Fase intermedia · Bracket |
| 🎯 | **Campaña de sponsor** — configura nombre, código de descuento, URL y mensaje del modal de éxito |
| 📢 | **Banner de sponsor** en el header — activable/desactivable desde admin |
| 🤝 | Sección de sponsors/aliados — sube logos, se sincronizan en tiempo real |
| ⬇️ | **Exportar datos**: participantes+emails CSV, picks CSV, leaderboard CSV |
| ⏰ | Control manual de cierre/apertura de picks |

---

## 🔄 Formato por división / Tournament Format

### Open & Mixed — 48 equipos

```
8 grupos de 6  →  4°vs5° Play-in (8 partidos)  →  Round of 32
1°/2°/3° con bye directo       Ganador Play-in → R32     6° → Consolación
R32 (16 partidos) → R16 (8) → QF (4) → SF (2) → Final 🏆
```

### Women's — 40 equipos

```
8 grupos de 5  →  10 Cross-Pools I–R (round-robin de 4 equipos)
  Pools I-L (Top): 1°/2° → Pre-QF bye · 3°/4° → 16 Play-in
  Pools M-P (Mid): 1°/2° → 16 Play-in · 3°/4° → Consolación
  Pools Q-R (Bot): todos → Consolación
16 Play-in (8 partidos) → Pre-QF → QF → SF → Final 🏆
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

*Spirit of the Game: predicción extra sin puntos — solo por el amor al juego.*

---

## ⏰ Fecha límite / Deadline

**15 agosto 2026 · 9:00 AM hora Irlanda (UTC+1)**

Picks bloqueados automáticamente. El admin también puede forzar cierre/apertura manual desde el panel.

---

## 🚀 Para participantes / How to participate

1. Abre la app → escribe tu **nombre**, **email** (privado) y **país**
2. Selecciona una división (🔵 Open / 🟣 Mixed / 🌸 Women's)
3. Navega por las 4 fases: **📊 Grupos → ⚡ Fase intermedia → 🏆 Championship → 🕊️ Spirit**
4. Repite en las 3 divisiones
5. Clic en **☁️ Guardar en leaderboard** → apareces en el ranking en vivo
6. Durante el torneo: **📊 Mis vs Resultados** para seguir tus aciertos
7. **📤 Compartir** para generar imagen de tu predicción para redes

---

## 🛠️ Setup para el admin

Ver **[SETUP.md](SETUP.md)** — guía completa.

**Único paso:** abre `index.html`, busca `REEMPLAZA_CON_TU_API_KEY` y pega tus 6 credenciales de Firebase. Los usuarios no configuran nada.

---

## 💰 Modelo de monetización / Monetization

La app es **gratuita para usuarios** y se monetiza por el back:

- **Base de datos** — emails + países de jugadores activos de Ultimate en la región
- **Conversión medible** — códigos de descuento de sponsors con tracking exacto de usos
- **Exposición de marca** — banner en header + modal de éxito post-guardado
- **Ko-fi** — apoyo directo de la comunidad al equipo de Desde La Línea

---

## 📁 Archivos del repositorio

```
wucc2026-predictor/
├── index.html        ← App completa (todo en un archivo)
├── README.md         ← Este archivo
├── SETUP.md          ← Guía de configuración para el admin
├── HOW-TO-PLAY.html  ← Página de instrucciones para compartir
├── CONTRIBUTING.md   ← Cómo reportar bugs
├── LICENSE           ← MIT
└── .nojekyll         ← Necesario para GitHub Pages
```

---

## 📞 Contacto / Contact

**Desde La Línea** — Medio de Ultimate Frisbee en español

📧 [desdelalinea.tv@gmail.com](mailto:desdelalinea.tv@gmail.com)
📸 [@desdelalinea](https://instagram.com/desdelalinea) · 🎥 [YouTube](https://youtube.com/@desdelalinea)
☕ [Ko-fi](https://ko-fi.com/desdelalinea)

Resultados oficiales: **results.wucc2026.com** · 22 agosto 2026

---

MIT License · Desde La Línea 2026
