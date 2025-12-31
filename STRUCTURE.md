# 📁 Structure du Repository Statique

Ce document explique la structure des fichiers et leur rôle dans le repository statique GitHub Pages.

## 📂 Structure des Dossiers

```
static-repo/
├── index.html              # Formulaire d'installation (à la racine)
├── admin/                  # Interface d'administration
│   ├── index.html          # Page de connexion
│   ├── dashboard.html      # Dashboard principal
│   └── ide.html            # IDE intégré (Monaco Editor)
├── core/                   # Scripts JavaScript essentiels
│   ├── admin.js            # Logique du dashboard admin
│   ├── frontend.js          # Utilitaires frontend
│   ├── ide-context.js      # Logique de l'IDE
│   └── WhatsappChatBox.min.js  # Widget WhatsApp
├── static/                 # Assets statiques (optionnel)
│   ├── js/                 # Bibliothèques JavaScript
│   ├── css/                # Styles CSS
│   └── fonts/              # Polices
├── .github/                # GitHub Actions workflows
│   └── workflows/
│       ├── sync-vars.yml   # Workflow de synchronisation des variables
│       └── README.md       # Documentation des workflows
├── README.md               # Documentation utilisateur
├── INSTRUCTIONS.md         # Guide de déploiement
├── QUICK-START.md          # Guide rapide
├── STRUCTURE.md            # Explication de la structure
├── CHECKLIST.md            # Checklist de déploiement
├── .gitignore              # Fichiers à ignorer
└── .nojekyll               # Désactive Jekyll
```

## 🎯 Rôle de Chaque Fichier

### `index.html` (Racine)
- **Rôle** : Formulaire d'installation initial
- **Fonction** : Permet à l'utilisateur de configurer et installer WebSuite Platform
- **Détection automatique** : Username et repo GitHub depuis l'URL
- **Après installation** : Sauvegarde `api_base_url` dans localStorage

### `admin/index.html`
- **Rôle** : Page de connexion au dashboard
- **Fonction** : Authentification de l'administrateur
- **Comportement** : 
  - Utilise `/api/login` (chemin relatif)
  - Si `api_base_url` est défini dans localStorage, les appels vont vers le Worker
  - Sinon, utilise les chemins relatifs (mode local)

### `admin/dashboard.html`
- **Rôle** : Dashboard principal de l'administration
- **Fonction** : Gestion du contenu, agents IA, configuration
- **Comportement** :
  - Utilise `buildApiUrl()` de `core/admin.js`
  - Redirige automatiquement vers le Worker si `api_base_url` est défini
  - Lien vers l'IDE intégré (`/admin/ide.html`)

### `admin/ide.html`
- **Rôle** : IDE intégré (Monaco Editor)
- **Fonction** : Édition de code, création de pages, déploiement GitHub
- **Comportement** :
  - Utilise Monaco Editor (CDN)
  - Gère les templates et pages frontend
  - Déploiement automatique vers GitHub

### `core/admin.js`
- **Rôle** : Logique JavaScript du dashboard
- **Fonction** : 
  - Gestion de l'authentification
  - Appels API (avec support Worker distant)
  - Gestion du dark mode
  - Fonction `buildApiUrl()` pour router les appels API

### `core/frontend.js`
- **Rôle** : Utilitaires frontend
- **Fonction** : Fonctions utilitaires pour le frontend
- **Utilisation** : Utilisé par les pages frontend et l'IDE

### `core/ide-context.js`
- **Rôle** : Logique de l'IDE
- **Fonction** : Gestion de l'éditeur, templates, déploiement
- **Utilisation** : Utilisé par `admin/ide.html`

### `core/WhatsappChatBox.min.js`
- **Rôle** : Widget WhatsApp Business
- **Fonction** : Intégration du chat WhatsApp
- **Utilisation** : Utilisé par `admin/dashboard.html`

### `.github/workflows/sync-vars.yml`
- **Rôle** : Workflow GitHub Actions pour synchroniser les variables
- **Fonction** : 
  - Synchronise les variables depuis GitHub Secrets vers le Cloudflare Worker
  - Déclenché automatiquement par le Worker Maître lors de l'installation
  - Peut être déclenché manuellement depuis GitHub Actions
- **Note** : Ce fichier est créé automatiquement par le Worker Maître, mais inclus ici comme template/reference

## 🔄 Flux Après Installation

### 1. Installation (index.html)
```
Utilisateur remplit le formulaire
  ↓
Worker Maître crée le Worker client
  ↓
api_base_url sauvegardé dans localStorage
  ↓
Redirection vers /admin
```

### 2. Connexion Admin (admin/index.html)
```
Utilisateur se connecte
  ↓
Appel à /api/login
  ↓
Si api_base_url existe → Appel vers Worker
  ↓
Sinon → Appel relatif (mode local)
```

### 3. Dashboard (admin/dashboard.html)
```
Dashboard chargé
  ↓
core/admin.js utilise buildApiUrl()
  ↓
Tous les appels API vont vers le Worker
  ↓
Worker sert le bundle depuis UNPKG
```

## 📝 Fichiers Statiques (Optionnel)

Les fichiers dans `static/` sont **optionnels** car :
- Le Worker Cloudflare sert le bundle complet depuis UNPKG
- Les assets peuvent être chargés depuis CDN
- GitHub Pages peut servir les fichiers statiques si présents

### Si vous incluez `static/` :

```bash
# Copier les assets essentiels
cp -r /chemin/vers/ProdBeta/static/js static/
cp -r /chemin/vers/ProdBeta/static/css static/
cp -r /chemin/vers/ProdBeta/static/fonts static/
```

### Assets CDN (Alternative)

Les fichiers admin utilisent des CDN pour :
- Tailwind CSS : `/static/js/tailwindcss.js` (peut être remplacé par CDN)
- Font Awesome : `/static/css/all.min.css` (peut être remplacé par CDN)
- Inter Font : `/static/fonts/inter.css` (peut être remplacé par CDN)

## ⚙️ Configuration

### Avant Déploiement

1. **Mettre à jour `MAITRE_URL`** dans `index.html` ligne ~194
2. **Vérifier les chemins** dans `admin/index.html` et `admin/dashboard.html`
3. **Optionnel** : Copier les assets statiques dans `static/`

### Après Installation

- Les appels API utilisent automatiquement le Worker
- Le Worker sert tout le code depuis le bundle UNPKG
- GitHub Pages sert uniquement les fichiers HTML statiques

## 🚀 Déploiement Minimal

**Minimum requis** :
- ✅ `index.html` (racine)
- ✅ `admin/index.html`
- ✅ `admin/dashboard.html`
- ✅ `admin/ide.html`
- ✅ `core/admin.js`
- ✅ `core/frontend.js`
- ✅ `core/ide-context.js`
- ✅ `core/WhatsappChatBox.min.js`
- ✅ `.nojekyll`

**Optionnel** :
- `static/` (assets) - Peut être remplacé par CDN
- `frontend/` - Non nécessaire, le Worker gère le frontend

## 💡 Notes

- Le frontend principal est servi par le Worker (bundle UNPKG)
- Les fichiers admin dans le repo statique permettent l'accès initial
- Après installation, tout fonctionne via le Worker Cloudflare
- Les assets peuvent être chargés depuis CDN pour réduire la taille du repo

