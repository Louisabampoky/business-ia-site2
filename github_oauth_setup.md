# Guide d'utilisation pour l'administrateur GitHub

Ce document explique comment configurer et utiliser l'application GitHub OAuth pour permettre l'authentification au système d'administration Decap CMS.

## Étape 1: Créer une application OAuth GitHub

1. Connectez-vous à votre compte GitHub
2. Accédez à Paramètres > Paramètres développeur > OAuth Apps
3. Cliquez sur "New OAuth App"
4. Remplissez les informations suivantes:
   - **Nom de l'application**: Business IA Admin
   - **URL de la page d'accueil**: https://xlhbijgn.manus.space
   - **Description de l'application**: Système d'administration pour le site Business IA
   - **URL de callback d'autorisation**: https://xlhbijgn.manus.space/admin/callback.html
5. Cliquez sur "Register application"
6. Notez le "Client ID" généré
7. Générez un nouveau "Client Secret" et notez-le également

## Étape 2: Mettre à jour la configuration du CMS

1. Modifiez le fichier `/admin/config.yml` pour y ajouter les informations d'authentification:
   ```yaml
   backend:
     name: github
     repo: bemart-limited/business-ia-site
     branch: main
     base_url: https://api.netlify.com
     auth_endpoint: auth
     client_id: VOTRE_CLIENT_ID
   ```
2. Remplacez `VOTRE_CLIENT_ID` par le Client ID noté précédemment

## Étape 3: Configurer le proxy d'authentification

Pour des raisons de sécurité, GitHub nécessite un proxy d'authentification pour les applications OAuth utilisées avec des sites statiques. Nous utiliserons le service Netlify pour cela:

1. Créez un compte sur Netlify (gratuit)
2. Dans les paramètres de votre site Netlify, accédez à "Access control" > "OAuth"
3. Cliquez sur "Install provider"
4. Sélectionnez GitHub et entrez votre Client ID et Client Secret
5. Cliquez sur "Install"

## Étape 4: Accéder à l'interface d'administration

1. Accédez à https://xlhbijgn.manus.space/admin/
2. Cliquez sur "Se connecter avec GitHub"
3. Autorisez l'application à accéder à votre compte GitHub
4. Vous serez redirigé vers l'interface d'administration
