# Guide d'Installation et d'Utilisation de Docker sur Debian

L'utilisation d'un conteneur permet d'empaqueter facilement des applications et de les tester rapidement sans affecter la machine hôte. Ce guide explique comment installer Docker via la méthode du dépôt officiel et présente les commandes de base pour débuter.

## I. Installation de Docker

### A. Installation des dépendances
Il est d'abord nécessaire de mettre à jour le cache des paquets et d'installer les dépendances requises au bon fonctionnement de Docker :
```bash
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg2
```

### B. Ajout du dépôt officiel Docker
Récupérez la clé GPG officielle, qui permettra de valider les paquets récupérés :
```bash
sudo curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
Ajoutez ensuite le dépôt officiel Docker à la liste des sources de votre machine Debian :
```bash
sudo echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```
Mettez à nouveau à jour le cache des paquets pour prendre en compte ce nouveau dépôt :
```bash
sudo apt-get update
```

### C. Installation des paquets Docker
Installez les trois paquets essentiels (le moteur Docker `docker-ce`, le client en ligne de commande `docker-ce-cli` et `containerd.io`) :
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
*(Optionnel)* Si vous souhaitez que le service Docker démarre automatiquement en même temps que votre machine :
```bash
sudo systemctl enable docker
```

### D. Vérification de l'installation
Vérifiez l'état du service Docker pour vous assurer qu'il est bien identifié sur la machine :
```bash
sudo systemctl status docker
```
Affichez la version de Docker actuellement installée :
```bash
docker --version
```
Pour confirmer que tous les composants fonctionnent parfaitement, téléchargez et exécutez le conteneur de test "hello-world" :
```bash
sudo docker run hello-world
```

---

## II. Commandes Docker Essentielles

Une fois installé sur votre serveur Debian, le client Docker permet de gérer les conteneurs et les images.

### Gestion des conteneurs
*   **Lister les conteneurs en cours d'exécution** :
    ```bash
    sudo docker ps
    ```
*   **Lister tous les conteneurs enregistrés** (peu importe qu'ils soient démarrés ou arrêtés) :
    ```bash
    sudo docker ps -a
    ```
*   **Démarrer un conteneur arrêté** (remplacez l'ID `d964015967b4` par celui de votre conteneur) :
    ```bash
    docker start d964015967b4
    ```
*   **Arrêter un conteneur en cours d'exécution** (remplacez l'ID `6108d7c37298`) :
    ```bash
    docker stop 6108d7c37298
    ```
*   **Supprimer un conteneur** (ex: suppression du conteneur test dont l'ID est `3c745b055853`) :
    ```bash
    docker rm 3c745b055853
    ```

### Gestion des images
*   **Télécharger une image à partir du Docker Hub** (ex: pour télécharger l'image Apache `httpd`) :
    ```bash
    docker pull httpd
    ```
*   **Lister les images disponibles localement** sur votre machine :
    ```bash
    docker images
    ```
*   **Supprimer une image Docker** (Attention : le conteneur associé doit avoir été arrêté et supprimé au préalable) :
    ```bash
    docker rmi hello-world
    ```

***

Source : https://www.it-connect.fr/installation-pas-a-pas-de-docker-sur-debian-11/
