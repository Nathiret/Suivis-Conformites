[README.md](https://github.com/user-attachments/files/35280921/README.md)
# T.I.S – Suivi Conformités

Application web progressive (PWA) de suivi des chantiers de conformité électrique pour **Tech-Immo Services**.

🔗 **Application** : [nathiret.github.io/Suivis-Conformites](https://nathiret.github.io/Suivis-Conformites/)

---

## Présentation

Outil interne utilisé par les techniciens de Tech-Immo Services pour suivre l'avancement des chantiers de conformité électrique (RGIE). Il remplace un suivi manuel sur Google Sheets en offrant une interface mobile optimisée, accessible depuis l'écran d'accueil de l'iPhone.

---

## Fonctionnalités

- **Trois vues** : Tableau (tri multi-colonnes), Fiches, Contrôles (regroupés par date)
- **Filtres** : Statut, Technicien, Type, Contrôle, Étiquettes, Influences extérieures, Recherche texte, « Mes chantiers »
- **Fiche chantier** : Google Maps, Waze, bouton Appeler, modification en ligne avec calendrier et sélecteur d'heure
- **Connexion par technicien** avec rôles (Écriture / Lecture), jetons de session sécurisés (HMAC, 60 jours), verrouillage anti-brute force
- **Protection des lignes** : vérification du nom du chantier avant chaque écriture pour éviter les conflits
- **Ouverture instantanée** via cache local (localStorage), synchronisation automatique toutes les 3 minutes
- **PWA** : icône TIS, nom « Suivi Confo. », plein écran iPhone, zones encoche/barre home respectées

---

## Architecture technique

| Composant | Technologie |
|---|---|
| Frontend | HTML / CSS / JS (fichier unique `index.html`) |
| Hébergement | GitHub Pages |
| Backend | Google Apps Script (Web App) |
| Données | Google Sheets (onglet « Conformités » + onglet « Accès ») |
| Communication | GET uniquement (évite les blocages CORS) |

Le frontend communique avec l'Apps Script via des requêtes GET avec les paramètres `action`, `token`, `row`, `expect` et `payload`.

---

## Fichiers du dépôt

```
index.html               # Application complète (HTML + CSS + JS)
manifest.webmanifest     # Manifeste PWA
apple-touch-icon.png     # Icône iOS
icon-192.png             # Icône PWA 192×192
icon-512.png             # Icône PWA 512×512
icon-maskable-512.png    # Icône PWA maskable
```

---

## Mise à jour

### Mettre à jour le site

1. Dépôt → **Add file → Upload files**
2. Glisser les fichiers modifiés (même nom = remplacement automatique)
3. Ajouter un message de commit → **Commit changes**
4. Attendre 1–2 minutes, puis actualiser l'application

### Mettre à jour l'Apps Script

1. Coller le nouveau code → **Enregistrer**
2. **Déployer → Gérer les déploiements** → sélectionner le déploiement existant → **✏️**
3. Choisir **« Nouvelle version »** → **Déployer**
4. ⚠️ Ne jamais utiliser « Nouveau déploiement » (cela crée une nouvelle URL)

> Si Code.gs **et** index.html changent : mettre à jour l'Apps Script **en premier**.

---

## Usage interne

Cet outil est réservé aux techniciens de Tech-Immo Services. Les accès (identifiant + code) sont gérés dans l'onglet **Accès** du Google Sheet associé.

---

*Développé pour Tech-Immo Services – Belgique*
