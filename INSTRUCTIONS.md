# 📋 Instructions pour le Repository Statique

Ce dossier contient tous les fichiers nécessaires pour créer un repository GitHub Pages qui permettra l'installation automatique de WebSuite Platform.

## 📁 Fichiers Inclus

- `index.html` - Formulaire d'installation (à la racine)
- `README.md` - Documentation pour les utilisateurs
- `.gitignore` - Fichiers à ignorer
- `.nojekyll` - Désactive Jekyll sur GitHub Pages

## 🚀 Utilisation

### Option 1 : Créer un Nouveau Repository

1. **Créer un nouveau repository sur GitHub**
   - Nom : `websuite-static` (ou votre choix)
   - Public ou Private
   - Ne pas initialiser avec README

2. **Cloner et copier les fichiers**
   ```bash
   git clone https://github.com/votre-username/websuite-static.git
   cd websuite-static
   
   # Copier tous les fichiers de static-repo/
   cp -r /chemin/vers/static-repo/* .
   ```

3. **Commit et push**
   ```bash
   git add .
   git commit -m "Add WebSuite Platform installation form"
   git push origin main
   ```

4. **Activer GitHub Pages**
   - Settings → Pages → Source: `main` → Save

### Option 2 : Utiliser ce Dossier Directement

```bash
cd static-repo
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/votre-username/votre-repo.git
git push -u origin main
```

## ⚙️ Configuration

### Mettre à jour l'URL du Worker Maître

Avant de déployer, modifiez dans `index.html` ligne ~187 :

```javascript
const MAITRE_URL = 'https://maitre.websuite.cc'; // Votre URL réelle
```

## ✅ Checklist

- [ ] Copier tous les fichiers dans votre repository
- [ ] Mettre à jour `MAITRE_URL` dans `index.html`
- [ ] Tester localement (ouvrir `index.html` dans un navigateur)
- [ ] Pousser vers GitHub
- [ ] Activer GitHub Pages
- [ ] Tester l'installation en live

## 🧪 Test Local

Pour tester localement avant de déployer :

```bash
# Avec Python
python -m http.server 8000

# Avec Node.js
npx http-server

# Avec PHP
php -S localhost:8000
```

Puis ouvrez `http://localhost:8000` dans votre navigateur.

## 📝 Notes

- Le formulaire détecte automatiquement le username et repo depuis l'URL GitHub Pages
- Les champs détectés sont pré-remplis mais peuvent être modifiés
- L'installation crée automatiquement un Worker Cloudflare et configure GitHub Actions

