# TP XSS CSRF
Organisateurs : Restoy Esteban, Janvier Victor, Coutard Antoine et Demourgues Lise.
Le cours est disponible ici : https://xsslearner.herokuapp.com/

Prérequis :
 - git
 - firefox
 - heroku [https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

Pour réaliser ce tp, il vous est demandé de forker ce repository dans votre espace github.
<img width="397" alt="image" src="https://user-images.githubusercontent.com/57868321/120502142-780b2480-c3c2-11eb-9b45-9bfcf2790067.png">

C'est dans ce nouveau repo que vous travaillerez. 
C'est également le lien de ce nouveau repo que vous devrez nous renvoyer pour être corrigé. 
Merci de bien penser à laisser le repo en public sinon nous ne pourrons vous corriger. 
Merci de renommer le projet comme suit : `xss-csrf-nom-prenom` 

Ce repository est composé :
 - d'un README, votre guideline et sujet de TP.
 - d'un dossier csrf

Tout au long du TP, des questions vous seront posées, merci de créer un markdown comme suit : 
```
touch reponses-nom-prenom.md
```
## Initiliation :

Executez ces commandes elle vous permettron de monter un serveur Heroku très rapidement (vous en avez besoin pour XSS => Level 2 Q5 & LEVEL 3 Q2 et pour la partie CSRF)

```zsh
cd csrf
git init
git add .
git commit -m “deploying on heroku” 
heroku login 
heroku apps:create my-malicious-website-<nom> // exemple my-malicious-website-restoy
git push heroku main
```

## Partie 1 - XSS - 13 points

Rendez-vous sur l'application suivante https://xss-csrf-tp.herokuapp.com/ et créez vous un compte. 
Pour se créer un compte : entrez un user, votre prenom de preference pour la correction.

### Level 1 : 2 points

Commencez par le niveau 1 : 
1. Essayez d'injecter du code sans passer par un formulaire.  2 points

### Level 2 : 7 points

(Ecrire dans le compte rendu les différents scripts injectés)
1. Injectez dans le formulaire de creation d'article (a droite) un script permettant d'afficher une alerte. 1 point
2. Pourquoi la balise script ne fonctionne pas ? 2 points 
3. Comment les donnees en base sont récupérées sur la page ? 1 point
4. Essayez de faire une injection XSS qui bloque totalement le bon fonctionnement du site il y a plusieurs réponses possibles. 2 points
5. Essayez de récupérer la session de l'utilisateur via une injection xss et de les envoyer sur heroku. Essayez de le faire de facon invisible  1 points

### Level 3 : 4 points

1. Rusez pour bypass le sanitizer 2 points
2. Faire un keylogger simple en js qui appelle le lien sur heroku  2 points

## Partie 2 - CSRF - 7 points

Trouvez un binôme de travail. Vous allez respectivement vous attaquer l'un l'autre.

Demandez a votre binôme de créer un article sur l'application (cf. level 2)

1. Avoir un site heroku fonctionnel. 2 points
2. Montez une attaque CSRF grâce à un formulaire. hint : https://xss-csrf-tp.herokuapp.com/articles/delete 2 points
Envoyez le lien de ce site malveillant à votre binôme et vérifiez que l'article qu'il a crée est supprimé.
4. Avoir une redirection visible c'est pas très "propre" comme attaque.
Faites donc en sorte de masquer cette attaque pour qu'elle soit invisible à l'utilisateur. 3 points

Bonus : si notre application est une API REST avec serialisation JSON. 
Donner le code du formulaire permettant d'envoyer un petit objet JSON comme suit :
```json
{ "account": 4 }
```
