# TP XSS CSRF
Organisateurs : Restoy Esteban, Janvier Victor, Coutard Antoine et Demourgues Lise.
Le cours est disponible ici : https://xsslearner.herokuapp.com/

Prérequis :
 - git
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

## Partie 1 - XSS - 13 points

Rendez-vous sur l'application suivante https://xss-csrf-tp.herokuapp.com/ et créez vous un compte.
Pour se créer un compte : entrer juste un user, votre prenom de preference.

### Level 1 : 2 points

Commencez par le niveau 1 : 
1. Essayer d'injecter du code sans passer par un formulaire.  2 point 

### Level 2 : 7 points
1. Injecter dans le formulaire de creation d'article (a droite) un script permettant d'afficher une alerte. 1 point
2. Pourquoi la balise script ne fonctionne pas ? 2 points 
3. Comment les donnes en base sont récupérées sur la page 1 point
4. Essayer de faire une Injection XSS qui bloque totalement le bon fonctionnement du site ils y a plusieurs réponse possible. 3 points
5. Essayer de récupérer la session de l'utilisateur via une injection xss et de les envoyer sur heroku la faille est vraiment visible essayer de le faire de facon invisible  2 points
(Ecrire dans le compte rendu le script injecté)

### Level 3 : 4 points

1. Rusez pour bypass le sanitizer 2 points

## Partie 2 - CSRF - 7 points

Trouvez un binôme de travail. Vous allez respectivement vous attaquer l'un l'autre.

```zsh
cd csrf
git init
git add .
git commit -m “deploying on heroku” 
heroku login 
heroku apps:create my-malicious-website-<nom> // exemple my-malicious-website-restoy
git push heroku main
```
Demandez a votre binôme de créer un article sur l'application (cf. level 1)

1. Avoir un site heroku fonctionnel. 2 points
2. Monter une attaque CSRF grâce à un formulaire. hint : https://xss-csrf-tp.herokuapp.com/articles/delete 2 points
3. Avoir une redirection visible c'est pas très "propre" comme attaque.
Faites donc en sorte de masquer cette attaque pour qu'elle soit invisible à l'utilisateur. 3 points

Bonus : si l'on change la route pour supprimer un article par : https://xss-csrf-tp.herokuapp.com/articles/delete?id=x
et que notre application est une API REST avec serialisation JSON. 
Donner le code pdu formulaire permettant d'envoyer un petit objet JSON comme suit :
```json
{ account: id }
```
