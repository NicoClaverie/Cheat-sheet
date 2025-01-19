
# Docker Cheat Sheet

## Qu'est-ce que Docker ?
**Docker** est une plateforme open-source conçue pour automatiser le déploiement d'applications dans des **conteneurs logiciels**. Ces conteneurs permettent aux développeurs d’empaqueter une application avec toutes ses dépendances pour garantir un fonctionnement uniforme sur différents environnements.

## Fonctionnalités Clés :
- **Portabilité** : Fonctionne de manière identique peu importe l’environnement (développement, test, production).
- **Isolation** : Chaque conteneur est isolé des autres, améliorant la sécurité et la stabilité.
- **Efficacité** : Démarrage rapide des conteneurs et meilleure utilisation des ressources.

## Installation et Configuration :
1. Dans une fenêtre terminal, exécuter les commandes suivantes :
    ```
    1 Add Docker's official GPG key :  
    sudo apt-get update  
    sudo apt-get install ca-certificates curl
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc

    2 Add the repository to Apt sources:
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
    ```

2. Vérifier que **Docker CLI** est installé :
    ```
    docker --version
    ```

3. Vérifier que Docker est installé et fonctionne avec une image
    ```
    sudo docker run hello-world
    ```

## Commandes Générales :
- Démarrer Docker :
    ```
    sudo systemctl start docker
    ```
- Vérifier le statut de Docker :
    ```
    sudo systemctl status docker
    ```

## Commande Docker Run :
- Exécuter un conteneur :
    ```
    docker run <image_name>
    ```

### Exemples pratiques :
- Lancer un conteneur en mode interactif avec un terminal bash :
    ```
    docker run -it <image_name> /bin/bash
    ```

- Lancer un conteneur en arrière-plan (détaché) :
    ```
    docker run -d <image_name>
    ```

- Lancer un conteneur et mapper un port local avec celui du conteneur :
    ```
    docker run -d -p 5000:80 <image_name>
    ```

- Monter un volume dans le conteneur :
    ```
    docker run -v /path/local:/path/container <image_name>
    ```

- Nommer un conteneur lors du lancement :
    ```
    docker run --name <container_name> <image_name>
    ```

## Gestion des Conteneurs :
- Lister tous les conteneurs :
    ```
    docker ps -a
    ```

- Démarrer un conteneur existant :
    ```
    docker start <container_id>
    ```

- Arrêter un conteneur :
    ```
    docker stop <container_id>
    ```

- Supprimer un conteneur :
    ```
    docker rm <container_id>
    ```

## Gestion des Images Docker :
- Lister toutes les images Docker locales :
    ```
    docker images
    ```

- Télécharger une image Docker (pull) :
    ```
    docker pull <image_name>
    ```

- Construire une image Docker à partir d’un Dockerfile :
    ```
    docker build -t <image_name> .
    ```

- Supprimer une image Docker :
    ```
    docker rmi <image_id>
    ```

## Gestion des Volumes Docker :
- Lister tous les volumes :
    ```
    docker volume ls
    ```

- Créer un volume :
    ```
    docker volume create <volume_name>
    ```

- Supprimer un volume :
    ```
    docker volume rm <volume_name>
    ```

## Nettoyage des Ressources avec Docker Prune :
- Nettoyer les conteneurs, images et volumes non utilisés :
    ```
    docker system prune
    ```

Cette commande supprime :
- Les conteneurs arrêtés
- Les réseaux non utilisés
- Les images **dangling** (non taggées ou non associées à un conteneur)
- Les caches de build non utilisés

### Options supplémentaires :
- Pour nettoyer les volumes également :
    ```
    docker system prune --volumes
    ```

- Forcer la suppression sans confirmation :
    ```
    docker system prune -f
    ```

- Nettoyage ciblé (par exemple, les conteneurs) :
    ```
    docker container prune
    ```

- Supprimer uniquement les images non utilisées :
    ```
    docker image prune
    ```

- Supprimer uniquement les volumes inutilisés :
    ```
    docker volume prune
    ```
## Lien externe

https://docs.docker.com/engine/install/ubuntu/  

https://blog.stephane-robert.info/docs/conteneurs/moteurs-conteneurs/docker/

https://linux-man.fr/index.php/2021/03/04/docker-network/

https://blog.alphorm.com/reseaux-docker-guide-complet

https://blog.stephane-robert.info/docs/conteneurs/moteurs-conteneurs/lazydocker/
