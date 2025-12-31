# WebSuite Platform - Repository Statique

Repository statique pour déployer WebSuite Platform sur GitHub Pages avec installation automatique.

## 📁 Structure

```
static-repo/
├── index.html              # Formulaire d'installation
├── admin/                  # Interface d'administration
│   ├── index.html          # Page de connexion
│   ├── dashboard.html      # Dashboard principal
│   └── ide.html            # IDE intégré
├── core/                   # Scripts JavaScript
│   ├── admin.js            # Logique du dashboard
│   ├── frontend.js         # Utilitaires frontend
│   ├── ide-context.js      # Logique de l'IDE
│   └── WhatsappChatBox.min.js  # Widget WhatsApp
└── static/                 # Assets statiques (optionnel)
```

> 💡 **Note** : Voir [STRUCTURE.md](STRUCTURE.md) pour plus de détails sur chaque fichier.

## 🚀 Installation Rapide

### 1. Cloner ce Repository

```bash
git clone https://github.com/votre-username/websuite-static.git
cd websuite-static
```

### 2. Déployer sur GitHub Pages

1. **Pousser vers GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Activer GitHub Pages**
   - Allez dans **Settings** → **Pages**
   - Sélectionnez la branche `main` comme source
   - Cliquez sur **Save**

Votre site sera disponible sur : `https://votre-username.github.io/websuite-static`

### 3. Installer WebSuite Platform

1. Accédez à votre site GitHub Pages
2. Le formulaire d'installation s'affiche automatiquement
3. Remplissez le formulaire :
   - **Email Administrateur** : Votre email
   - **Mot de passe Administrateur** : Minimum 12 caractères
   - **GitHub Personal Access Token** : Token avec permissions `repo`, `workflow`, `write:packages`
   - **GitHub Username** : Détecté automatiquement ✅
   - **Nom du Repository** : Détecté automatiquement ✅
   - **Domaine personnalisé** (optionnel) : Si vous avez un domaine personnalisé

4. Cliquez sur **"Installer WebSuite Platform"**

L'installation se fait automatiquement en ~30 secondes !

## 📝 Configuration

### GitHub Personal Access Token

Créez un token avec les permissions suivantes :
- `repo` - Accès complet aux repositories
- `workflow` - Gestion des workflows GitHub Actions
- `write:packages` - Écriture des packages

Créer un token : https://github.com/settings/tokens

### Variables d'Environnement

Après l'installation, vous pouvez configurer vos variables dans **GitHub Secrets** :

1. Allez dans votre repository → **Settings** → **Secrets and variables** → **Actions**
2. Ajoutez vos variables (ex: `BLOG_FEED_URL`, `GOOGLE_AI_KEY`, etc.)
3. Les variables sont automatiquement synchronisées vers votre Worker

### Déclencher la Synchronisation

Si vous modifiez des variables dans GitHub Secrets :

1. Allez dans **Actions** → **Sync Variables to Worker**
2. Cliquez sur **Run workflow**

## 🎯 Utilisation

Une fois installé :

- **Dashboard Admin** : `https://votre-username.github.io/websuite-static/admin`
- **Frontend** : `https://votre-username.github.io/websuite-static`
- **Worker API** : URL fournie après l'installation

## 🔧 Personnalisation

### Modifier l'URL du Worker Maître

Si vous utilisez votre propre Worker Maître, modifiez dans `index.html` :

```javascript
const MAITRE_URL = 'https://votre-worker-maitre.workers.dev';
```

## 📚 Documentation

- [Documentation Complète](https://docs.websuite.cc)
- [Guide d'Installation](https://docs.websuite.cc/guide/installation)
- [Système d'Installation Automatique](https://github.com/websuite-cc/CMS/blob/main/ProdBeta/INSTALLATION-SYSTEM.md)

## 🆘 Support

- 📧 **Email** : community@websuite.cc
- 🐛 [GitHub Issues](https://github.com/websuite-cc/CMS/issues)
- 📖 [Documentation](https://docs.websuite.cc)

## 📄 License

MIT License - Voir [LICENSE](LICENSE) pour plus de détails.

