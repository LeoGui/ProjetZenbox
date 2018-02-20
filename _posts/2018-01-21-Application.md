---
layout: post
title:  "Partie application"
date:   2018-01-21 16:16:01
categories: jekyll update
---


<p style="text-align:justify;">Dans un premier temps notre partie client sera très basique comme nous l’avons déjà
expliqué dans la partie serveur et servira à tester le bon fonctionnement des parties serveur
et traitement du langage. Autrement dit, le traitement d’une demande client étant la partie
essentielle dans notre projet ; il faut qu’elle puisse être testée le plus rapidement possible.
Cependant une fois que les parties serveurs et traitement du langages seront opérationnelles
nous souhaitons réaliser une Application intuitive pour rendre son utilisation facile pour
l’utilisateur.</p>

# 1. Plateforme utilisée

<p style="text-align:justify;">La solution finale de notre application sera une application mobile développée sous
plateforme Android. Suivant des cours de développement d’application mobile sous Android,
nous avons ou aurons les compétences suivantes nécessaires afin d’atteindre nos objectifs
d’ici la fin du semestre :</p>
- Connaissance des langage Java et Javascript
- Connaissance de l’environnement de travail Android Studio
- Utilisation du protocole Bluetooth

<p style="text-align:justify;">Nous pensons donc avoir les compétences nécessaires pour atteindre nos objectifs en
utilisant cette solution. Cependant, un de nos objectifs étant de rendre possible l’utilisation
de notre solution sur d’autres plateformes qu’Android, nous devrons plus tard nous former
afin d’acquérir les compétences nécessaires.
Concernant le choix du protocole de communication utilisé entre notre partie client et
les autres parties de notre solution, nous avions le choix entre le Bluetooth et le WIFI. En effet
ces deux protocoles étaient tout à fait adaptés à notre solution et pouvaient facilement être
utilisés avec des cartes Raspberry Pi. N’ayant pas d’intérêt à choisir l’un plutôt que l’autre,
nous avons choisi Bluetooth sans raison particulière.</p>

# 2. Schéma de notre solution

![image](/assets/application.png)
<p style="text-align:justify;">Ce schéma ne représente que les différentes interfaces graphiques auxquelles sera
confronté l’utilisateur final. Il ne représente pas l’échange de données entre notre application
mobile et la partie traitement de langage ou serveur. L’échange de messages se fait de la
même manière que celle employée dans la solution test. Cette architecture nous convient
puisqu’elle permet de couvrir tous besoins. Nous pourrons l’améliorer par la suite si besoin
sans problèmes puisque les différentes parties sont bien séparées.
Lorsque le client se connecte à l’application, il arrive sur un écran où il peut renseigner
son Login et Mot de passe afin de s’authentifier. Ensuite, il pourra choisir de configurer des
scènes ou alors d’accéder au chat qui lui permettra de communiquer avec notre solution
domotique. Dans la partie éditeur, il sera possible de renseigner des mots-clefs particuliers
qui déclencheront les scènes afin de faciliter le travail de la partie de traitement du langage.
Par exemple on pourra spécifier que le mot clef “salon” référera à tous les objets connectés
situés dans le salon (qui ne seront connus que par un identifiant et non par leur position
géographique). Ces mots clés seront stockés dans la partie serveur qui s’occupera de séparer
une commande de scènes en plusieurs commande.</p>

# 3. Communications avec le serveur
#### a. Authentification

<p style="text-align:justify;">La partie application mobile de notre solution devra envoyer des données à notre
partie serveur dans le cadre de l’authentification. La partie serveur gérera la base de données
contenant tous les comptes utilisateurs autorisés à se connecter au système.
Le protocole utilisé sera du Bluetooth, ce qui permet de communiquer sans problème
avec la partie serveur où que soit l’utilisateur dans la limite de la propriété.
Le format du message sera bien spécifié puisque les messages seront transmis sous un
format JSON particulier. Le format exact des messages est le même que celui décrit dans la
solution test.</p>

#### b. Envoie de commande

<p style="text-align:justify;">La partie application mobile devra aussi envoyer des données au serveur dans le cadre
d’envoi de commandes par l’utilisateur.
Ces commandes seront envoyées par protocole Bluetooth également.
Le message sera encore « brut », c’est-à-dire que la commande utilisateur ne sera pas
encore modifiée. C'est la partie traitement du langage qui s’en chargera. Le message
encapsulé dans le protocole de transmission sera tout de même au format JSON, de la même
manière qu’expliqué dans la partie solution test.</p>
