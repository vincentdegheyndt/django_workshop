# L'application Instaclone

1. [Installation de Python-Django](../README.md)
2. [Création de l'app](creationappli.md)
3. [Structure](structure.md)
4. [Media](media.md)
5. [PostgreSQL](postgresql.md)
6. [CSS](css.md)
7. [Formulaire](formulaire.md)
   

## La création d'application

Quand on lance un projet, un dossier se crée ainsi qu'un sous-dossier du même nom. Pour créer une application (un blog, une page e-commerce, etc) dans ce projet, on tape la commande suivante à la racine où se trouve `manage.py`:

    ./manage.py startapp gallery


Si vous êtes curieux, je vous invite à lire ce qui suit. Sinon, scrollez jusqu'à l'image du paresseux. 

Voici l'arborescence du projet avant d'installer l'application:

![arborescence de base](img/arborescence.png)



Á la racine, on a donc `manage.py` qui est le script de gestion du projet et qu'on va appeler à chaque fois qu'on veut faire tourner le serveur. 

Dans le sous-dossier du projet, on trouve :
-  `__init__.py`: un fichier qui initialise un paquet et dit à python de traiter les sous-dossiers comme des modules (en gros). 
- `settings.py` qui contient toute la configuration de base du projet.
`urls.py`:  qui contient la configuration des urls, of course.
- `wsgi.py`: on se s'en occupe pas pour le moment ; c'est pour déployer le projet sur d'autres serveurs.

Allons maintenant fouiller dans le dossier de l'application qui apparait après qu'on ait executé la commande `startapp`: 

![arborescence de l'application](img/appliarbo.png)

Tout d'abord, on y voit un dossier "migrations" qui permet à Django de migrer d'un coup de baguette magique le code python à la base de donnée. Ensuite, nous avons :

 - `admin.py`: qui permet d'ajouter, supprimer et modifier du contenu dans l'interface admin de Django. 
 - `apps.py`: où se trouvent les classes de configuration spécifiques à chaque application.
 - `models.py`: qui communique avec la base de données.
 - `views.py`: code de gestion des requêtes/réponses.
 - `tests.py`: pour automatiser les tests dans le code et éviter les bugs. On ne le verra pas dans ce tutoriel. 
 
 Mais où allons-nous mettre le code HTML, te demandes-tu ? Les templates ? Vous allez voir :) 

![image du paresseux](img/paresseux.jpg)

Coucou toi! Bien dormi ? On reprend ! 


Après avoir installé l'application et pour que tout fonctionne bien, on l'indique dans `settings.py` dans le dossier du projet:

    'gallery.apps.GalleryConfig', 

!['installed apps'](img/installedapps.png)

Tu peux maintenant passer à la structure de ton app.: [structure](structure.md).
