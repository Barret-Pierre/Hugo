---
date: 2023-09-10T10:58:08-04:00
description: "Pourquoi et comment protéger les mots de passe ?"
featured_image: "/images/crypto.jpg"
title: "Hashage et Cryptage"
toc: true
---

## Context

Encore aujourd'hui et malgrès les recommendations de la CNIL (Commission National de l'Informatique et des Libertés), le mot de passe les plus utilisé au sein de l'Union Européenne reste "123456". Notre but en tant que développeur est d'incité les utilisateur à renforcer leur mot de passe. Pour cela de nombreuse solutions existe tels que la vérification de la force des mots de passe par l'intermédiaire de Regexp ou de validation d'input.

On pourrait croire qu'un mot de passe complexe protège naturellement les données sensible de l'utilisateur. Malheureusement c'est un peut plus complexe que cela.

## Probématique

Lorsqu'un utilisateur se connecte sur notre site, celui ci choisi un mot de passe. Ce mot de passe sera enregistrer en basse de donées. Cependant, contraindre l'utilisateur à entrer un mot de passe fort n'empèche pas sa lecture au sein de la base de donnée.

Pour protèger ses données sensible, nous allons devoir les chiffrer pour qu'elle ne soit pas facilement utilisable en cas d'attaque ou de leak de notre base.

## Solution d'encodage

Nous avons alors la possibilité d'utiliser une des trois solution proposé cidessous.

![Schéma des trois solution](/images/crypto-solution.png)

Le criptage à chiffrement sysmétrique :
Également appelé chiffrement symétrique, est une méthode de cryptage où la même clé est utilisée pour à la fois chiffrer et déchiffrer les données. En d'autres termes, la clé qui est utilisée pour protéger l'information est la même que celle utilisée pour la restaurer à son état original.

Le criptage à chiffrement asysmétrique :
Également appelé chiffrement asymétrique, est une technique de cryptage où deux clés distinctes mais mathématiquement liées sont utilisées : une clé publique et une clé privée. Ces clés fonctionnent en paire, et ce qui est chiffré avec l'une des clés ne peut être déchiffré qu'avec l'autre. La clé publique peut être partagée librement, tandis que la clé privée doit rester secrète.

Le hashage :
Le hashage est un processus de conversion d'une quantité de données (généralement de taille variable) en une valeur de taille fixe, généralement une séquence de caractères alphanumériques. La fonction de hachage, ou algorithme de hachage, est responsable de cette transformation. L'idée principale derrière le hashage est de produire une empreinte numérique unique (le "hash" ou "haché") pour chaque ensemble de données d'entrée unique.

Dans notre cas le hashage des données sensible en base est une obligation. C'est la solution qui permet un sécurité optimal contrairement au cryptage qui est essentialelement utilisé lors de transmition de fichier sensible.

## Paradigme

Pour comprendre quelle différence il y a entre le hashage et le cryptage essayons de comprendre leur paradigme.

**Cryptage**

![Schéma de la logique d'une fonction de cryptage](/images/cryptage.png)

Comme expliqué précédement, le cryptage permet d'empêcher la lecture d'une information sensible à quiquonque n'aurait pas la clé de chiffrement. Une fonction de cryptage prend donc en entré une donnes sensible. Cette fonction va créer ce que l'on apelle une empreinte de cette donnée, grace à une clé de chiffrement. Cette empreinte pourra être déchifrer avec la bonne clé. Le chiffrement est donc reverssible.

**Hashage**

![Schéma de la logique d'une fonction de hashage](/images/hashage.png)

Une fonction de hashage est un peu plus complexe. Cette fonctione va elle aussi créer une empreinte, cependant celle si ne sera pas déchiffrable. La données passé en entré ne pourra pas être récupéré, le procéssus de chiffrement est irréversible. Pour vérifier le mot de passe d'un utilisateur par exemple, nous comparrerons le hash enregistrer en base de données avec le mot de passe hashé fournis lors de la soumision du formulaire de connexion.

## Les fonctions de hashage

Une fonction de hasage se base sur le principe de multiplicité. Pour des entrées différentes on pourrait avoir la même empreinte. C'est ce que l'on apelle une colision. Une fonciton de hashage retourne toujours une empreinte de longeueur identique quelquesoit la données à chiffrer. Cette longueur s'apelle la plage de chiffrement. Plus il yaura de colision plus il sera difficile de retrouver la données d'origine, plus la plage est grande et moins il y'aura de colision. Si il y'a trop de colision, alors les données d'entré risque de retourner la même empreinte, ce qui n'est pas très sécurisé. Une bonne fonction de hashage réside dans le juste équilibre entre le nombre de colision et la grandeur de sa plage.

Bien sur nous pourrions créer notre propre fonction de hashage, mais ce processus est fastidieux. Par ailleur de nombreux modules existe déjà comme [Bcrypt](https://www.npmjs.com/package/bcrypt) pour Node.Js. Ces modules sont grandement utilisé et donc très souvent mis à l'épreuve.

## Les différentes attaques de base de données

On pourrait croire que maintenant que nos données sensible sont hashées, elles sont à l'abris bien au chaud dans notre base de données. Si jamais notre base de données est récupéré par une personne mal intentionné, il lui sera plus difficile de déchiffrer ces informations. Cependant difficile n'est pas inmpossible.

De nos jour les hacker ont recourt à de nomberuse solution pour récupérer des informations hashés. En voici quelques une pour votre culture personnelle.

![Schéma des attaques de base de données](/images/attac.png)

Attaque par dictionnaire :
Attaque par force brute :

L'utilisation conjointe de ses deux méthodes est particulièrement dévastatrice pour des compte ayant utiliser des mot de passe faible par exemple.

## Conclusion

Le hashage des mot de passe et données sensible en base de donéess est indispensable. Le cryptage n'est pas une alternative viable au hashage pour sécurisé ces données. De nos jours les méthode utiliser par les hacker pour récupérer ces information sensible sont particulièrement efficace sur des données hashée à faible complexité. Inciter les utilisateurs à utiliser des mots de passes robustes reduis grandement les risque de récupération d'information en cas d'ataque par force brute et dictionnaire combiné. Des solution de hashage existe déjà et serotn toujours plus performante que des solution réalisé from scratch.
