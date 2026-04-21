
# Cheat Sheet : Commandes `netsh` sous Windows

## ⚡ Introduction
`netsh` (Network Shell) est un outil en ligne de commande Windows pour configurer, gérer et dépanner les paramètres réseau.

---

## 🛠️ Commandes générales
| Commande                          | Description                                             |
|-----------------------------------|---------------------------------------------------------|
| `netsh help`                      | Affiche l’aide pour les commandes disponibles.          |
| `netsh interface show interfaces` | Liste les interfaces réseau et leur statut.             |
| `netsh wlan show all`             | Exécute un diagnostic réseau complet.                   |
| `netsh wlan show wlanreport`             | La commande la plus complète pour analyser les problèmes Wi-Fi récents. Elle génère un fichier HTML très détaillé.                   |

---

## 🌐 Configurations TCP/IP
| Commande                                        | Description                                                                 |
|------------------------------------------------|-----------------------------------------------------------------------------|
| `netsh int ip reset`                           | Réinitialise les paramètres TCP/IP.                                         |
| `netsh int ipv4 show config`                   | Affiche la configuration actuelle d’IPv4.                                   |
| `netsh int ipv6 reset`                         | Réinitialise les paramètres IPv6.                                           |
| `netsh int ipv4 set address`                   | Configure une adresse IP statique.                                          |
| `netsh interface ip set dns name=<interface>`  | Configure un serveur DNS pour une interface réseau.                         |

---

## 🔐 Sécurité et pare-feu
| Commande                                   | Description                                                                |
|-------------------------------------------|----------------------------------------------------------------------------|
| `netsh advfirewall show allprofiles`      | Affiche les paramètres du pare-feu pour tous les profils.                  |
| `netsh advfirewall reset`                 | Réinitialise toutes les règles du pare-feu.                                |
| `netsh advfirewall firewall add rule`     | Ajoute une règle de pare-feu (entrée/sortie).                              |
| `netsh advfirewall set allprofiles state off` | Désactive le pare-feu pour tous les profils réseau.                        |

---

## 🔗 Wi-Fi et réseaux sans fil
| Commande                                        | Description                                                                 |
|------------------------------------------------|-----------------------------------------------------------------------------|
| `netsh wlan show profiles`                     | Liste tous les profils Wi-Fi enregistrés.                                   |
| `netsh wlan show profile name=<NomProfil>`     | Affiche les détails d’un profil Wi-Fi spécifique.                           |
| `netsh wlan delete profile name=<NomProfil>`   | Supprime un profil Wi-Fi.                                                   |
| `netsh wlan start hostednetwork`               | Démarre un réseau Wi-Fi hébergé (mode hotspot).                             |
| `netsh wlan stop hostednetwork`                | Arrête un réseau Wi-Fi hébergé.                                             |

---

## ⚙️ Winsock
| Commande                    | Description                                                                     |
|-----------------------------|---------------------------------------------------------------------------------|
| `netsh winsock show catalog`| Affiche les fournisseurs de service Winsock.                                    |
| `netsh winsock reset`       | Réinitialise le catalogue Winsock aux paramètres par défaut.                    |

---

## 📡 Proxy
| Commande                            | Description                                                                 |
|-------------------------------------|-----------------------------------------------------------------------------|
| `netsh winhttp show proxy`          | Affiche la configuration actuelle du proxy.                                 |
| `netsh winhttp reset proxy`         | Supprime la configuration actuelle du proxy.                                |
| `netsh winhttp set proxy <proxy>`   | Configure un proxy spécifique (ex. `proxy.exemple.com:8080`).               |
| `netsh winhttp import proxy source=ie` | Importe les paramètres proxy d'Internet Explorer.                          |

---

## 💡 Commandes avancées
| Commande                                | Description                                                                 |
|-----------------------------------------|-----------------------------------------------------------------------------|
| `netsh interface ipv4 set subinterface` | Configure les paramètres spécifiques d’une sous-interface.                  |
| `netsh bridge show adapter`             | Affiche les adaptateurs réseau participant à un pont.                       |
| `netsh lan show interfaces`             | Affiche les interfaces réseau LAN.                                          |
| `netsh http show urlacl`                | Affiche les URL réservées pour le service HTTP.sys.                         |

---

## 🛑 Dépannage réseau
| Commande                                  | Description                                                                 |
|-------------------------------------------|-----------------------------------------------------------------------------|
| `netsh trace start capture=yes`           | Démarre une capture de trafic réseau.                                       |
| `netsh trace stop`                        | Arrête la capture de trafic réseau.                                         |
| `netsh int tcp show global`               | Affiche les paramètres globaux TCP.                                         |
| `netsh interface ip show neighbors`       | Affiche les voisins ARP pour les interfaces réseau.                         |

---

## 📘 Notes
- Les commandes nécessitent souvent des privilèges administratifs.
- Utilisez **`netsh /?`** ou **`help`** après une commande pour plus de détails.

---

### 🎯 Exemple pratique
Réinitialiser une configuration réseau complète :
```cmd
netsh int ip reset
netsh winsock reset all
ipconfig /release
ipconfig /renew
ipconfig /flushdns
```
