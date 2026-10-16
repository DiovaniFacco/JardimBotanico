<div align="center">

# 🌿 Jardim Botânico — UFSM

**A pocket guide to the Botanical Garden of UFSM.**

Plant map, opening hours, and visit scheduling — as an installable, offline-ready Progressive Web App.

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](#)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](#)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](#)
[![Leaflet](https://img.shields.io/badge/Leaflet-199900?logo=leaflet&logoColor=white)](#)
[![PWA](https://img.shields.io/badge/PWA-installable-5A0FC8?logo=pwa&logoColor=white)](#)

</div>

---

## 💡 The idea

Visitors to the **Jardim Botânico da UFSM**, in Santa Maria (RS), used to walk around with a paper map and guess where things were. This project turns that into an app: open it on your phone, see where every point of interest is, check the opening hours, and book a guided visit — all without downloading anything from an app store.

It's a **Progressive Web App**, so it installs straight from the browser, opens like a native app, and keeps working even with a weak connection.

## ✨ What it does

**🏠 Home** — a welcoming landing page with a photo carousel of the garden (`keen-slider` + `tiny-slider`) and a clear menu to every section.

**🗺️ Interactive map** — built with **Leaflet** over **OpenStreetMap** tiles. Points of interest (buildings, plant collections, leisure areas) come with name + description popups and load **live** from a Google Apps Script API, so the garden's staff can update locations in a spreadsheet and have them appear in the app.

**📍 "Where am I?" and walk recording** — the map uses the browser's geolocation to drop a red marker on your current position. You can also **start recording your visit**, watch your route drawn as a blue line in real time, and **export the whole track as a CSV** file.
Category toggles above the map let you focus on Edificações, Coleções or Lazer.

**📅 Visit scheduling** — a simple form to request a visit: name, e-mail, date, time and whether you'd like a **guide**.

**☎️ Contact & hours** — phone numbers, social links and the opening hours, so visitors don't have to call just to check.

**📲 Installable & offline** — a `manifest.json` and a service worker cache every page, stylesheet, script and photo. Installed on a phone, the garden guide is available in the middle of the garden — where the signal usually isn't.

## 🧱 Tech stack

| Layer | Choice |
| --- | --- |
| Markup & style | Vanilla HTML5 + CSS3 |
| Interactivity | Vanilla JavaScript |
| Map | Leaflet 1.7 + OpenStreetMap tiles |
| UI helpers | Bootstrap 5, Font Awesome, Keen/Tiny Slider |
| Map data | Google Apps Script + Google Sheets (JSON endpoint) |
| Offline / install | Service Worker + Web App Manifest |

No build step, no framework, no `node_modules` — it's plain web, and it just runs.

## 🚀 Running locally

Because it's a static site, any static server works. A service worker needs `http://` or `https://` — opening the files directly with `file://` won't register it.

```bash
# from inside the project folder
python3 -m http.server 8080
# then open http://localhost:8080/home.html
```

## 🎛️ Customizing

- **Points of interest:** they come from the Apps Script URL in `script.js` (`var url = '...'`). Point it at your own deployment/sheet to change the data.
- **Map starting point:** the coordinates passed to `map.setView(...)` in `script.js`.
- **Branding:** name, colors and icon live in `manifest.json` + `icon.png`; the slider photos are `jard1.jpg` … `jard7.jpg`.

## 📁 Project structure

```
├── home.html            # Landing page + photo carousel
├── Mapa.html            # Interactive map
├── agendamento.html     # Visit scheduling form
├── contato.html         # Contact & opening hours
├── script.js            # Map, markers, geolocation, track recording
├── styles*.css          # Per-page styles
├── manifest.json        # PWA metadata
├── service-worker.js    # Offline cache
└── jard1..7.jpg         # Garden photos
```

## 📌 Notes

- All user-facing content is in **Portuguese (pt-BR)**, since the garden's visitors are Brazilian.
- The map's POIs are fetched from an external Google Apps Script endpoint; if that endpoint is unavailable, the map still loads — only the markers won't appear.

## 👤 Author

**Diovani Facco** — [LinkedIn](https://www.linkedin.com/in/diovani-facco-3a247b11a/) · [diovanifacco@gmail.com](mailto:diovanifacco@gmail.com)
