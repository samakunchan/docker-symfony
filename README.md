# Docker Symfony

C'est un projet qui permet de lancer un container afin d'installer le framework Symfony comme moi je l'entends.
<br> Quand moi j'installe Symfony, j'installe Symfony + une base de donnée, c'est tout. 
<br> Je n'installe pas tout ce qui est Traefik, mailer, tartanpion. Je le fais uniquement si j'en ai besoin. 
<br> C'est comme ça aussi que j'arrive le mieux à comprendre les évolutions technologiques et les choix qui ont été fait

## Pré-requis:
- Docker: [Lien d'installation](https://docs.docker.com/compose/install/)
- Créer votre fichier `.env` avec le fichier d'exemple `.env.exemple` à la racine.

## Installation

Build le projet et attendre un moment:

    docker-compose build --pull --no-cache

Et quand c'est fini:

    docker compose up -d

Se rendre dans le container avec la commande ci-dessous pour créer un projet

    docker exec -it server /bin/sh

**TOUT SE FAIT DEPUIS CE CONTAINER MAINTENANT**
<br>**OU**
<br>**UTILISER LE DOCKER DESKTOP**

---
## Créer son projet

- From scratch: 

  `symfony new .`

- Projet existant:
  <br>`git clone .`
  <br>`composer install`

## Installer ORM
Le pack ORM a son propre docker du coup, il s'installe dans un second temps. À la question, si je veux mettre le projet sous docker, moi je met "non", il est déjà sous docker.

    composer require symfony/orm-pack

    Do you want to include Docker configuration from recipes?
    [y] Yes
    [n] No
    [p] Yes permanently, never ask again for this project
    [x] No permanently, never ask again for this project
    (defaults to y): n


## Utilisation
Avant d'utiliser symfony, n'oublie pas d'aller dans le `/project/.env` afin de modifier l'url de connexion à la base de donnée.

    Changer ceci:
    DATABASE_URL="mysql://app:!ChangeMe!@127.0.0.1:3306/app?serverVersion=8&charset=utf8mb4"    
    en:
    DATABASE_URL="mysql://[MYSQL_USER]:[MYSQL_ROOT_PASSWORD]@[NOM DU SERVICE DOCKER]:3306/[MYSQL_DATABASE]?serverVersion=8&charset=utf8mb4"
    (replacer les variables)
---
    symfony server:start    

- SERVER : [http://127.0.0.1:9000/](http://127.0.0.1:9000/)
- PHPMYADMIN : [http://127.0.0.1:8100/](http://127.0.0.1:8100/)
