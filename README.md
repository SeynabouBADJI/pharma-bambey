# PharmaGarde Bambey — Structure React

## Stack
- **React 18** + React Router v6
- **Axios** pour les appels API
- **Leaflet / React-Leaflet** pour la carte interactive
- **React-Toastify** pour les notifications
- **Spring Boot** (backend — port 8080)

---

## Arborescence du projet

```
pharma-bambey/
├── .env                          # REACT_APP_API_URL=http://localhost:8080/api
├── package.json
├── public/
│   └── index.html
└── src/
    ├── App.js                    # Router principal + layout global
    ├── index.js
    │
    ├── services/
    │   └── api.js                # Axios instance + tous les appels API
    │                               (pharmacieService, medicamentService,
    │                                stockService, gardeService, authService)
    │
    ├── hooks/
    │   └── index.js              # useGarde | usePharmacie | useMedicament
    │
    ├── pages/
    │   ├── HomePage.js           # Page d'accueil (hero + stats + grille)
    │   ├── PharmaciesPage.js     # Liste de toutes les pharmacies
    │   ├── GardePage.js          # Planning de garde (calendrier)
    │   ├── MedicamentsPage.js    # Recherche de médicaments
    │   ├── StockPage.js          # Gestion du stock (admin)
    │   ├── LoginPage.js          # Formulaire de connexion
    │   └── NotFoundPage.js       # Page 404
    │
    ├── components/
    │   ├── layout/
    │   │   ├── Navbar.js         # Barre de navigation + menu mobile
    │   │   └── Footer.js
    │   │
    │   ├── common/
    │   │   ├── StatsBanner.js    # 3 chiffres clés sur une ligne
    │   │   ├── PrivateRoute.js   # Garde-route JWT pour pages admin
    │   │   └── Spinner.js
    │   │
    │   ├── garde/
    │   │   └── GardeList.js      # Cartes pharmacies de garde du jour
    │   │
    │   ├── medicaments/
    │   │   ├── StockTable.js     # Tableau médicaments + barres de stock
    │   │   └── AlerteStock.js    # Bandeau d'alerte stock bas
    │   │
    │   └── map/
    │       └── MapView.js        # Carte Leaflet centrée sur Bambey
    │
    └── styles/
        └── index.css             # Styles globaux (palette verte #0B5C3D)
```

---

## Routes

| Route          | Accès  | Description                        |
|----------------|--------|------------------------------------|
| `/`            | Public | Page d'accueil                     |
| `/pharmacies`  | Public | Liste complète des pharmacies      |
| `/garde`       | Public | Planning de garde / calendrier     |
| `/medicaments` | Public | Recherche de médicaments           |
| `/stock`       | Admin  | Gestion des stocks (JWT requis)    |
| `/login`       | Public | Connexion administrateur           |

---

## Appels API vers Spring Boot

| Service            | Endpoint                          | Méthode |
|--------------------|-----------------------------------|---------|
| Pharmacies de garde | `/api/pharmacies/garde`          | GET     |
| Toutes pharmacies  | `/api/pharmacies`                 | GET     |
| Stock médicaments  | `/api/medicaments`                | GET     |
| Alertes stock bas  | `/api/medicaments/alertes`        | GET     |
| Recherche méd.     | `/api/medicaments/search?q=...`   | GET     |
| Garde du jour      | `/api/gardes?date=YYYY-MM-DD`     | GET     |
| Connexion          | `/api/auth/login`                 | POST    |

---

## Démarrage

```bash
# Installer les dépendances
npm install

# Lancer en développement (Spring Boot doit tourner sur :8080)
npm start
```
