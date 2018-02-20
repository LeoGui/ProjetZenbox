---
layout: post
title:  "Cahier des charges"
date:   2017-10-13 16:16:01
categories: jekyll update
---


<p style="text-align:justify;">La fonction principale de notre boitier est de contrôler les différents équipements qui sont connectés dans la maison. L’utilisateur devra être en mesure, à partir d’une application et via une chatbox textuelle, de contrôler l’ensemble des objets connectés en local (pas d’exportations de données sur internet). Notre système sera composé de plusieurs parties. La partie boitier, la partie application, la partie serveur, traitement du langage et équipements domotiques.</p>

  <p style="text-align:justify;"><strong>Partie Boitier : </strong> Notre boitier contiendra la partie serveur et la partie traitement du langage qui seront hébergés sur des cartes Raspberry Pi. Il faut qu’il soit assez grand pour accueillir un nombre de cartes suffisant et qu’il soit possible de l’agrandir ou d’accéder facilement aux cartes à l’intérieur.</p>


![image](/assets/Boitier.png)



  <p style="text-align:justify;"><strong>Partie Client : </strong>Notre application devra être adaptée aux besoins de l’utilisateur. Nous voulons implémenter différentes fonctionnalités dont certaines plus importantes et prioritaires. Elle devra être connectée à la partie serveur afin de transmettre les demandes de l’utilisateur.</p>


![image](/assets/Client1.png)
![image](/assets/Client2.png)

  <p style="text-align:justify;"><strong>La partie serveur : </strong>Dans notre boîtier, il y aura une partie serveur géré via un ou plusieurs Raspberrys pis. Ces derniers devront recevoir les demandes des utilisateurs et les faire analyser par la partie traitement du langage. La partie traitement de langage devra répondre au serveur en renvoyant la demande programme. Le serveur envoie ensuite la ou les commandes appropriées aux réseaux d’objets connectés. Le système doit être capable de communiquer avec les objets connectés en Zigbee et/ou avec les protocoles en 433 et 868 Mhz car les équipements que nous aurons ne pourrons communiquer qu’avec ces protocoles. Cela couvre de nombreux protocoles (voir état de l’art). Chaque membre d’une famille devra créer son propre compte qui contrôlera les objets de la maison et il ne sera pas possible de connecter plusieurs personnes au même compte. Il y aura potentiellement des soucis si plusieurs personnes veulent allumer ou éteindre une lampe, et nous allons donc devoir définir des droits utilisateurs pour contrer ce problème.</p>

![image](/assets/Serveur.png)  

  <p style="text-align:justify;"><strong>La partie traitement du langage : </strong>Pour cette partie, il faudra prévoir un ou plusieurs Raspberry qui recevront les demandes utilisateurs via le serveur et les traiteront afin de renvoyer la demande programme au serveur. Le fonctionnement de cette partie sera basé sur un réseau de neurones (voir état de l’art). Ce réseau de neurones devra nous permettre de réaliser les fonctionnalités décrites ci-dessous.</p>

![image](/assets/Traitement.png)

<p style="text-align:justify;"><strong>Les objets connectés : </strong>Le boîtier contrôlera des équipements. Il faudra donc, avant tout, que la maison soit équipée en objets connectés. Ils devront être capable de communiquer avec la partie serveur en indiquant tous types de données à propos d’eux-mêmes. Ils devront donc pouvoir communiquer en Zigbee et/ou avec les protocoles 433 et 868Mhz (la raison est expliquée dans la partie serveur). Le boîtier devra être capable de commander tous types d’objets connectés tels que des lampes, des volets... Il n’y a pas de fonctionnalités spéciales à implémenter dans cette partie. Il faudra cependant faire attention à la compatibilité des protocoles de transmissions entre notre partie serveur et les objets connectés.</p>
