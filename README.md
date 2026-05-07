# Audomarois Data — Infrastructure

## Architecture

```
GitHub Repository
├── index.html          ← Votre site (audomarois-data.html renommé)
├── data.json           ← Données générées automatiquement chaque nuit
├── fetch_data.py       ← Script de collecte (tourne via GitHub Actions)
└── .github/
    └── workflows/
        └── update-data.yml  ← Planification nocturne
```

## Sources utilisées

| Source | Données | Auth requise |
|--------|---------|-------------|
| [INSEE BDM](https://api.insee.fr) | Chômage localisé, population | Clé gratuite |
| [Recherche-Entreprises](https://recherche-entreprises.api.gouv.fr) | Créations SIRENE | ❌ Aucune |
| [France Travail Open Data](https://francetravail.io) | Offres d'emploi | Clé gratuite |
| [data.gouv.fr](https://www.data.gouv.fr) | Fichiers CSV INSEE | ❌ Aucune |

## Mise en place (30 minutes)

### 1. Créer le dépôt GitHub
```
github.com → New repository → "audomarois-data" → Public
```

### 2. Pousser les fichiers
```bash
git init
git add .
git commit -m "Premier déploiement"
git remote add origin https://github.com/VOTRE_LOGIN/audomarois-data.git
git push -u origin main
```

### 3. Activer GitHub Pages
```
Settings → Pages → Source: "Deploy from branch" → Branch: main → /root
```
Votre site sera disponible sur : `votre-login.github.io/audomarois-data`

### 4. Obtenir les clés API (optionnel — améliore la qualité des données)

**INSEE** (gratuit, instantané) :
→ https://api.insee.fr/catalogue/ → Créer un compte → Applications → Nouvelle application

**France Travail** (gratuit, 24h) :
→ https://francetravail.io/data/api → S'inscrire → Créer une application

Ajouter les clés dans : Settings → Secrets → Actions → New secret

### 5. Nom de domaine personnalisé (optionnel)
Achetez `audomarois-data.fr` sur OVH (~10€/an)
Settings → Pages → Custom domain → audomarois-data.fr

## Mise à jour manuelle
Actions → "Mise à jour des données économiques" → Run workflow
