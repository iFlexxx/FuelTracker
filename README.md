# ⛽ FuelTracker PWA

Application iPhone/Android de suivi de carburant — E85, SP95, mélange, économies.

## Fichiers

```
index.html          ← Application principale
manifest.json       ← Config PWA
sw.js               ← Service Worker (mode hors-ligne)
icon-192.png        ← Icône app 192×192
icon-512.png        ← Icône app 512×512
apple-touch-icon.png ← Icône iPhone (180×180)
```

## Déploiement sur GitHub Pages

1. Crée un nouveau dépôt GitHub (ex: `fueltracker`)
2. Upload tous ces fichiers à la racine du dépôt
3. Va dans **Settings → Pages**
4. Source : **Deploy from a branch** → `main` → `/ (root)` → Save
5. Ton app sera disponible sur `https://TON_USERNAME.github.io/fueltracker/`

## Installer en PWA sur iPhone

1. Ouvre l'URL dans **Safari** (pas Chrome)
2. Tap l'icône **Partager** (carré avec flèche)
3. **"Sur l'écran d'accueil"**
4. L'app s'installe comme une vraie appli native 🎉

## Fonctionnalités

- 🚗 Gestion multi-véhicules (marque, modèle, année, réservoir, conso officielle, surconso E85)
- ⛽ Enregistrement de pleins (E85, SP95, mixte)
- ⚗️ Calculateur de mélange en temps réel (ratio E85 configurable par saison)
- 📷 Photo ticket de caisse + analyse IA automatique (Claude)
- 📊 Dashboard : dépenses, km, conso moyenne, coût/km
- 🌿 Calcul des économies E85 vs 100% SP95
- 📅 Filtres par mois
- 💾 Données stockées localement (localStorage)
- 📶 Mode hors-ligne (Service Worker)
