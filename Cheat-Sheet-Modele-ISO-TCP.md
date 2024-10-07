## Modèle OSI

| Couche             | Numéro | Description                                                                                       | Phrase clé                   | Mnémotechnie 1 | Mnémotechnie 2  |
| ------------------ | ------ | ------------------------------------------------------------------------------------------------- | ---------------------------- | -------------- | --------------- |
| Application        | 7      | Interface utilisateur et applications réseau, fournit les services de communication aux logiciels | Services aux applications    | Après          | Automatiquement |
| Présentation       | 6      | Traduction des données, chiffrement et compression                                                | Formatage des données        | Plusieurs      | Passe           |
| Session            | 5      | Gestion des sessions de communication entre applications                                          | Gestion des connexions       | Semaines       | Se              |
| Transport          | 4      | Transmission fiable des données, contrôle d'erreurs et flux                                       | Transport fiable             | Tout           | Tout            |
| Réseau             | 3      | Routage des paquets de données à travers des réseaux                                              | Adressage et routage         | Respire        | Réseau          |
| Liaison de données | 2      | Transfert de trames entre deux nœuds directement connectés                                        | Communication de nœud à nœud | La             | Le              |
| Physique           | 1      | Transmission des bits bruts sur un support physique                                               | Transmission physique        | Paix           | Pour            |


## Modèle TCP/IP

| Couche                    | Description                                                                                                        | Phrase clé                           |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------ |
| Application               | Interface utilisateur et applications réseau, protocoles tels que HTTP, FTP, SMTP                                  | Services aux applications            |
| Transport                 | Transmission fiable des données entre les hôtes, protocoles tels que TCP et UDP                                    | Transport fiable                     |
| Internet                  | Routage des paquets de données entre les réseaux, protocole IP (IPv4, IPv6)                                        | Adressage et routage                 |
| Accès réseau (ou liaison) | Communication sur le réseau physique, interfaces matérielles et protocoles de liaison de données (Ethernet, Wi-Fi) | Accès physique et liaison de données |


## Lien entre modèle OSI et TCP/IP

| Modèle OSI         | Couche OSI/TCP | Modèle TCP/IP              |
| ------------------ | -------------- | -------------------------- |
| Application        | 7/4            | Application                |
| Présentation       | 6/4            | (Inclus dans Application)  |
| Session            | 5/4            | (Inclus dans Application)  |
| Transport          | 4/3            | Transport                  |
| Réseau             | 3/2            | Internet                   |
| Liaison de données | 2/1            | Accès réseau (ou liaison)  |
| Physique           | 1/1            | (Inclus dans Accès réseau) |
