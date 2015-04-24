Réaliser smarfooter + postclic
==============================

Le but de l'exercice est de réaliser en javascript un smartfooter qui au clic sur celui-ci ouvre un postclic Interstitiel.

Specs du smartfooter
---------------------
- format mobile responsive
- en overlay sur la page, au dessus du contenu
- ratio initial : 320x75
- fixe en bas du browser
- zone de clic sur l'ensemble de la bannière qui ouvre un postclic

optionnel:
- au "touch" sur le site publisher il disparait avec effet de slidedown. Il réapparait avec effet de slideUp lorsque l'utilisateur ne "touch" plus l'écran.
- après 10 interactions sur le site du publisher (10 touch), le format disparait


Specs de l'interstiel
---------------------

- format mobile responsive
- overlay
- ratio initial : 320x480
- prend toute la taille disponible dans le navigateur
- une croix de fermeture permet de fermer le format (http://storage.mozoo.com/creative_scripts/images/close_cross_official.svg)
- zone de clic sur l'ensemble du format ou sur un CTA (Clic To Action) définie dans la créative. 
- après le clic sur le CTA, l'interstiel doit être fermé.




Specs de nos formats
---------------------

- overlay
- responsive

Contraintes optionnelles:
- formats servis dans une iframe sur un domaine différent du publisher 
- formats servis par l'Adserver de manière assynchrone tout en ayant des scripts contenant la méthode document.write();



Etapes:
--------------------

1/ Implémenter en javascript natif une solution pour créer un smartfooter au chargement de la page qui répond aux spécs du smartfooter.

2/ Implémenter en javascript natif une solution pour créer le postclic Interstitiel après un clic sur le smartfooter.
L'utilisateur doit rester sur la page du publisher.

3/ Proposer des solutions pour les 2 contraintes optionnelles rencontrées pour la diffusion de nos formats:
- communication entre iframe de différents domaines 
- implémentation de script assynchrone avec la méthode document.write() 

Notes:
--------------------
Le format doit s'afficher correctement sur iPhone et sur un smartphone Android.


Réponses à la question 3
--------------------

- implémentation de script assynchrone avec la méthode document.write() :

Si l'Adserver fournit un format avec un script contenant la methode document.write(),
il risque d'y avoir un bug lors de la récupération du format de manière asynchrone en Ajax.
En effet le document.write() va surcharger la page avec son contenu et effacer le contenu déjà présent.
Il faut donc intercepter toute présence de document.write() dans le format, avec une regex par exemple,
et remplacer le document.write() par un element.innerHTML. 


