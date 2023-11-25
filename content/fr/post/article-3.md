---
date: 2023-09-12T10:58:08-04:00
description: "L'art de dissimuler du contenu à la vue de tous"
featured_image: "/images/stegano.jpg"
toc: true
title: "La stéganographie"
---

## Avant propos

La stéganographie, est un art ancien de dissimulation de l'information, a évolué au fil du temps pour devenir une technique numérique sophistiquée. Cette discipline vise à cacher des données à l'intérieur d'autres données de manière à ne pas éveiller les soupçons. Un exemple moderne fascinant de stéganographie est la capacité de dissimuler des messages au sein d'images numériques.

## Définition

La stéganographie se distingue de la cryptographie, qui cherche à rendre les messages illisibles, en cherchant plutôt à rendre les messages invisibles. Le mot "stéganographie" provient du grec "steganos" (caché) et "graphie" (écriture), ce qui illustre bien l'objectif de cette pratique millénaire.

## Stéganographie et images ?

Dans le contexte des images numériques, la stéganographie exploite les propriétés subtiles des fichiers graphiques pour incorporer des informations supplémentaires sans altérer significativement l'apparence de l'image. Les variations de couleurs, de pixels ou même de métadonnées peuvent être utilisées pour dissimuler des données.

**1. Modification des pixels**

Une méthode courante consiste à modifier légèrement la valeur des pixels d'une image. En ajustant subtilement les composants de couleur, il est possible d'introduire des données sans que cela ne soit perceptible à l'œil humain.

Vous pouvez retouver sur mon [github](https://github.com/Barret-Pierre/stegano_programme), un exemple de stéganographie utilisant le principe de modification de pixel.

**2. Utilisation de l'éspace de couleur**

Les espaces de couleur comme RGB (Rouge, Vert, Bleu) peuvent être exploités pour cacher des informations. Par exemple, en utilisant la composante rouge d'un pixel pour stocker des données, il est possible de cacher un message sans affecter significativement l'apparence de l'image.

**3. Intégration dans les métadonnées**

Certains systèmes de stéganographie utilisent les métadonnées d'une image pour cacher des informations. En ajoutant des données dans les champs non visibles, comme les commentaires ou les informations de copyright, les messages peuvent être dissimulés de manière astucieuse.

## Les sniffer

Alors que la stéganographie offre une méthode astucieuse pour dissimuler des informations, des outils de détection tels que les "sniffers" sont développés pour identifier ces manipulations. Dans le contexte des images stéganographiées, un sniffer analyse les fichiers à la recherche de schémas caractéristiques qui pourraient indiquer la présence de données cachées.

## Fonctionnement d'un sniffer

1. **Analyse des propriétés statistiques :**

Les sniffers utilisent des algorithmes avancés pour comparer les propriétés statistiques d'une image normale avec celles d'une image potentiellement stéganographiée. Des anomalies dans la distribution des couleurs, des pixels ou d'autres caractéristiques visuelles peuvent être des indicateurs.

2. **Examen des métadonnées :**

Certains sniffers examinent également les métadonnées de l'image, à la recherche d'informations inattendues ou non conformes. Des modifications dans les champs de métadonnées peuvent révéler la présence de données cachées.

3. **Analyse de l'espace de couleur :**

Les sniffers peuvent se concentrer sur des espaces de couleur spécifiques, tels que le RGB, pour détecter des altérations subtiles. Par exemple, la recherche de variations significatives dans une composante spécifique peut indiquer la présence de données dissimulées.

![Sniffer stéganographie](/images/sniffer.png)

Voici un exemple de ce à quoi peut ressembler la détéction par analyse de l'espace couleur. Tout à gauche l'image original. En haut a gauche une image sans message caché passé dans le sniffer. Plus on avance vers la droite plus l'image se déforme, ce qui indique le degré de pixels altérés. Si une images est déformé, elle renferme surement un message.

## Limitations des sniffers

Bien que les sniffers soient des outils puissants, ils ne sont pas infaillibles. Les stéganographes peuvent adapter leurs techniques pour contourner les méthodes de détection courantes. Des approches avancées, telles que l'utilisation de méthodes de stéganographie robuste, peuvent rendre la détection plus difficile.

## Les applications de la stéganographie

La stéganographie trouve des applications dans divers domaines. Du côté positif, elle peut être utilisée pour la protection des données, la dissimulation de messages confidentiels ou même pour des besoins artistiques. Cependant, elle peut également être utilisée à des fins malveillantes, telles que le vol d'informations sensibles.

## Conclusion

La stéganographie dans les images est un domaine fascinant où l'art ancien de cacher des messages rencontre la sophistication de la technologie numérique. Alors que cette technique peut être utilisée de manière constructive, elle soulève également des préoccupations éthiques quant à son utilisation potentielle à des fins malveillantes. En fin de compte, comprendre la stéganographie peut aider à renforcer la sécurité numérique et à sensibiliser aux défis constants de la protection des informations dans notre monde interconnecté.
