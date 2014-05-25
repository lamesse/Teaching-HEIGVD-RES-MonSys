Welcome
============================

This repo is used for the Web Infrastructure lab. Fork and clone it.

1. Arnaud Desclouds et Antoine Messerli

2. URL du fork : https://github.com/lamesse/Teaching-HEIGVD-RES-MonSys.git


3. Contenu du fichier host :

	192.168.33.20	www.monsys.com

	192.168.33.20	live.clashofclasses.ch

	192.168.33.20	leaderboard.clashofclasses.ch 


4. Etat des lieux :

Tout fonctionne correctement, nous sommes arrivés au bout du labo.

5. Capture d'écran : 

![](/img/live.jpg)

![](/img/leader.jpg)

6. Fichiers modifiés :

monsys-web-infra/Vagranfile : modification pour avoir trois dockers de plus + changement du port public

monsys-web-infra/docker : ajout d'un dossier web-clash qui est au départ une copie de web-apache

monsys-web-infra/docker/web-clash/site-config : ajout de leaderboard.clashofclasses.ch.conf et de live.clashofclasses.ch.conf Ces fichiers contiennent les configurations des deux virtual host, utilisés par les les dockers web-clash.

monsys-web-infra/docker/web-clash/site-content : création de deux répertoires : leaderboard.clashofclasses.ch et live.clashofclasses.ch. Ils contiennent le contenu des deux sites.

monsys-web-infra/docker/rp-nginx/etc/nginx/sites-enables : modification du fichier default, pour faire fonctionner les deux sites supplémentaires.
