# Site de J-ECS (Junior Entreprise ECS) : jecs.ci

Site statique (HTML/CSS) hébergé sur Cloudflare, avec un espace d'administration sur **jecs.ci/admin**.

## Ce que l'administrateur peut modifier

Il suffit d'aller sur **jecs.ci/admin** et de se connecter avec un compte GitHub autorisé.

- **L'équipe** : mandat, texte de présentation, membres (nom, poste, promotion, photo, LinkedIn). On peut ajouter, supprimer ou réordonner les membres par glisser-déposer.
- **Informations générales** : titre et texte d'accueil, délai de réponse, e-mail, WhatsApp, adresse, liens LinkedIn et Facebook.
- **Services** : ajouter, modifier ou retirer un service, son icône et ses prestations.
- **Témoignages, clients et chiffres clés** : chaque section reste masquée tant qu'elle est vide. N'y mettre que des informations réelles, avec l'accord des clients cités.

Après « Publier », le site est mis à jour en 1 à 2 minutes.

## Organisation des fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | La page du site (mise en page, styles, sections fixes) |
| `content/site.json` | Textes d'accueil et coordonnées |
| `content/services.json` | Liste des services |
| `content/temoignages.json`, `partenaires.json`, `chiffres.json` | Sections facultatives |
| `content/membres.json` | Membres de l'équipe |
| `images/membres/` | Photos des membres |
| `images/brand/` | Logo J-ECS |
| `admin/` | Espace d'administration (Sveltia CMS) |
| `merci.html` | Page affichée après l'envoi du formulaire |

## Mise en ligne sur Cloudflare (hébergement actuel)

Le site est un site statique, sans compilation. Les fichiers `wrangler.jsonc` et `.assetsignore` indiquent à Cloudflare quoi publier.

1. **GitHub** : créer un dépôt `jecs-site` sur le compte GitHub de la structure et y déposer tout le contenu de ce dossier (fichiers cachés compris : `.assetsignore`).
2. **admin/config.yml** : remplacer (déjà fait : `J-ECS/jecs-site`).
3. **Cloudflare** : Workers & Pages → ouvrir le projet → Settings → Builds → *Connect* le dépôt GitHub `jecs-site`, branche `main`. Laisser la commande de build vide ; la commande de déploiement est `npx wrangler deploy`. Chaque modification publiée depuis l'admin redéploie alors le site automatiquement.

## Accès à l'administration (J-ECS)

L'administration utilise Sveltia CMS. Chaque administrateur a besoin d'un compte GitHub invité sur le dépôt (Settings → Collaborators, rôle Write).

1. Aller sur `/admin` du site, cliquer sur **Sign In with Token**.
2. Suivre le lien proposé pour créer un jeton GitHub (fine-grained, limité au dépôt `jecs-site`, permission **Contents : Read and write**), puis le coller.
3. Le jeton reste dans le navigateur. À ne jamais partager ; le révoquer sur GitHub en fin de mandat.

Option plus confortable plus tard : un bouton « Sign In with GitHub » via le service gratuit *sveltia-cms-auth* déployé sur Cloudflare, puis `base_url` dans `admin/config.yml`.

## Formulaires

Les formulaires sont prévus pour Netlify Forms et ne transmettent rien sur Cloudflare tant qu'ils n'ont pas été adaptés.

## Passation de mandat

À chaque nouveau bureau : inviter les nouveaux administrateurs sur le dépôt GitHub, retirer les anciens, puis mettre à jour l'équipe depuis jecs.ci/admin. Les comptes GitHub et d'hébergement doivent rester au nom de J-ECS.
