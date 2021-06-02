# TP XSS CSRF
Organisateurs : Restoy Esteban, Janvier Victor, Coutard Antoine et Demourgues Lise.
Le cours est disponible ici : https://xsslearner.herokuapp.com/

Prérequis :
 - git
 - heroku [https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

Pour realiser ce tp, il vous est demande de forker ce repository dans votre espace github.
<img width="397" alt="image" src="https://user-images.githubusercontent.com/57868321/120502142-780b2480-c3c2-11eb-9b45-9bfcf2790067.png">

C'est dans ce nouveau repo que vous travaillerez. 
C'est egalement le lien de ce nouveau repo que vous devrez nous renvoyer pour etre corrige.
Merci de bien penser a laisser le repo en public sinon nous ne pourrons vous corriger.
Merci de renommer le projet comme suit : `xss-csrf-nom-prenom`

Ce repository est compose :
 - d'un README, votre guideline et sujet de TP.
 - d'un dossier xss
 - d'un dossier csrf

Tout au long du TP, des questions vous seront posees, merci de creer un markdown comme suit : 
```
touch reponses-nom-prenom.md
```

## Partie 1 - XSS - 13 points

Rendez-vous sur l'application suivante https://xss-csrf-tp.herokuapp.com/ et creez vous un compte.
Pour se creer un compte entrer juste un user, votre prenom de preference.

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



1. Essayer d'injecter du code sans passer par un formulaire.  1 point 
1. Essayer de récupérer la session de l'utilisateur via une injection xss et de les envoyer sur heroku la faille est vraiment visible, essayer de la camoufler 3 points

### Level 3 : 4 points

1. Bypass le filter Qui enlebera les balise scripts imagez body  ...  2 points
<img>denaduegdduya
Faire un keylogger simple en js qui appelle le lien sur heroku  2 points


## Partie 2 - CSRF - 7 points

```
cd csrf
git init
git add .
git commit -m “deploying on heroku” 
heroku login 
heroku apps:create my-malicious-website-<nom> exemple my-malicious-website-restoy
git push heroku main
```

N'oubliez pas d'insérer des données à chaque fois pour que vous puissiez voir si votre attaque fonctionne car la route que vous allez appeler ne fais que reset la base de donnée à l'état d'origine.

1. Avoir un site heroku fonctionnel (2 points)

2. Monter une attaque CSRF qui permet de rediriger sur : "<<URL>>" grâce à un formulaire (2 points)

3. Avoir une redirection visible c'est pas très "propre" comme attaque.
Faites donc en sorte de masquer cette redirection pour que l'utilisateur ait l'impression de rester sur votre site malicieux. (3 points)
  
