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