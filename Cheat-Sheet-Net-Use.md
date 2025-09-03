# Cheat Sheet - Commande `net use` sous Windows

| Commande | Description |
|----------|------------|
| `net use` | Affiche les lecteurs réseau actuellement connectés. |
| `net use X: \\serveur\partage /user:nom_utilisateur "mot_de_passe"` | Connecte un lecteur réseau avec authentification. |
|`net use X: \\serveur\partage /user:DOMAIN\nom_utilisateur "mot_de_passe"`|Connecte un lecteur réseau avec authentification Active Directory. |
| `net use X: \\serveur\partage /persistent:yes` | Connecte un lecteur réseau et le rend persistant. |
| `net use X: /delete` | Déconnecte le lecteur `X:`. |
| `net use * /delete /y` | Déconnecte toutes les connexions réseau sans confirmation. |
| `net use \\serveur\partage /user:nom_utilisateur mot_de_passe` | Accède à un partage sans mapper un lecteur. |
| `net use LPT1: \\serveur\imprimante /persistent:yes` | Connecte une imprimante réseau à `LPT1:`. |
| `net use LPT1: /delete` | Supprime la connexion à l’imprimante. |
| `net use X: /status` | Affiche l’état de la connexion réseau. |

---
Ce tableau résume les principales commandes `net use` pour gérer les connexions réseau et imprimantes sous Windows.
