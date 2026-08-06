# Carnet de bord — v2

Suivi des pleins, de la consommation et des coûts, pour plusieurs véhicules.
Application web autonome (un seul fichier HTML), installable sur iPhone/Android, **100 % hors ligne**.

---

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | L'application entière (HTML + CSS + JS) |
| `manifest.json` | Nom, icônes, mode plein écran |
| `sw.js` | Service worker : fonctionnement hors ligne |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | Icônes |

---

## Mise en ligne sur GitHub Pages

1. Créer un dépôt (par ex. `carnet`) et y déposer les 6 fichiers **à la racine**.
2. Settings → Pages → Source : `main` / `root` → Save.
3. L'URL sera `https://iflexxx.github.io/FuelTracker/`.

## Installation sur iPhone

1. Ouvrir l'URL dans **Safari** (obligatoire, pas Chrome).
2. Bouton Partager → **Sur l'écran d'accueil**.
3. L'app se lance en plein écran, sans barre d'adresse, et fonctionne sans réseau.

---

## Comment la consommation est calculée

Méthode **plein-à-plein**, la seule fiable :

- La consommation d'un segment = tout le carburant ajouté entre deux **pleins complets**, divisé par la distance entre ces deux pleins.
- Un **appoint** (10 L en vitesse, sans faire le plein) compte dans le litrage du segment en cours sans le clôturer : la conso tombera au prochain plein complet, en incluant ces litres. Le relevé du compteur y est facultatif.
- L'interrupteur **« J'ai oublié un plein avant »** casse la chaîne : le calcul repart proprement à partir de ce plein, sans fausser la moyenne.

Conséquence : il faut **deux pleins complets** avant de voir la première consommation.

## Saisie du compteur

Deux modes, au choix à chaque plein :

- **Compteur total** — la valeur lue au tableau de bord (ex. 187 240).
- **Km parcourus** — le trip remis à zéro au plein précédent (ex. 620).

Dans les deux cas, la valeur absolue est stockée : les deux modes sont mélangeables sans risque. Un garde-fou prévient si le compteur recule ou si la distance dépasse 8 000 km.

## Quantité et prix

Trois champs : litres, €/L, total. Il suffit d'en remplir **deux**, le troisième se calcule. La virgule décimale française est acceptée partout.

---

## Statistiques calculées

- Consommation moyenne, du dernier plein, meilleure et pire (L/100 km)
- Écart avec la consommation annoncée du constructeur
- Coût du carburant au km et aux 100 km
- Coût de revient tout compris (carburant + dépenses) au km
- Total dépensé, litres, distance suivie, prix moyen du litre
- Litre le moins / le plus cher, avec la station
- Nombre de pleins, jours moyens entre deux pleins, litres par plein
- Kilométrage mensuel et annuel, budget projeté sur 12 mois *(après ~6 semaines de suivi)*
- Autonomie théorique sur un plein (d'après la capacité du réservoir)
- Graphiques : conso par plein, prix du litre dans le temps, dépenses par mois
- Dépenses hors carburant réparties par catégorie

---

## Données

Tout est stocké dans le `localStorage` du navigateur, sur l'appareil. Rien ne part sur un serveur, aucun compte, aucun suivi.

- **Exporter une sauvegarde (.json)** — sauvegarde complète, restaurable.
- **Exporter les pleins (.csv)** — ouvrable dans Excel/Numbers (séparateur `;`, encodage UTF-8 avec BOM).
- **Restaurer une sauvegarde** — remplace les données actuelles.
- **Récupérer les données de FuelTracker v1** — bouton visible uniquement si les clés `ft_fillups` / `ft_vehicles` de la v1 existent sur la même origine (même compte GitHub Pages).

⚠️ Supprimer l'app de l'écran d'accueil ou vider les données Safari efface tout. Exportez une sauvegarde de temps en temps.

## Mise à jour de l'app

Après avoir modifié `index.html`, changez la constante `CACHE` dans `sw.js` (ex. `carnet-v2.0.1`), sinon l'ancienne version reste en cache.
