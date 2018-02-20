---
layout: post
title:  "Partie traitement du langage"
date:   2018-01-21 16:16:01
categories: jekyll update
---


<p style="text-align:justify;">La partie traitement du langage de notre solution va permettre de comprendre les
demandes de l’utilisateur afin de les transformer en commandes compréhensibles par la
partie serveur. Entre autres, elle devra comprendre le langage naturel français. Plus
précisément, elle doit pouvoir prendre en entrée une chaîne de caractères provenant d’un
client et la décomposer afin d’extraire automatiquement les informations importantes avant
de les transmettre au serveur sous un format particulier.
Développer une solution de traitement de langage par nous-mêmes est trop
compliqué et nous avons choisi d’utiliser un logiciel disponible sur le marché dans le but de
traiter cette partie à notre place.</p>

# 1. Choix du logiciel


<p style="text-align:justify;">Nous avons fait le choix d’utiliser le réseau de neurones créé par l’université de
Stanford, Core NLP. Nous utiliserons l’API fournie avec CoreNLP. Ce choix repose sur
plusieurs facteurs, le premier étant qu’il répond à nos besoins d’un logiciel open source
permettant de traiter des données textuelles en français et en Anglais. Ensuite en navigant sur
la page web dédié à Core NLP nous avons pu constater qu’il était très bien documenté ce qui
facilite la prise en main. Enfin ce qui a motivé notre choix est que tout le code source est en
JAVA, langage dans lequel nous avons des connaissances et nous pouvons donc si besoin nous
intéresser au code source directement afin de comprendre son fonctionnement. De plus il est
possible d’utiliser des wrappers en différents langages ce qui nous permettra d’utiliser celui
avec lequel nous somme le plus à l’aise, et celui dans lequel sera développé notre solution.
Notre choix se porte sur le langage JavaScript car c’est celui que nous utilisons le plus cette
année.
De plus nous avons pu déjà voir en réalisant notre état de l’art qu’il existe déjà des projets
ressemblant au notre utilisant CoreNLP sur un Raspberry pi.</p>

# 2. Fonctionnement de CoreNLP


<p style="text-align:justify;">Le principe du logiciel est de pouvoir utiliser plusieurs outils d’analyse linguistique. Il
est possible de choisir lesquels on souhaite utiliser et ceux qui ne correspondent pas à notre
demande. Dans ces outils certains permettent au logiciel d’étiqueter les mots selon leurs types
(nom, verbe, personne, etc) . Enfin une fois les types associés on peut traiter ces données
et faire ressortir celles qui nous intéressent. On voit donc bien ici que les fonctionnalités de ce logiciel correspondent pleinement à nos besoins, ce que nous avons pu vérifier grâce à leur version démo sur la page web (voir figure ci-dessous). Pour ce qui est de l’utilisation, il y a la possibilité de tester les différentes fonctions sur des textes directement sur leur site. Une fois que l’on aura pu tester les outils utiles pour notre projet, nous pourrons faire appel à l’outil depuis notre programme. Pour ce faire il y a deux solutions possibles, soit il faut télécharger la librairie correspondant à JavaScript (node.js) depuis le site web, soit utiliser des gestionnaires de dépendances tels que Maven, Ant ou Gradle qui importent
automatiquement les librairies. </p>

![image](/assets/traitement.png)


# 3. Utilisation dans notre projet


<p style="text-align:justify;">À partir du schéma global on peut voir que la partie traitement du langage de notre
projet reçoit les messages envoyés par le client à travers la partie serveur. Son objectif va être
de comprendre les informations fournies dans la commande en repérant les verbes d’actions
(exemple : Allumer, Éteindre…) mais aussi l’objet ou le groupe d’objet concerné. Une fois ces
informations récupérées la partie traitement du langage va devoir les transformer en une
commande au format JSON qui sera envoyé au serveur. Le format JSON est utilisé afin que le
serveur quisera codé en nodeJS puisse l’interpréter facilement. Ce type de document JSon est
le suivant : </p>

<div style="text-align:center;">{pseudo : “nomClient”, objet: “idObjet”, action : “actionaEffectuer”}</div>


<p style="text-align:justify;">Dans le cas où le scénario est activé par un client, la partie traitement du langage décompose
le scénario en plusieurs messages à envoyer à la partie serveur. C’est la partie serveur qui
stockera les différents scénarios dans une base de données. Elle enverra les commandes à la
partie serveur, et enverra une seule commande pour un seul objet. C’est à dire que lors de
l’activation d’un scénario, la partie traitement de langage enverra plusieurs messages à la
partie serveur et chacun de ces messages activera un objet connecté.
Cette partie est donc une des plus importantes de notre projet car le bon
fonctionnement repose en grande partie sur la compréhension des commandes. Ce sera donc
la partie que nous allons devoir réaliser en premier afin de pouvoir la tester au maximum et
s’assurer de son bon fonctionnement. </p>
