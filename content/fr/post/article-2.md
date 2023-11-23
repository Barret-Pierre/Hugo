---
date: 2023-09-11T10:58:08-04:00
description: "Logo d'Hugo"
featured_image: "/images/hugo.svg"
tags: []
subtitles: [introduction, definition, remind, install, create, theme]
title: "Hugo et les github-pages"
---

# Introduction

Mettre en ligne un site statique peut être fastidieux. Entre la phase de conception, de développement et de déploiment, le processus de création peut s'avérer particulièrement lourd. Découvrons comment Hugo et les Github-pages peuvent palier ce problème.

# Définition

**Hugo c'est quoi ?**

Hugo est un outil open source utilisé pour créer des sites
web statiques. Contrairement aux systèmes de gestion de contenu (CMS) dynamiques comme WordPress, Hugo génère des fichiers HTML statiques prêts à être servis par n’importe quel serveur web. il est particulièrement efficace pour créer rapidement des blogs, des portfolios et des sites de documentation.

**Github-pages c'est quoi ?**

GitHub Pages est un service d’hébergement fourni
par GitHub qui permet de publier des sites web directement à partir d’un dépôt GitHub.

# Rapels

**Git**

Git est un système de contrôle de version distribué. Il enregistre les
modifications apportées aux fichiers au fil du temps, permettant ainsi de revenir à des versions antérieures si nécessaire. Il nous permettra de versionner notre projet

**Github**

GitHub est une plateforme de gestion de code source et de
collaboration basée sur Git. Elle permet de stocker des répertoires (projets), de collaborer sur des modifications, et de gérer le développement de logiciels. Nous utiliseront cette plateforme pour héberger notre projet.

**Github actions**

GitHub Actions est un outil d’automatisation qui permet de créer des workflows personnalisés pour tester, construire et déployer du code directement depuis GitHub. Nous l'utiliseront pour créer notre propre workflow de déploiement.

# Installer Hugo

Vous pouvez installer Hugo sur **MacOs** par l'intermédiaire de [Homebrew](https://brew.sh/). Dans votre terminal entrez la commande suivante.

```
brew install hugo
```

Pour verifier que Hugo est bien installé rentrez la commande suivante.

```
hugo version
```

Vous dreviez obtenir ceci.

```
hugo v0.120.4-f11bca5fec2ebb3a02727fb2a5cfb08da96fd9df+extended darwin/arm64 BuildDate=2023-11-08T11:18:07Z VendorInfo=brew
```

