# Gestor Integral Farmacias 💊

**Version:** 1.0.0  
Lightweight web application for pharmacy census browsing, technical auditing, and visit management.

---

## Features

- **Interactive Map:** Leaflet map with dark/satellite layer toggle, real-time search, service and visit status filters, and direct GPS navigation.
- **Client-Side Architecture:** Fast, zero-install web app with zero external backend dependencies required for standard usage.
- **Pharmacy Management:** Official collegiate codes, contact details, network structures, and peripheral tracking.
- **Hardware Auditing:** Scalable workstation setup for standalone or server-client configurations, with print-friendly output.
- **Visit Tracking & Global Timeline:** Chronological logging of visits per pharmacy and unified global timeline with filtering.
- **Storage & Persistence:** Optional Google Auth cloud sync via Firebase, plus local JSON import/export and ink-saving PDF printing.

---

## Privacy & 3-Tier Data Architecture

To ensure strict separation between public open-data census records, personal technician logs, and confidential corporate data, the application implements a 3-tier architecture:

### 1. Public Master Census (Neutral Catalog)
- **File:** `FarmaciasNavarra.js` / `FarmaciasNavarra.json`
- **Scope:** Minimal public pharmacy directory (`F00xxx` IDs, names, addresses, municipalities, zones, and GPS coordinates).
- **Privacy:** Contains zero commercial or proprietary client data, making the repository completely safe for public hosting and usable out-of-the-box by any independent user.
- **Protection:** Master fields are read-only by default and protected via an administrator lock verified against a one-way **SHA-256** cryptographic hash.

### 2. Private User Data (Personal Visit Logs)
- **Scope:** Technician identity and chronological visit records (`visitas`).
- **Persistence:** Stored privately under each authenticated user's document in Firebase Firestore (`usuarios_datos/{uid}`) or managed offline via local `*.json` files.
- **Privacy:** Strictly isolated per user account; standard Google login only accesses the user's own visit history.

### 3. Corporate Enterprise Overlay (Protected Cloud Layer)
- **Scope:** Full pharmacy records and commercial/technical data (phones, emails, CIFs, Distribution & IT client flags, internal client codes, installed management software, primary distributor, purchasing groups, shared observations, and hardware audits).
- **Persistence:** Stored client-side encrypted (**AES-GCM** / PBKDF2) in Firebase Firestore (`empresa_datos/navarra`) when online, or exported/loaded offline via a single unified local `*.json` file (`Guardar` / `Abrir / Cargar`)—never in the public source code or static catalog files.
- **Access Control:** Toggled via the top bar `Empresa` button (works both with Google Auth and offline for local JSON work) and validated client-side via a **SHA-256** hash. Bottom action buttons (`Abrir / Cargar`, `Guardar`, `Limpiar`, `PDF / Imprimir`) remain disabled unless **Empresa** mode is active.

---

## Third-Party & Attributions

- **[Leaflet.js](https://leafletjs.com/):** Open-source JavaScript library for interactive web maps.
- **Map Tiles & Data:** &copy; [Esri ArcGIS](https://www.esri.com/) (World Dark Gray & World Imagery).

---

## Languages

- **Interface:** Spanish (`es`)
- **Code Comments & Documentation:** English (`en`)

---

## Usage

- **Online App:** Access the live web app directly via [GestorIntegralFarmacias Online](https://lantegia.github.io/GestorIntegralFarmacias/) to use cloud sync features.
- **Local:** Open `index.html` in any modern web browser. *Note: When running locally without Google Auth, data is loaded and saved via local JSON files.*

---

## License

GNU General Public License v3.0 (GPL-3.0-or-later)

---

## Credits

Original idea by [Zuhaitz (Alberto V. I.)](https://www.aiurri.xyz), created with Google Antigravity and VSCodium.  
All projects by Zuhaitz on [GitHub](https://github.com/zuhaitz-arbola).
