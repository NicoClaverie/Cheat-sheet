| Commande                                                | Description                                                   |
| ------------------------------------------------------- | ------------------------------------------------------------- |
| `docker network ls`                                     | Liste tous les réseaux Docker disponibles.                    |
| `docker network inspect <nom_du_réseau>`                | Affiche les détails d'un réseau spécifique.                   |
| `docker network create <nom_du_réseau>`                 | Crée un réseau personnalisé.                                  |
| `docker network rm <nom_du_réseau>`                     | Supprime un réseau spécifié.                                  |
| `docker network connect <nom_du_réseau> <conteneur>`    | Connecte un conteneur à un réseau existant.                   |
| `docker network disconnect <nom_du_réseau> <conteneur>` | Déconnecte un conteneur d'un réseau.                          |
| `docker run --network=<nom_du_réseau>`                  | Démarre un conteneur en le connectant à un réseau spécifique. |
| `docker network prune`                                  | Supprime tous les réseaux non utilisés.                       |


# Commandes Docker

| Catégorie                | Commande                                       | Description                                                                 |
|--------------------------|-----------------------------------------------|-----------------------------------------------------------------------------|
| **Images**               | `docker images`                               | Liste les images disponibles localement.                                   |
|                          | `docker pull <image>`                         | Télécharge une image depuis un registre (par défaut Docker Hub).           |
|                          | `docker push <image>`                         | Envoie une image vers un registre.                                         |
|                          | `docker build -t <image> .`                   | Construit une image à partir d'un `Dockerfile`.                            |
|                          | `docker rmi <image>`                          | Supprime une image locale.                                                 |
|                          | `docker tag <source> <cible>`                 | Ajoute un tag à une image.                                                 |
|                          | `docker save -o <fichier.tar> <image>`        | Sauvegarde une image dans un fichier.                                      |
|                          | `docker load -i <fichier.tar>`                | Charge une image depuis un fichier.                                        |
| **Conteneurs**           | `docker ps`                                   | Liste les conteneurs en cours d'exécution.                                 |
|                          | `docker ps -a`                                | Liste tous les conteneurs (actifs et stoppés).                             |
|                          | `docker run <image>`                          | Lance un conteneur depuis une image.                                       |
|                          | `docker run -d <image>`                       | Lance un conteneur en arrière-plan (mode détaché).                         |
|                          | `docker run --name <nom> <image>`             | Lance un conteneur avec un nom spécifique.                                 |
|                          | `docker stop <conteneur>`                     | Arrête un conteneur en cours d'exécution.                                  |
|                          | `docker start <conteneur>`                    | Démarre un conteneur stoppé.                                               |
|                          | `docker restart <conteneur>`                  | Redémarre un conteneur.                                                    |
|                          | `docker rm <conteneur>`                       | Supprime un conteneur arrêté.                                              |
|                          | `docker logs <conteneur>`                     | Affiche les logs d'un conteneur.                                           |
|                          | `docker exec -it <conteneur> <commande>`      | Exécute une commande dans un conteneur en cours d'exécution.               |
|                          | `docker attach <conteneur>`                   | Attache votre terminal à un conteneur en cours d'exécution.                |
|                          | `docker export <conteneur> > <fichier.tar>`   | Exporte le système de fichiers d'un conteneur dans un fichier tar.         |
|                          | `docker import <fichier.tar>`                 | Importe un fichier tar en tant qu'image.                                   |
| **Réseaux**              | `docker network ls`                           | Liste les réseaux Docker disponibles.                                      |
|                          | `docker network inspect <nom>`                | Affiche les détails d'un réseau spécifique.                                |
|                          | `docker network create <nom>`                 | Crée un réseau personnalisé.                                               |
|                          | `docker network rm <nom>`                     | Supprime un réseau.                                                        |
|                          | `docker network connect <nom> <conteneur>`    | Connecte un conteneur à un réseau.                                         |
|                          | `docker network disconnect <nom> <conteneur>` | Déconnecte un conteneur d'un réseau.                                       |
|                          | `docker network prune`                        | Supprime tous les réseaux non utilisés.                                    |
| **Volumes**              | `docker volume ls`                            | Liste les volumes Docker.                                                  |
|                          | `docker volume inspect <nom>`                 | Affiche les détails d'un volume spécifique.                                |
|                          | `docker volume create <nom>`                  | Crée un volume personnalisé.                                               |
|                          | `docker volume rm <nom>`                      | Supprime un volume.                                                        |
|                          | `docker volume prune`                         | Supprime tous les volumes non utilisés.                                    |
| **Systèmes**             | `docker system df`                            | Affiche l'espace utilisé par Docker (images, conteneurs, volumes, etc.).   |
|                          | `docker system prune`                         | Nettoie les ressources inutilisées (images, conteneurs, réseaux, etc.).    |
|                          | `docker info`                                 | Affiche des informations détaillées sur l'installation Docker.             |
|                          | `docker version`                              | Affiche les versions du client et du serveur Docker.                       |

