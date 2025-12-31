# 🚀 Quick Start - Repository Statique

Guide rapide pour créer et déployer le repository statique GitHub Pages.

## 📋 Fichiers Inclus

Ce dossier contient tous les fichiers nécessaires :

- ✅ `index.html` - Formulaire d'installation (à la racine)
- ✅ `README.md` - Documentation pour les utilisateurs finaux
- ✅ `.gitignore` - Fichiers à ignorer
- ✅ `.nojekyll` - Désactive Jekyll sur GitHub Pages
- ✅ `INSTRUCTIONS.md` - Guide détaillé

## ⚡ Déploiement en 3 Étapes

### 1. Créer le Repository GitHub

```bash
# Créer un nouveau repo sur GitHub (via interface web ou CLI)
# Nom recommandé: websuite-static
```

### 2. Copier les Fichiers

```bash
# Option A: Depuis ce dossier
cd static-repo
git init
git add .
git commit -m "Initial commit: WebSuite Platform installation form"
git remote add origin https://github.com/votre-username/websuite-static.git
git push -u origin main
```

### 3. Activer GitHub Pages

1. Allez sur GitHub → Votre repository
2. **Settings** → **Pages**
3. **Source**: `main` → **Save**

Votre site sera disponible sur : `https://votre-username.github.io/websuite-static`

## ⚙️ Configuration Avant Déploiement

**Important** : Avant de pousser, modifiez dans `index.html` ligne ~194 :

```javascript
const MAITRE_URL = 'https://maitre.websuite.cc'; // Mettre votre URL réelle
```

## 🧪 Test Local

Pour tester avant de déployer :

```bash
# Avec Python
python -m http.server 8000

# Avec Node.js
npx http-server

# Puis ouvrir http://localhost:8000
```

## ✅ Checklist

- [ ] Copier tous les fichiers dans votre repository
- [ ] Mettre à jour `MAITRE_URL` dans `index.html`
- [ ] Tester localement
- [ ] Pousser vers GitHub
- [ ] Activer GitHub Pages
- [ ] Tester l'installation en live

## 🎯 Utilisation

Une fois déployé :

1. L'utilisateur accède à `https://username.github.io/repo`
2. Le formulaire s'affiche automatiquement
3. Les champs GitHub Username et Repository sont **détectés automatiquement** ✅
4. L'utilisateur remplit les autres champs
5. Clique sur "Installer"
6. Installation terminée en ~30 secondes !

## 📝 Notes

- Le formulaire détecte automatiquement le username et repo depuis l'URL
- Les champs détectés sont pré-remplis mais modifiables
- L'installation crée automatiquement un Worker Cloudflare
- Les variables sont gérées via GitHub Secrets

## 🆘 Support

- Voir `INSTRUCTIONS.md` pour plus de détails
- Voir `README.md` pour la documentation utilisateur

