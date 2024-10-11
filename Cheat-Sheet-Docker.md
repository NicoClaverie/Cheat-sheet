
# Docker Cheat Sheet

## Qu'est-ce que Docker ?
**Docker** est une plateforme open-source conçue pour automatiser le déploiement d'applications dans des **conteneurs logiciels**. Ces conteneurs permettent aux développeurs d’empaqueter une application avec toutes ses dépendances pour garantir un fonctionnement uniforme sur différents environnements.

## Fonctionnalités Clés :
- **Portabilité** : Fonctionne de manière identique peu importe l’environnement (développement, test, production).
- **Isolation** : Chaque conteneur est isolé des autres, améliorant la sécurité et la stabilité.
- **Efficacité** : Démarrage rapide des conteneurs et meilleure utilisation des ressources.

## Installation et Configuration :
1. Dans une fenêtre terminal, exécuter les commandes suivantes :
    ```bash
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo apt-add-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt update
    sudo apt install docker-ce docker-ce-cli containerd.io
    sudo docker --version
    ```

2. Vérifier que **Docker CLI** est installé :
    ```bash
    docker --version
    ```

## Commandes Générales :
- Démarrer Docker :
    ```bash
    sudo systemctl start docker
    ```
- Vérifier le statut de Docker :
    ```bash
    sudo systemctl status docker
    ```

## Commande Docker Run :
- Exécuter un conteneur :
    ```bash
    docker run <image_name>
    ```

### Exemples pratiques :
- Lancer un conteneur en mode interactif avec un terminal bash :
    ```bash
    docker run -it <image_name> /bin/bash
    ```

- Lancer un conteneur en arrière-plan (détaché) :
    ```bash
    docker run -d <image_name>
    ```

- Lancer un conteneur et mapper un port local avec celui du conteneur :
    ```bash
    docker run -d -p 5000:80 <image_name>
    ```

- Monter un volume dans le conteneur :
    ```bash
    docker run -v /path/local:/path/container <image_name>
    ```

- Nommer un conteneur lors du lancement :
    ```bash
    docker run --name <container_name> <image_name>
    ```

## Gestion des Conteneurs :
- Lister tous les conteneurs :
    ```bash
    docker ps -a
    ```

- Démarrer un conteneur existant :
    ```bash
    docker start <container_id>
    ```

- Arrêter un conteneur :
    ```bash
    docker stop <container_id>
    ```

- Supprimer un conteneur :
    ```bash
    docker rm <container_id>
    ```

## Gestion des Images Docker :
- Lister toutes les images Docker locales :
    ```bash
    docker images
    ```

- Télécharger une image Docker (pull) :
    ```bash
    docker pull <image_name>
    ```

- Construire une image Docker à partir d’un Dockerfile :
    ```bash
    docker build -t <image_name> .
    ```

- Supprimer une image Docker :
    ```bash
    docker rmi <image_id>
    ```

## Gestion des Volumes Docker :
- Lister tous les volumes :
    ```bash
    docker volume ls
    ```

- Créer un volume :
    ```bash
    docker volume create <volume_name>
    ```

- Supprimer un volume :
    ```bash
    docker volume rm <volume_name>
    ```

## Nettoyage des Ressources avec Docker Prune :
- Nettoyer les conteneurs, images et volumes non utilisés :
    ```bash
    docker system prune
    ```

Cette commande supprime :
- Les conteneurs arrêtés
- Les réseaux non utilisés
- Les images **dangling** (non taggées ou non associées à un conteneur)
- Les caches de build non utilisés

### Options supplémentaires :
- Pour nettoyer les volumes également :
    ```bash
    docker system prune --volumes
    ```

- Forcer la suppression sans confirmation :
    ```bash
    docker system prune -f
    ```

- Nettoyage ciblé (par exemple, les conteneurs) :
    ```bash
    docker container prune
    ```

- Supprimer uniquement les images non utilisées :
    ```bash
    docker image prune
    ```

- Supprimer uniquement les volumes inutilisés :
    ```bash
    docker volume prune
    ```