# Options principales pour `docker run`

| Option                                 | Description                                                                                          |
|----------------------------------------|------------------------------------------------------------------------------------------------------|
| `--name <nom>`                         | Attribue un nom au conteneur.                                                                        |
| `-d`                                   | Exécute le conteneur en arrière-plan (mode détaché).                                                 |
| `-it`                                  | Lance un conteneur en mode interactif avec un terminal attaché.                                      |
| `--rm`                                 | Supprime automatiquement le conteneur après son arrêt.                                               |
| `-p <hôte:conteneur>`                  | Mappe un port du conteneur à un port de l’hôte.                                                      |
| `-P`                                   | Mappe automatiquement les ports exposés du conteneur vers des ports aléatoires sur l'hôte.           |
| `-v <hôte:conteneur>`                  | Monte un volume (ou un chemin local) dans le conteneur.                                              |
| `--mount type=bind,source=<src>,target=<dst>` | Monte un répertoire ou un fichier spécifique avec une configuration avancée.                        |
| `--network <nom>`                      | Spécifie le réseau Docker à utiliser pour le conteneur.                                              |
| `--env <clé=valeur>` ou `-e <clé=valeur>` | Passe une variable d'environnement au conteneur.                                                   |
| `--env-file <fichier>`                 | Charge un fichier contenant des variables d'environnement.                                           |
| `--restart <politique>`                | Définit la politique de redémarrage (`no`, `always`, `on-failure`, `unless-stopped`).                |
| `--cap-add <cap>`                      | Ajoute une capacité Linux spécifique au conteneur.                                                  |
| `--cap-drop <cap>`                     | Supprime une capacité Linux spécifique du conteneur.                                                |
| `--privileged`                         | Donne au conteneur tous les privilèges (accès étendu au système hôte).                               |
| `--cpu-shares <valeur>`                | Définit la priorité CPU relative du conteneur.                                                      |
| `--memory <valeur>`                    | Limite l'utilisation de la mémoire pour le conteneur.                                               |
| `--hostname <nom>`                     | Définit le nom d'hôte (hostname) du conteneur.                                                      |
| `--entrypoint <commande>`              | Redéfinit le point d'entrée (`ENTRYPOINT`) de l'image Docker.                                        |
| `--user <utilisateur>`                 | Exécute le conteneur en tant qu'utilisateur ou groupe spécifique.                                    |
| `--detach-keys <combinaison>`          | Redéfinit la combinaison de touches pour détacher le conteneur (par défaut : `Ctrl+P`, `Ctrl+Q`).    |
| `--log-driver <driver>`                | Spécifie le pilote de journalisation (exemple : `json-file`, `syslog`, `journald`).                  |
| `--device <chemin>`                    | Ajoute un périphérique hôte au conteneur (comme une carte graphique ou un périphérique USB).         |
| `--tmpfs <chemin>`                     | Monte un système de fichiers temporaire (`tmpfs`) dans le conteneur.                                |
| `--ipc <mode>`                         | Configure les espaces IPC (`shareable`, `private`, etc.).                                            |
| `--pid <mode>`                         | Définit l'espace PID à utiliser (`host`, `container:<nom>`).                                         |
| `--uts <mode>`                         | Configure l'espace UTS pour le conteneur (`host`, etc.).                                             |
| `--security-opt <option>`              | Applique une option de sécurité (comme `no-new-privileges`).                                         |
| `--workdir <chemin>`                   | Définit le répertoire de travail par défaut du conteneur (`WORKDIR`).                                |
| `--health-cmd <commande>`              | Définit une commande de vérification de l'état (health check) pour le conteneur.                    |
| `--health-interval <durée>`            | Spécifie l'intervalle entre les vérifications de santé.                                              |
| `--health-retries <nombre>`            | Définit le nombre de tentatives pour la vérification de santé avant de considérer un échec.          |
| `--health-start-period <durée>`        | Définit une période de grâce avant de commencer les vérifications de santé.                          |
| `--health-timeout <durée>`             | Définit la durée maximale pour une vérification de santé.                                            |
| `--volume-driver <driver>`             | Spécifie le pilote de volume à utiliser pour les volumes montés.                                     |
| `--read-only`                          | Lance le conteneur avec un système de fichiers en lecture seule.                                     |


