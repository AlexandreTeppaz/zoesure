# ZOESURE ZF319 — Web Bluetooth Controller

Interface web minimaliste permettant de contrôler un ou deux projecteurs LED **ZOESURE Smart Flood Light (modèle ZF319)** directement depuis un navigateur compatible **Web Bluetooth**, sans avoir besoin de l'application mobile officielle (désormais hors service) ni d'ouvrir le boîtier.

---

## Fonctionnalités

- **Contrôle individuel ou synchronisé :** Connexion simultanée de deux panneaux (`Panneau 1`, `Panneau 2`) avec sélection de cible (`Panneau 1`, `Panneau 2` ou `Les deux` par défaut).
- **Alimentation :** Allumage et extinction instantanés.
- **Couleurs RGB :** Sélecteur de couleur complet (16 millions de couleurs) et palette d'accès rapide.
- **Luminosité & Blanc (CCT) :** Réglage de l'intensité lumineuse (1 à 100 %) et balance entre blanc chaud et blanc froid.
- **Animations intégrées :** Modes dynamiques calculés en temps réel (**Arc-en-ciel**, **Respiration**, **Gyrophare**) avec contrôle de la vitesse.
- **100 % client-side :** Aucun serveur backend requis ; les commandes transitent directement entre le navigateur et les projecteurs via BLE.

---

## Matériel compatible

- **Marque :** ZOESURE
- **Modèle :** ZF319 (`Smart Flood Light 50W`)
- **FCC ID :** `2A5K7-WRD36WRGBCCT`
- **Nom Bluetooth diffusé :** `ZF319-XXXX`

---

## Prérequis et compatibilité navigateurs

L'API **Web Bluetooth** nécessite impérativement un contexte sécurisé (**HTTPS** ou `localhost`).

- **Android :** Google Chrome, Microsoft Edge, Brave (Bluetooth et localisation activés).
- **Desktop (Windows / macOS / Linux) :** Google Chrome, Microsoft Edge.
- **iOS / iPadOS :** Safari ne supporte pas nativement Web Bluetooth (nécessite un navigateur tiers compatible comme *Bluefy*).

---

## Déploiement et utilisation

### 1. Hébergement via GitHub Pages
1. Déposez le fichier `index.html` à la racine de votre dépôt GitHub.
2. Rendez-vous dans **Settings > Pages**.
3. Sous **Branch**, sélectionnez `main` (dossier `/ (root)`) et cliquez sur **Save**.
4. Ouvrez l'URL HTTPS générée (`https://<utilisateur>.github.io/<depot>/`) sur votre téléphone ou PC.

### 2. Utilisation en local
```bash
# Lancer un serveur HTTP local sur le port 8000
python -m http.server 8000
