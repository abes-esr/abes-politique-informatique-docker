# politique-informatique-docker

[![Docker Pulls](https://img.shields.io/docker/pulls/abesesr/abes-politique-informatique.svg)](https://hub.docker.com/r/abesesr/abes-politique-informatique/)

Configuration docker 🐳 pour déployer le site web https://politique-informatique.abes.fr  
Le code source et le contenu du site est disponible ici : https://github.com/abes-esr/abes-politique-informatique

## URLs

Les URLs correspondantes aux déploiements en local, dev, test et prod sont les suivantes :

- local :
    - http://127.0.0.1:28940/
    - http://127.0.0.1:3000/ (c'est l'URL par défaut lorsque l'on démarre docusaurus en mode développement avec ``npm start``)
- dev (sous vpn) :
    - https://politique-informatique-dev.abes.fr
    - http://diplotaxis6-dev.v212.abes.fr:28940/
- test (sous vpn) :
    - https://politique-informatique-test.abes.fr
    - http://diplotaxis6-test.v202.abes.fr:28940/
- prod
    - https://politique-informatique.abes.fr
    - http://diplotaxis6-prod.v102.abes.fr:28940/

## Prérequis

Disposer de :
- ``docker``
- ``docker-compose``

## Installation

Déployer la configuration docker dans un répertoire :
```bash
# adaptez /opt/pod/ avec l'emplacement où vous souhaitez déployer l'application
cd /opt/pod/
git clone https://github.com/abes-esr/abes-politique-informatique-docker.git
```

Configurer l'application depuis l'exemple du fichier [``.env-dist``](./.env-dist) (ce fichier contient la liste des variables avec des explications et des exemples de valeurs) :
```bash
cd /opt/pod/abes-politique-informatique-docker/
cp .env-dist .env
# personnaliser alors le contenu du .env
```

Démarrer l'application :
```bash
cd /opt/pod/abes-politique-informatique-docker/
docker-compose up -d
```

## Démarrage et arrêt

```bash
# pour démarrer l'application (ou pour appliquer des modifications 
# faites dans /opt/pod/abes-politique-informatique-docker/.env)
cd /opt/pod/abes-politique-informatique-docker/
docker-compose up -d
```

Remarque : retirer le ``-d`` pour voir passer les logs dans le terminal et utiliser alors CTRL+C pour stopper l'application

```bash
# pour stopper l'application
cd /opt/pod/abes-politique-informatique-docker/
docker-compose stop


# pour redémarrer l'application
cd /opt/pod/abes-politique-informatique-docker/
docker-compose restart
```

## Supervision

```bash
# pour visualiser les logs de l'appli
cd /opt/pod/abes-politique-informatique-docker/
docker-compose logs -f --tail=100
```

Cela va afficher les 100 dernières lignes de logs générées par l'application et toutes les suivantes jusqu'au CTRL+C qui stoppera l'affichage temps réel des logs.


## Configuration

Pour configurer l'application, vous devez créer et personnaliser un fichier ``/opt/pod/abes-politique-informatique-docker/.env`` (cf section [Installation](#installation)). Les paramètres à placer dans ce fichier ``.env`` et des exemples de valeurs sont indiqués dans le fichier [``.env-dist``](https://github.com/abes-esr/abes-politique-informatique-docker/blob/develop/.env-dist)

## Sauvegardes

Les éléments suivants sont à sauvegarder:
- ``/opt/pod/abes-politique-informatique-docker/.env`` : contient la configuration spécifique de notre déploiement

### Restauration depuis une sauvegarde

Réinstallez l'application politique-developpement depuis la [procédure d'installation ci-dessus](#installation) et récupéré depuis les sauvegardes le fichier ``.env`` et placez-le dans ``/opt/pod/abes-politique-informatique-docker/.env`` sur la machine qui doit faire repartir politique-developpement.

