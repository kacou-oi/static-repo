# ✅ Checklist de Déploiement

Checklist complète pour déployer le repository statique sur GitHub Pages.

## 📋 Avant de Commencer

- [ ] Avoir un compte GitHub
- [ ] Avoir un repository GitHub (vide ou existant)
- [ ] Avoir un GitHub Personal Access Token avec permissions : `repo`, `workflow`, `write:packages`

## 📁 Fichiers Inclus

Vérifiez que tous les fichiers suivants sont présents :

### Fichiers Essentiels
- [ ] `index.html` (à la racine)
- [ ] `admin/index.html`
- [ ] `admin/dashboard.html`
- [ ] `admin/ide.html`
- [ ] `core/admin.js`
- [ ] `core/frontend.js`
- [ ] `core/ide-context.js`
- [ ] `core/WhatsappChatBox.min.js`
- [ ] `.nojekyll`
- [ ] `.gitignore`

### Documentation
- [ ] `README.md`
- [ ] `INSTRUCTIONS.md`
- [ ] `QUICK-START.md`
- [ ] `STRUCTURE.md`
- [ ] `CHECKLIST.md` (ce fichier)

### GitHub Actions
- [ ] `.github/workflows/sync-vars.yml`
- [ ] `.github/workflows/README.md`

### Optionnel
- [ ] `static/` (assets) - Peut être ajouté plus tard ou utiliser CDN

## ⚙️ Configuration

### 1. Mettre à jour l'URL du Worker Maître

- [ ] Ouvrir `index.html`
- [ ] Trouver la ligne avec `const MAITRE_URL = ...`
- [ ] Mettre à jour avec votre URL réelle du Worker Maître
- [ ] Exemple : `const MAITRE_URL = 'https://maitre.websuite.cc';`

### 2. Vérifier les Chemins

- [ ] Vérifier que les chemins dans `admin/index.html` sont corrects
- [ ] Vérifier que les chemins dans `admin/dashboard.html` sont corrects
- [ ] Vérifier que `core/admin.js` est accessible depuis `/core/admin.js`

## 🧪 Test Local

Avant de déployer, tester localement :

- [ ] Lancer un serveur local :
  ```bash
  python -m http.server 8000
  # ou
  npx http-server
  ```
- [ ] Ouvrir `http://localhost:8000`
- [ ] Vérifier que le formulaire d'installation s'affiche
- [ ] Vérifier que les champs GitHub Username et Repository sont détectés automatiquement
- [ ] Vérifier que `/admin` affiche la page de connexion

## 🚀 Déploiement

### 1. Initialiser Git (si nouveau repo)

- [ ] `git init`
- [ ] `git add .`
- [ ] `git commit -m "Initial commit: WebSuite Platform installation form"`

### 2. Connecter au Repository GitHub

- [ ] `git remote add origin https://github.com/votre-username/votre-repo.git`
- [ ] `git push -u origin main`

### 3. Activer GitHub Pages

- [ ] Aller sur GitHub → Votre repository
- [ ] **Settings** → **Pages**
- [ ] **Source** : `main`
- [ ] **Folder** : `/ (root)`
- [ ] Cliquer sur **Save**

### 4. Vérifier le Déploiement

- [ ] Attendre quelques minutes pour le déploiement
- [ ] Accéder à `https://votre-username.github.io/votre-repo`
- [ ] Vérifier que le formulaire s'affiche correctement
- [ ] Vérifier que `/admin` fonctionne

## 🎯 Test d'Installation

Une fois déployé, tester l'installation complète :

- [ ] Accéder au formulaire d'installation
- [ ] Vérifier que GitHub Username et Repository sont pré-remplis
- [ ] Remplir tous les champs requis
- [ ] Cliquer sur "Installer WebSuite Platform"
- [ ] Vérifier que l'installation se termine avec succès
- [ ] Vérifier que le Worker est créé dans Cloudflare Dashboard
- [ ] Vérifier que les variables sont dans GitHub Secrets
- [ ] Vérifier que le workflow GitHub Actions est créé

## ✅ Post-Installation

Après l'installation réussie :

- [ ] Vérifier que `/admin` redirige vers le Worker
- [ ] Se connecter avec les identifiants admin
- [ ] Vérifier que le dashboard fonctionne
- [ ] Vérifier que les appels API vont vers le Worker
- [ ] Tester la synchronisation des variables via GitHub Actions

## 🐛 Dépannage

Si quelque chose ne fonctionne pas :

- [ ] Vérifier la console du navigateur pour les erreurs
- [ ] Vérifier les logs du Worker Maître dans Cloudflare Dashboard
- [ ] Vérifier les logs du workflow GitHub Actions
- [ ] Vérifier que `MAITRE_URL` est correct dans `index.html`
- [ ] Vérifier que `.nojekyll` est présent (important pour GitHub Pages)

## 📚 Documentation

- [ ] Lire `README.md` pour la documentation utilisateur
- [ ] Lire `INSTRUCTIONS.md` pour les instructions détaillées
- [ ] Lire `STRUCTURE.md` pour comprendre la structure
- [ ] Lire `QUICK-START.md` pour le guide rapide

## 🎉 C'est Prêt !

Une fois toutes les cases cochées, votre repository statique est prêt à être utilisé par les utilisateurs finaux !

