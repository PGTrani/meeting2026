# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Landing page statica per il **XIX Meeting Giovanissimi "MeTeenGo"** (Aprile 2026) della Pastorale Giovanile dell'Arcidiocesi Trani-Barletta-Bisceglie. Bundled con Webpack 5, pensata per hosting su GitHub Pages (nessun backend).

La pagina offre 3 bottoni principali che puntano a risorse Google Drive (Note Tecniche, Form di Iscrizione, Regolamento Contest) e un link secondario per la locandina A4 stampabile.

## Commands

- **Dev server**: `npm start` — webpack-dev-server con live reload e HMR
- **Production build**: `npm run build` — output in `dist/`
- **No test runner configurato**

Installare dipendenze con `npm install` prima di qualsiasi comando.

## Architecture

- **Entry point**: `js/app.js` → bundled in `dist/js/app.js`
- **HTML**: `index.html` — pagina singola con hero, 3 action buttons e footer
- **Styles**: `css/style.css` — CSS custom (no preprocessor), copiato in dist
- **Loghi**: `img/logo-pastorale.jpg`, `img/logo-diocesi.png` — mostrati nell'header
- **Static assets**: `img/`, `icon.svg`, `favicon.ico`, `icon.png`, `robots.txt`, `site.webmanifest`, `404.html` — copiati in `dist/` via CopyWebpackPlugin
- **Font**: Nunito da Google Fonts (caricato via CDN)

## Webpack Configuration

Tre file con `webpack-merge`:
- `webpack.common.js` — entry/output condiviso
- `webpack.config.dev.js` — dev server, inline source maps, serve dalla root
- `webpack.config.prod.js` — production mode, HtmlWebpackPlugin, CopyWebpackPlugin

## Editing Links

I link Google Drive nei 3 bottoni e nel link locandina sono placeholder (`href="#"`) in `index.html`. Sostituire con gli URL definitivi.

## Resources

La cartella `resources/` contiene materiali di riferimento (locandina PNG, presentazione DOCX, regolamento PDF, loghi) — non fanno parte del build web.