### Commandes générales sur les réseaux


#### 1. Lister les réseaux existants :



```
docker network ls
``` 

Affiche tous les réseaux Docker disponibles (par défaut : bridge, host, none).

#### 2. Créer un nouveau réseau :

```
docker network create <nom_du_réseau>
```

Crée un réseau personnalisé (par défaut de type `bridge`).

Options courantes :

Spécifier un type de réseau :
```
docker network create --driver <bridge|overlay|macvlan|none> <nom_du_réseau>
```
Exemple avec un sous-réseau :
```
docker network create --subnet=192.168.1.0/24 mon_reseau
```
#### 3. Inspecter un réseau :

```
docker network inspect <nom_du_réseau>
```
Donne des informations détaillées sur un réseau (conteneurs connectés, IP, sous-réseau, etc.).

Supprimer un réseau :

bash
Copier le code
docker network rm <nom_du_réseau>
Supprime un réseau (si aucun conteneur ne l'utilise).

Prune des réseaux inutilisés :

bash
Copier le code
docker network prune
Supprime tous les réseaux non utilisés par des conteneurs actifs.

Gérer les conteneurs avec les réseaux
Connecter un conteneur à un réseau :

bash
Copier le code
docker network connect <nom_du_réseau> <nom_du_conteneur>
Ajoute un conteneur existant à un réseau.

Déconnecter un conteneur d'un réseau :

bash
Copier le code
docker network disconnect <nom_du_réseau> <nom_du_conteneur>
Retire un conteneur d'un réseau.

Exemple de configuration avancée
Créer un réseau bridge personnalisé avec une plage IP spécifique :

bash
Copier le code
docker network create \
  --driver bridge \
  --subnet=192.168.100.0/24 \
  mon_bridge
Lancer un conteneur sur un réseau personnalisé :

bash
Copier le code
docker run --rm --network=mon_bridge --name mon_conteneur nginx
Créer un réseau macvlan pour accéder directement au réseau physique :

bash
Copier le code
docker network create \
  --driver macvlan \
  --subnet=192.168.1.0/24 \
  --gateway=192.168.1.1 \
  -o parent=eth0 \
  mon_macvlan
Vérification rapide des réseaux et des IP des conteneurs
Afficher les IP des conteneurs connectés :
bash
Copier le code
docker network inspect <nom_du_réseau> | jq '.[0].Containers'