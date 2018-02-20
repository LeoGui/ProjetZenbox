---
layout: post
title:  "Organisation globale de notre box"
date:   2018-01-21 16:16:01
categories: jekyll update
---

<p style="text-align:justify;">Voici le schéma global de notre box : </p>

![image](/assets/schema.png)

<p style="text-align:justify;">Comme vous pouvez le voir sur ce schéma, dans notre projet, il y a 3 grandes parties :</p>

- La partie Client contenant l’interface utilisateur sous forme d’une application

- Les Objets Connectés de nature variée et communiquant à l’aide de protocoles

- Notre Box contenant la partie de traitement du langage et la partie serveur

<p style="text-align:justify;">Dans notre box, on pourra trouver des Raspberry Pi qui feront office de serveur et hébergeront
le logiciel de traitement de langage.</p>

<p style="text-align:justify;">Pour commencer, le client s'authentifie (pseudo et mot de passe) depuis
l’application mobile, ces données seront envoyées à la partie serveur qui les traitera et
renverra une réponse permettant la connexion de l’utilisateur et son accès aux fonctions de
la ZenBox. Nous utiliserons une base de données afin de stocker les différents pseudos et mot
de passe des utilisateurs.
Les commandes seront ensuite envoyées depuis l’application mobile sous forme
d’échange de messages textuels avec le serveur. Elles seront d’abord envoyées à la partie
serveur qui interagira avec la partie traitement de langage à travers des sockets TCP en
utilisant le format JSon pour les messages. Une fois les messages analysés par la partie
traitement du langage, ils sont renvoyés sous forme de messages compréhensibles par les la
partie serveur qui va pouvoir faire associer les noms d’objets avec les équipements connus
par cette partie, afin de les renvoyer aux objets connectés. La partie serveur aura pour rôle
d’envoyer les commandes aux différents objets connectés et de renvoyer un message de
validation ou d’erreur de la commande à l’utilisateur.</p>
