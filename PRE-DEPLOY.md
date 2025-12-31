# ✅ Checklist Avant Déploiement GitHub

Vérifiez ces points **AVANT** de pousser sur GitHub.

## ⚙️ Configuration Obligatoire

### 1. Configurer l'URL du Worker Maître

**Fichier** : `index.html` (ligne ~194)

**Action** : Remplacer l'URL placeholder par votre URL réelle

```javascript
// AVANT (à changer)
const MAITRE_URL = 'https://maitre.websuite.cc';

// APRÈS (votre URL réelle)
const MAITRE_URL = 'https://votre-worker-maitre.workers.dev';
```

> ⚠️ **IMPORTANT** : Si vous ne configurez pas cette URL, l'installation ne fonctionnera pas !

## 📋 Vérification des Fichiers

Vérifiez que tous ces fichiers sont présents :

- [x] `index.html` (formulaire d'installation)
- [x] `admin/index.html` (page de connexion)
- [x] `admin/dashboard.html` (dashboard)
- [x] `admin/ide.html` (IDE intégré)
- [x] `core/admin.js`
- [x] `core/frontend.js`
- [x] `core/ide-context.js`
- [x] `core/WhatsappChatBox.min.js`
- [x] `.github/workflows/sync-vars.yml`
- [x] `.github/workflows/README.md`
- [x] `.nojekyll` (important pour GitHub Pages)
- [x] `.gitignore`

## 🧪 Test Local (Recommandé)

Avant de pousser, testez localement :

```bash
cd static-repo
python -m http.server 8000
# ou
npx http-server
```

Puis ouvrez `http://localhost:8000` et vérifiez :
- [ ] Le formulaire s'affiche correctement
- [ ] Les champs GitHub Username et Repository sont détectés automatiquement
- [ ] Le formulaire est fonctionnel (pas d'erreurs dans la console)

## 🚀 Commandes pour Pousser sur GitHub

```bash
cd static-repo

# Initialiser Git (si nouveau repo)
git init

# Ajouter tous les fichiers
git add .

# Commit
git commit -m "Initial commit: WebSuite Platform installation form"

# Ajouter le remote (remplacer par votre URL)
git remote add origin https://github.com/votre-username/votre-repo.git

# Pousser
git push -u origin main
```

## ✅ Après le Push

1. **Activer GitHub Pages** :
   - Allez sur GitHub → Votre repository
   - **Settings** → **Pages**
   - **Source** : `main` → **Save**

2. **Vérifier le déploiement** :
   - Attendez 1-2 minutes
   - Accédez à `https://votre-username.github.io/votre-repo`
   - Vérifiez que le formulaire s'affiche

3. **Tester l'installation** :
   - Remplissez le formulaire
   - Vérifiez que l'installation fonctionne

## 🐛 Si Problème

- Vérifiez la console du navigateur (F12)
- Vérifiez que `MAITRE_URL` est correct
- Vérifiez que `.nojekyll` est présent
- Vérifiez les logs GitHub Actions si le workflow ne fonctionne pas

## 📝 Notes

- Le workflow GitHub Actions sera créé automatiquement par le Worker Maître
- Les secrets GitHub seront injectés automatiquement lors de l'installation
- Le Worker Cloudflare sera créé automatiquement

---

**Une fois cette checklist complétée, vous pouvez pousser sur GitHub !** 🚀