Pour les autres systèmes d'exploitation, je vous laisse aller sur la [documentation d'Hugo](https://gohugo.io/installation/).

# Créer son site avec Hugo

## Architecture d'Hugo

Dans un premier temps nous allons créer le site en local.
Ouvrez votre éditeur de code préféré et choissisez le répertoire de travail qui vous convient.

Créez un nouveau site avec hugo.

```
hugo new site myWebSite
```

Hugo construit l'architecture de dossier suivante.

```
my-site/
├── archetypes/
│   └── default.md
├── assets/
├── content/
├── data/
├── i18n/
├── layouts/
├── static/
├── themes/
└── hugo.toml
```

**Archetypes**

Ce dossier contient les templates utilisés lors de la création de chaque nouveau contenu.

**Assets**

Ce dossier contient tous les fichiers personnalisés qui seront passés au pipeline de build du site, comme les fichier CSS, Sass, Javascript...

**Content**

Ce dossier regroupe tous les fichiers markdown comprenant le contenu du site.

**Data**

Ce dossier permet de stocker des fichiers contenant des données qui seront utilisable par les templates et le contenu. Des matadonnées ou des données en dure par exemple.

**i18n**

Ce dossier contient l'ensemble des tables de traduction. Cela permet de gèrer le multilingue

**Layouts**

Ce dossier contient l'ensemble des templates personnalisés. Ces templates sont utilisés en corrélation avec les fichiers de contenus pour créer les pages du site.

**Static**

Ce dossier contient tout les fichiers statiques du site (images, vidéos...).

**Themes**

Ce dossier contient les différent thèmes utilisés pour le site.

**hugo.toml**

Ce fichier est le fichier de configuration du site Hugo. C'est ce fichier qui est utilisé pour construire le site en fonction des paramètres qu'il contient.

## Créer son premier post

Maintenant que votre architecture est posée. Créez votre premier post en utilisant la commande suivante.

```
hugo new content posts/my-first-post.md
```

Hugo créé le fichier correspondant dans le répertoire _content/posts_. Si vous ouvrez ce fichier vous verez ceci.

```
---
title: "My First Post"
date: 2022-11-20T09:03:20-08:00
draft: true
---
```

C'est ce que l'on apelle le "Front Matter". Cette section regroupe les metadonnées lié au contenu. On y retourve le titre, l'heure à laquelle le post a été créé, ainsi qu'un paramètre _draft_. Ce paramètre indique à Hugo que ce post est en brouillon et qu'il n'est pas nécéssaire de l'inclure dans le rendu du site lors du build.

Ajoutez un peu de [markdown](https://commonmark.org/help/) à votre contenu.

```
---
title: "My First Post"
date: 2022-11-20T09:03:20-08:00
draft: true
---
## Introduction

Ceci est un text en **gras**, et ça c'est un text en *italic*.

Visitez le site [Hugo](https://gohugo.io) !

```

Votre premier post est créé. Vous allez maintenant lancer le build de votre site.

```
hugo -D
```

Cette commande à pour but de construire votre site en créant les fichier statique nécéssaire. Le flag _-D_ vous permet de prendre en compte les fichiers draft lors de la construction.

Vous devez avoir remarqué que l'architecture a changé. Deux nouveaux dossier sont apparus.

```
my-site/
├── archetypes/
│   └── default.md
├── assets/
├── content/
├── data/
├── i18n/
├── layouts/
├── public/       <-- Créé à la construction du site
├── resources/    <-- Créé à la construction du site
├── static/
├── themes/
└── hugo.toml
```

**public**

Ce dossier contient l'ensemble des fichiers statiques générés lors du build du site. C'est ce dossier qui est utilisé lors du déploiement du site.

**resources**

Ce dossier contient tous les fichiers d'assets générés lors du build du site. Il contient les fichier CSS et Javascript minifiés utilisé par nos pages.

Votre site est construit et prêt à être déployer localement.

```
hugo server -D
```

Cette commande déploie le site localement et prend en compte les fichiers drafts lors du build.

Vous pouvez accèder à votre site à partir de [http://localhost:1313](http://localhost:1313). Pour l'instant votre site n'affiche rien à part une érreure 404 c'est tout à fait normal, vous n'avez pas encore de structure de pages.

# Ajouter un thème à notre site

## Installer un thème

Votre site n'as pas de structure et nous aimerions pour en créer une arpidement, cette étape peut être longue et fastidieuse. Heureusement, Hugo met à disposition de nombreux thèmes.

Choisissez un thème sur [HugoThemes](https://themes.gohugo.io/)
Personellement j'ai choisi le thème "Ananke".

Installer le thème au sein de votre projet, depuis le répertoire racine de votre site.

```
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```

Cette commande initialise votre répertoire git et clone le repository du thème en question dans le dossier _themes/ananke_. Le thème est accèssible depuis ce dossier.

Indiquez à Hugo que vous souhaitez utiliser ce thème en vous rendant dans le fichier de configuration hugo.toml et en ajoutant la ligne suivante.

```
theme = 'ananke'
```

Si vous retournez sur votre site maintenant rien n'a changé. Effectivement il faut relancer la commande de build _hugo_ pour que les nouvelles mises à jour du fichier de configuration soient prises en compte.

```
hugo -D
hugo server -D
```

Votre site ressemble maintenant à ceci.

![Exemple du site avec thème](/images/site-theme.png)

Pour utiliser le site préconçu proposé par le thème, vous pouvez copier-coller l'ensemble des fichiers contenus dans le dossier `/theme/ananke/exempleSite/content` dans le dossier `/content/`.

⚠️ Le site d'exemple est un site gérant le multilingue, si vous désirez l'utiliser, copier le contenu du fichier de configuration `config.toml` dans votre fichier de configuration principal `hugo.toml`.

## Surcharger le thème

Si vous voulez changer le style et pourquoi pas l'architecture de certains élément il faut commencer par ajouter un style customisé.

Dans le dossier assests, créez un dossier `ananke/css`. Dans ce dossier créez un fichier `custom.css`. C'est dans ce fichier que vous pourrez créer vos propres classe CSS et surcharger celui du thème. Surchargez le CSS en ajoutant le style suivant.

```
body {
  color: red;
}
```

Indiquez à hugo qu'il faut prendre en compte le fichier `custom.css` lors du build. Ouvrez le fichier de configuration `hugo.toml`
Au sein du paramètre `params` ajoutez la ligne suivante.

```
[params]
  ...
  custom_css = ["custom.css"]
```

Relancez le site pour voir apparaitre les modification. (N'oubliez pas de relancer le build 😉)

## Modifier la structure du thème

Modifiez la structure du footer. Pour cela, modifiez le temple HTML.

L'ensemble des fichiers permettant de figer la structure du site se trouvent dans le dossier `theme/ananke/layout`. C'est dans ce dossier que pioche Hugo lorsqu'il doit construire le site. Il n'est pas d'usage de modifier directement ces fichiers.

Créez le dossier `layouts/partials` à la racine du projet. C'est dans ce dossier que va piocher Hugo en priorité pour créer la strucutre du site.

Copiez le fichier `/themes/ananke/layouts/partials/site-footer.html` et collez le dans `/layouts/partials/`.

Vous devriez vous retoruver avec cette architecture de dossier.

```
my-site/
├── ...
├── layouts/
│   └── partials/
│       └── site-footer.html
└── ...
```

Ouvrez ensuite le fichier `site-footer.html` et copiez-collez les lignes suivantes.

```
<footer class="{{ .Site.Params.background_color_class | default " bg-black" }} bottom-0 w-100 pa3" role="contentinfo">
  <div class="flex justify-between">
    <a class="f4 fw4 hover-white no-underline white-70 dn dib-ns pv2 ph3" href="{{ .Site.Home.Permalink }}">
      &copy; {{ with .Site.Copyright | default .Site.Title }} {{ . | safeHTML }} {{ now.Format "2006"}} {{ end }}
    </a>
  </div>
</footer>
```

Relancez le serveur et constatez maintenant que le bouton twitter à disparut. Le site utilise donc bien votre footer personalisé.

# Déployer son site sur github

## Initialiser git au sein du projet

Créez un nouveau repository.
Les répository sont des répertoires distants hébergés par la plateforme [Github](https://github.com/).

Créez un nouveau repository sur github.

![Création d'un nouveau repository github](/images/repo.png)

Dans votre terminal, configurez les informations de connexion Git, pour éviter de rentrer vos identifiants de connexion à chaque fois.

```
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
```

Retournez sur votre répertoire de travail et initialiser git à la racine du projet.

```
git init
```

Chargez toutes les modifications précédentes.

```
git add .
```

Cette commande est particulièrement utile mais peut s'avérer dangeureuse, car elle charge toutes les modifications et les prépare à être envoyées sur le repository distant. Dans notre cas nous ne souhaitons pas envoyé le dossier public et ressources car il ne font pas parti des fichiers sources.

Pour ignorer ces deux dossiers, créez à la racine de votre projet, un fichier `.gitignore`. Indiquez dans ce fichier les dossiers et fichiers à ignorer lors d'un stage.

Collez les lignes suivantes dans votre .`gitignore`.

```
/public
/resources
.hugo_build.lock
```

Une fois les fichiers prêts à partir nous allons créer notre premier commit. Le commit permet d'enregistrer les modification précédement chargé. Les commit sont définit par un identifiant unique et un message.

```
git commit -m "Votre message"
```

Créez la connexion avec votre répertoire distant

```
git remote add origin https://yourepository.git
```

Poussez vos modifications sur le repository distant.

```
git push -u origin main
```

Le flag -u ou --set-upstream est ici utilisé pour indiquer que la branch main est une branch d'origine valide, si ce n'est pas le cas la branch sera créer sur le repository distant.

# Déployer le site manuellement

Commencez par build le site en local si ce n'est pas déjà fait.

```
hugo
```

⚠️ Avant de lancer le build modifiez votre fichier de configuration pour indiquer vers quelle url vous souhaitez faire pointer vos requêtes de récupération de fichier statique. Pour cela changez le paramètre `baseUrl` par l'url cible de votre site.

Rendez-vous dans le dossier public et lancez l'initialisation de git.

```
git init
```

Chargez l'ensemble des modifications apportées à la création du dossier public et créez votre commit.

```
git add .
git commit -m "Votre message"
```

Créez une branche de déploiement manuel nommée `gh-pages` et connectez le répertoire local à votre répertoire distant.

```
git branch -M gh-pages
git remote add origin https://yourepository.git
```

Enfin poussez votre comit et la nouvelle branche sur le repository distant.

```
git push -u origin gh-pages.
```

Si vous vous rendez sur votre git-hub, vous vérrez que la branche gh-pages existe et quelle contient uniquement le dossier public.

Utilisons les Gihutb-pages pour déployer manuellement votre site. Commencez par vous rendre dans les `settings/pages` de votre repository.

![Settings repository](/images/settings-repo-manual.png)

Choissisez la source de déploiement 'Deploy from a branch'. Selectionnez la branch gh-pages et sauvegardez.

Rendez vous dans l'onglet Actions et admirez le déploiement de votre site s'executer. Une fois le déploiement terminé un lien est accessible pour accèder à votre site.

## Déployer automatique le site

Vous imaginez refaire ce déploiement à chaque fois que l'on créer un nouveau post sur notre site. Cela semble fastidieux. Nous allons donc metre en place un déploiment continue. Pour cela nous allons utiliser les github-actions.

Commencez pas créer un dossier `.github/workflows` à la racine de notre projet. Ce dossier contiendra tout les workflows nécéssaire au déploiement de votre site.

Créez un fichier de configuration appelé `deploy.yml` dans ce dossier. Ouvrez le fichier dans votre editeur et collez le workflows proposé par la documentation technique de Hugo.

```
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.120.2
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v3
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          # For maximum backward compatibility with Hugo modules
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v2
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2
```

⚠️ Les fichier de configuration yaml sont sensible à l'indentation.

Modifiez les settings/pages de votre repository. Cette fois-ci choisissez 'deploy from github actions'. Pushez les modifications sur votre répository distant.

Rendez vous dans l'onglet Actions et admirez le déploiement de votre site s'executer. Une fois le déploiement terminé un lien est accessible pour accèder à votre site.

# Conclusion

Vous avez appris à créer un site avec Hugo. Cette solution permet de créer des sites statiques rapidement grâce à des templates préconçus. Le CSS et la strucutre des templates peuvent être surchargés et sont facilement personalisables. Le déploiement peut se faire manuellement par l'intermédiaire d'une branche dédiée ou automatiquement grâce au Github-actions par l'intermédiaire d'un fichier de configuration.

Hugo reste une solution simple pour créer un site statique rapide, les thèmes disposent tous d'une docuementation qui permet de répondre au mieux aux exigences de fonctionnalités particulière.
