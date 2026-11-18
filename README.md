# 💡 ZOESURE — Web Bluetooth Controller

![Status](https://img.shields.io/badge/Statut-Op%C3%A9rationnel-2ea44f?style=for-the-badge)
![Bluetooth](https://img.shields.io/badge/Web_Bluetooth-BLE-0082FC?style=for-the-badge&logo=bluetooth&logoColor=white)<br>
![Tested](https://img.shields.io/badge/Test%C3%A9_sur-ZOESURE_ZF319-FF4500?style=for-the-badge)
![License](https://img.shields.io/badge/Usage-Personnel_%26_Gratuit-111111?style=for-the-badge)

Application web minimaliste permettant de contrôler un ou plusieurs projecteurs LED **ZOESURE Smart Flood Light** directement depuis votre navigateur via **Web Bluetooth**, en remplacement de l'application mobile officielle hors service.

> [!TIP]
> **Aucune installation ni téléchargement requis** : tout fonctionne directement en ligne en cliquant sur **[ouvrir l'interface ZOESURE Control](https://alexandreteppaz.github.io/zoesure/)**.

---

## 🌐 Accéder à l'application

👉 **[Accéder à l'interface ZOESURE Control](https://alexandreteppaz.github.io/zoesure/)**

### Compatibilité des appareils et navigateurs

| Plateforme | Navigateurs supportés | Remarques |
| :--- | :--- | :--- |
| 🟢 **Android** | Chrome, Edge, Brave | Activer le **Bluetooth** et la **Localisation** |
| 🟢 **Windows / Mac / Linux** | Chrome, Edge | Bluetooth requis sur l'ordinateur |
| 🟡 **iOS / iPadOS** | *Bluefy* (App Store) | Safari ne supporte pas nativement Web Bluetooth |

### Modèles ZOESURE compatibles
* ✅ **Confirmé et testé :** **ZOESURE ZF319** (*Smart Flood Light 50W* — testé en conditions réelles, 100 % fonctionnel).
* 🔄 **Autres modèles ZOESURE (`ZF-...`, `ZT-...`) :** Non testés physiquement, mais l'interface intègre les deux profils Bluetooth (`0x0929` et `0xFFE0`) extraits de l'application officielle — cela devrait donc fonctionner sur l'ensemble de la gamme.

---

## 🔗 Comment connecter vos projecteurs

1. Branchez vos projecteurs LED sur le secteur.
2. Cliquez sur **[ouvrir l'interface en ligne](https://alexandreteppaz.github.io/zoesure/)** depuis votre navigateur.
3. Dans le premier encadré, cliquez sur **Connecter** à droite de **Panneau 1**.
4. Dans la fenêtre Bluetooth qui s'ouvre, sélectionnez votre projecteur (son nom ressemble généralement à **`ZF319-4B56`**, **`ZF-XXXX`** ou **`ZT-XXXX`**).
5. *(Optionnel)* Cliquez sur **`[+]`** en haut à droite pour ajouter d'autres panneaux (`Panneau 2`, `Panneau 3`...) et connectez-les de la même manière.

> [!NOTE]
> Pour des raisons de sécurité imposées par les navigateurs web, la connexion Bluetooth est coupée à chaque actualisation de la page. Il faut donc cliquer sur **Connecter** pour resélectionner vos panneaux après un rechargement. Vos noms et le nombre de panneaux créés restent quant à eux enregistrés.

---

## 🎛️ Guide des boutons et contrôles

### ➕ Gestion des panneaux (en haut)
* **`[+]` :** Ajoute un nouveau panneau à votre liste (`Panneau 2`, `Panneau 3`, etc.).
* **Nom du panneau :** Cliquez directement sur `Panneau 1` pour le renommer (ex. *Salon*, *Jardin*, *Mur*). Sauvegardé automatiquement dans votre navigateur.
* **`×` :** Supprime un panneau ajouté.
* **`?` :** Réaffiche l'aide rapide en 4 étapes.

### 🎯 Cible du contrôle
* **Tous** *(sélectionné par défaut)* : Envoie vos commandes simultanément et de façon synchronisée à tous les panneaux connectés.
* **[Nom du panneau] :** Permet d'isoler et de piloter un seul panneau indépendamment des autres.

### ⚡ Alimentation & Couleurs
* **Allumer / Éteindre :** Contrôle l'alimentation des projecteurs ciblés.
* **Sélecteur de couleur :** Ouvre la palette complète (16 millions de couleurs RGB).
* **Carrés de couleur :** Raccourcis directs (🔴 Rouge, 🟠 Orange, 🟡 Jaune, 🟢 Vert, 🔵 Bleu, 🟣 Violet).

### ☀️ Luminosité & Blanc (CCT)
* **Luminosité :** Règle l'intensité de `1 %` à `100 %`.
* **Blanc Chaud / Froid :** Passe en éclairage blanc pur et ajuste la température entre blanc chaud (`0 %`) et blanc froid (`100 %`).

### ✨ Animations
* **Arc-en-ciel :** Défilement fluide de tout le spectre de couleurs.
* **Respiration :** Variation progressive de l'intensité sur la couleur sélectionnée.
* **Gyrophare :** Alternance flash rouge et bleu.
* **Vitesse :** Ajuste la cadence de l'animation en cours.

> [!IMPORTANT]
> Les animations sont calculées en temps réel par la page web. Votre téléphone ou PC doit donc rester à proximité et connecté en Bluetooth aux panneaux LED pour que l'animation continue de tourner.

---

## 🛠️ Spécifications techniques (Reverse Engineering BLE)

L'application communique sans chiffrement sur les profils GATT suivants :

* **Profil principal (ZF319) :** Service `0x0929` — Characteristic Write `0x1224`
* **Profil secondaire (autres modèles) :** Service `0xFFE0` — Characteristic Write `0xFFE1`

| Action | Trame Hexadécimale | Détail des octets |
| :--- | :--- | :--- |
| **Allumer** | `01 04 02 01` | Commande fixe |
| **Éteindre** | `01 04 02 00` | Commande fixe |
| **Couleur RGB** | `01 04 0A 01 RR GG BB` | `RR`, `GG`, `BB` : `0x00` à `0xFF` |
| **Luminosité** | `01 04 03 VV` | `VV` : `0x01` (1 %) à `0x64` (100 %) |
| **Blanc CCT** | `01 04 04 00 WW CC` | `WW` chaud (`0x00`–`0xFF`), `CC` froid (`255 - WW`) |

---

## 👤 Auteur & Licence

Projet développé et mis à disposition gratuitement par **Alex** pour aider les utilisateurs des projecteurs ZOESURE suite à l'arrêt de l'application officielle.  
Utilisation personnelle libre — **toute appropriation ou revente commerciale de ce code est interdite.**
