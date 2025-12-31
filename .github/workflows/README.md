# GitHub Actions Workflows

Ce dossier contient les workflows GitHub Actions pour WebSuite Platform.

## 📋 Workflows Inclus

### `sync-vars.yml`

**Rôle** : Synchronise les variables d'environnement depuis GitHub Secrets vers le Cloudflare Worker.

**Déclencheurs** :
- `workflow_dispatch` : Déclenchement manuel depuis l'interface GitHub
- `repository_dispatch` : Déclenchement automatique par le Worker Maître

**Fonctionnement** :

1. **Setup Wrangler** : Configure Wrangler CLI pour interagir avec Cloudflare
2. **Inject Variables** : Injecte toutes les variables depuis GitHub Secrets vers le Worker

**Variables synchronisées** :

- **Variables de base** (obligatoires) :
  - `ADMIN_EMAIL`
  - `ADMIN_PASSWORD`
  - `GITHUB_PAT`
  - `GITHUB_USER`
  - `GITHUB_REPO`

- **Variables optionnelles** :
  - `BLOG_FEED_URL`
  - `YOUTUBE_FEED_URL`
  - `PODCAST_FEED_URL`
  - `EVENTS_FEED_URL`
  - `GOOGLE_AI_KEY`
  - `OPENAI_API_KEY`
  - `MISTRAL_AI_API_KEY`
  - `DEEPSEEK_API_KEY`
  - `DEEPL_API_KEY`
  - `SUPABASE_URL`
  - `SUPABASE_ANON_KEY`
  - Et bien d'autres...

## 🔧 Configuration Requise

### Secrets GitHub Requis

Pour que le workflow fonctionne, vous devez configurer ces secrets dans **Settings → Secrets and variables → Actions** :

- `CLOUDFLARE_API_TOKEN` : Token API Cloudflare avec permissions Workers
- `CLOUDFLARE_ACCOUNT_ID` : Account ID Cloudflare
- `ADMIN_EMAIL` : Email administrateur
- `ADMIN_PASSWORD` : Mot de passe administrateur
- `GITHUB_PAT` : GitHub Personal Access Token
- `GITHUB_USER` : Nom d'utilisateur GitHub
- `GITHUB_REPO` : Nom du repository

### Secrets Optionnels

Toutes les autres variables (BLOG_FEED_URL, OPENAI_API_KEY, etc.) sont optionnelles et peuvent être ajoutées selon vos besoins.

## 🚀 Utilisation

### Déclenchement Automatique

Le workflow est automatiquement déclenché par le Worker Maître lors de l'installation initiale.

### Déclenchement Manuel

1. Allez dans **Actions** → **Sync Variables to Worker**
2. Cliquez sur **Run workflow**
3. Sélectionnez la branche (généralement `main`)
4. Cliquez sur **Run workflow**

### Après Modification de Secrets

Si vous modifiez des secrets dans GitHub Secrets, vous pouvez :

1. Déclencher manuellement le workflow
2. Ou attendre que le Worker Maître le déclenche automatiquement

## 📝 Notes

- Le workflow utilise le nom du Worker : `{GITHUB_USER}-websuite-worker`
- Seules les variables définies dans GitHub Secrets sont synchronisées
- Les variables vides sont ignorées
- Le workflow est idempotent (peut être exécuté plusieurs fois sans problème)

## 🔍 Vérification

Pour vérifier que les variables sont bien synchronisées :

1. Allez dans Cloudflare Dashboard → Workers
2. Sélectionnez votre Worker (`{username}-websuite-worker`)
3. Allez dans **Settings** → **Variables**
4. Vérifiez que toutes les variables sont présentes

## 🐛 Dépannage

### Erreur : "CLOUDFLARE_API_TOKEN not found"

- Vérifiez que le secret `CLOUDFLARE_API_TOKEN` est bien configuré dans GitHub Secrets
- Vérifiez que le token a les bonnes permissions (Workers:Edit, Account:Read)

### Erreur : "CLOUDFLARE_ACCOUNT_ID not found"

- Vérifiez que le secret `CLOUDFLARE_ACCOUNT_ID` est bien configuré
- L'Account ID est disponible dans Cloudflare Dashboard → Overview

### Erreur : "Worker not found"

- Vérifiez que le Worker a bien été créé par le Worker Maître
- Le nom du Worker doit être : `{GITHUB_USER}-websuite-worker`

### Variables non synchronisées

- Vérifiez que les variables sont bien définies dans GitHub Secrets
- Vérifiez les logs du workflow pour voir les erreurs éventuelles
- Vérifiez que le nom du Worker est correct

## 📚 Documentation

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Wrangler Action](https://github.com/cloudflare/wrangler-action)
- [Cloudflare Workers Secrets](https://developers.cloudflare.com/workers/configuration/secrets/)

