# Liste de filtres d'affichage (display filters) 
Essentiels pour Wireshark, organisée par catégorie pour une utilisation plus facile.

## Protocoles de base
|Filtre|	Description|	Exemple(s) d'utilisation|
|:-:|:-:|:-:|
|`tcp`, `udp`, `icmp`|	Affiche les paquets d'un protocole de transport ou de contrôle spécifique.|`tcp` : pour voir seulement les paquets TCP.|
|`arp`|	Isole les paquets du protocole de résolution d'adresse.|`arp`|
|`dns`, `http`, `ssh`, `tls`|Filtre les paquets des protocoles applicatifs courants.	|`dns` : pour analyser les requêtes DNS.<br>http : pour le trafic web non-chiffré.|


## Hôtes, ports et adresses
|Filtre	|Description	|Exemple(s) d'utilisation|
|:-:|:-:|:-:|
|`ip.addr == <adresse_ip>`|	Affiche le trafic en provenance ou à destination d'une adresse IP donnée.	|`ip.addr == 192.168.1.1`|
|`ip.src == <adresse_ip>`|Filtre le trafic dont la source est l'IP spécifiée.	|`ip.src == 10.0.0.5`|
|`ip.dst == <adresse_ip>`|Filtre le trafic dont la destination est l'IP spécifiée.|`ip.dst == 8.8.8.8`|
|`tcp.port == <numéro_port>`|	Affiche les paquets dont le port source ou le port de destination est celui spécifié.|`tcp.port == 80`|
|`tcp.srcport == <numéro_port>`|Filtre par port source TCP.|`tcp.srcport == 443`|
|`eth.addr == <adresse_mac>`|Filtre le trafic par adresse MAC.|`eth.addr == 00:1a:2b:3c:4d:5e`|


## Opérateurs logiques et de comparaison
|Filtre|	Description	|Exemple(s) d'utilisation|
|:-:|:-:|:-:|
|`and`, `or`|Combine plusieurs conditions.|`ip.addr == 192.168.1.1 and tcp.port == 80`|
|`not` ou `!`|	Inverse le résultat d'un filtre.	|`not arp` : exclut tout le trafic ARP.|
|`==`, `!=`|	Compare une valeur.|`http.response.code == 404` : pour voir les erreurs "Not Found".|
|`>`, `<`, `>=`, `<=`|	Compare des valeurs numériques.	|`frame.len > 1500` : pour les paquets dont la taille est supérieure à 1500 octets.|


##Champs spécifiques et contenus
|Filtre|	Description|	Exemple(s) d'utilisation|
|:-:|:-:|:-:|
|`dns.qry.name == "google.com"`|	Filtre par nom de domaine dans une requête DNS.	|`dns.qry.name contains "google.com"`|
|`http.request.method == "POST"`|	Isole les requêtes HTTP de type POST.	|`http.request.method == "GET"`|
|`http.response.code >= 400`|	Affiche toutes les réponses HTTP qui sont des erreurs.|`http.response.code`|
|`frame contains "password"`|	Recherche une chaîne de caractères dans la charge utile de n'importe quel paquet.|`http contains "user"`|
