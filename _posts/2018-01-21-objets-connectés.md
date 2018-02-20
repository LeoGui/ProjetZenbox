---
layout: post
title:  "Objets connectés"
date:   2018-01-21 16:16:01
categories: jekyll update
---

<p style="text-align:justify;">Les objets connectés que nous aurons à notre disposition seront des marques suivantes :</p>

- <p style="text-align:justify;"> Ikea. Ces équipements fonctionnent grâce au protocole Zigbee et communiquent avec
une box qui centralise tous les objets connectés de la marque. Cette box communique
avec l’application via le protocole CoAP encapsulé dans du HTTP. Nous avons deux
possibilités pour contrôler les objets connectés de la marque Ikea. Premièrement, nous
pouvons contrôler la box en utilisant Libcoap afin de “court-circuiter” les échanges
entre l’application et la box. La seconde possibilité est d'interagir en Zigbee
directement avec les objets connectés. Cela nous évite de devoir utiliser la box.</p>

- <p style="text-align:justify;">Sonoff : ces équipements fonctionnent par l'intermédiaire de cartes wifi intégrées. Il
est possible de modifier le code des équipements pour qu’ils puissent communiquer
avec notre partie serveur en ajoutant par exemple un client mqtt.</p>
