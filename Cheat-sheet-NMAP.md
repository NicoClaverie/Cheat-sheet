- [Nmap Switch Options](#nmap-switch-options)
  - [Target Specification](#target-specification)
  - [Port Specification](#port-specification)
  - [Service and Version Detection](#service-and-version-detection)
  - [Host Discovery](#host-discovery)
  - [NSE Scripts](#nse-scripts)
  - [OS Detection](#os-detection)
- [Version IT-connect](#version-it-connect)
  - [1. Présentation](#1-présentation)
  - [2. Nmap : CheatSheet IT-Connect](#2-nmap--cheatsheet-it-connect)
    - [2.1 Scan de port](#21-scan-de-port)
    - [2.2 Découverte des hôtes actifs](#22-découverte-des-hôtes-actifs)
    - [2.3 Détection de version](#23-détection-de-version)
    - [2.4 Les scripts NSE : recherche de vulnérabilité](#24-les-scripts-nse--recherche-de-vulnérabilité)
    - [2.5 Gestion de la sortie Nmap](#25-gestion-de-la-sortie-nmap)
    - [2.6 Optimisation des performances](#26-optimisation-des-performances)
    - [2.7 Les types de scan TCP](#27-les-types-de-scan-tcp)
  - [3. Conclusion](#3-conclusion)


# Nmap Switch Options

## Target Specification

| SWITCH     | EXAMPLE                        | DESCRIPTION              |
| ---------- | ------------------------------ | ------------------------ |
| (none)     | `nmap 192.168.1.1`             | Scan a single IP         |
| (none)     | `nmap 192.168.1.1 192.168.2.1` | Scan specific IPs        |
| (none)     | `nmap 192.168.1.1-254`         | Scan a range             |
| (none)     | `nmap scanme.nmap.org`         | Scan a domain            |
| (none)     | `nmap 192.168.1.0/24`          | Scan using CIDR notation |
| `-iL`      | `nmap -iL targets.txt`         | Scan targets from a file |
| `-iR`      | `nmap -iR 100`                 | Scan 100 random hosts    |
| `-exclude` | `nmap -exclude 192.168.1.1`    | Exclude listed hosts     |

---

## Port Specification

| SWITCH       | EXAMPLE                               | DESCRIPTION                                                           |
| ------------ | ------------------------------------- | --------------------------------------------------------------------- |
| `-p`         | `nmap 192.168.1.1 -p 21`              | Port scan for port x                                                  |
| `-p`         | `nmap 192.168.1.1 -p 21-100`          | Port range                                                            |
| `-p`         | `nmap 192.168.1.1 -p U:53,T:21-25,80` | Port scan multiple TCP and UDP ports                                  |
| `-p`         | `nmap 192.168.1.1 -p-`                | Port scan all ports                                                   |
| `-p`         | `nmap 192.168.1.1 -p http,https`      | Port scan from service name                                           |
| `-F`         | `nmap 192.168.1.1 -F`                 | Fast port scan (100 ports)                                            |
| `-top-ports` | `nmap 192.168.1.1 --top-ports 2000`   | Port scan the top x ports                                             |
| `-p-65535`   | `nmap 192.168.1.1 -p-65535`           | Leaving off end port in range makes the scan start at port 1          |
| `-p0-`       | `nmap 192.168.1.1 -p0-`               | Leaving off end port in range makes the scan go through to port 65535 |

---

## Service and Version Detection

| SWITCH                    | EXAMPLE                                      | DESCRIPTION                                                                |
| ------------------------- | -------------------------------------------- | -------------------------------------------------------------------------- |
| `-sV`                     | `nmap 192.168.1.1 -sV`                       | Attempts to determine the version of the service running on port           |
| `-sV --version-intensity` | `nmap 192.168.1.1 -sV --version-intensity 8` | Intensity level 0 to 9. Higher number increases possibility of correctness |
| `-sV --version-light`     | `nmap 192.168.1.1 -sV --version-light`       | Enable light mode. Lower possibility of correctness. Faster                |
| `-sV --version-all`       | `nmap 192.168.1.1 -sV --version-all`         | Enable intensity level 9. Higher possibility of correctness. Slower        |
| `-A`                      | `nmap 192.168.1.1 -A`                        | Enables OS detection, version detection, script scanning, and traceroute   |

---

## Host Discovery

| SWITCH | EXAMPLE                          | DESCRIPTION                                     |
| ------ | -------------------------------- | ----------------------------------------------- |
| `-sL`  | `nmap 192.168.1.1-3 -sL`         | No Scan. List targets only                      |
| `-sn`  | `nmap 192.168.1.1/24 -sn`        | Disable port scanning. Host discovery only      |
| `-Pn`  | `nmap 192.168.1.1-5 -Pn`         | Disable host discovery. Port scan only          |
| `-PS`  | `nmap 192.168.1.1-5 -PS22-25,80` | TCP SYN discovery on port x. Port 80 by default |
| `-PA`  | `nmap 192.168.1.1-5 -PA22-25,80` | TCP ACK discovery on port x. Port 80 by default |
| `-PU`  | `nmap 192.168.1.1-5 -PU53`       | UDP discovery on port x. Port 40125 by default  |
| `-PR`  | `nmap 192.168.1.1/24 -PR`        | ARP discovery on local network                  |
| `-n`   | `nmap 192.168.1.1 -n`            | Never do DNS resolution                         |

---

## NSE Scripts

| SWITCH            | EXAMPLE                                                                     | DESCRIPTION                                                             |
| ----------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `-sC`             | `nmap 192.168.1.1 -sC`                                                      | Scan with default NSE scripts. Considered useful for discovery and safe |
| `-script default` | `nmap 192.168.1.1 --script default`                                         | Scan with default NSE scripts. Considered useful for discovery and safe |
| `-script`         | `nmap 192.168.1.1 --script=banner`                                          | Scan with a single script. Example banner                               |
| `-script`         | `nmap 192.168.1.1 --script=http*`                                           | Scan with a wildcard. Example http                                      |
| `-script`         | `nmap 192.168.1.1 --script http,banner`                                     | Scan with two scripts. Example http and banner                          |
| `-script`         | `nmap 192.168.1.1 --script "not intrusive"`                                 | Scan default, but remove intrusive scripts                              |
| `-script-args`    | `nmap --script snmp-sysdescr --script-args snmpcommunity=admin 192.168.1.1` | NSE script with arguments                                               |

---

## OS Detection

| SWITCH              | EXAMPLE                                | DESCRIPTION                                                                                          |
| ------------------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `-O`                | `nmap 192.168.1.1 -O`                  | Remote OS detection using TCP/IP stack fingerprinting                                                |
| `-O --osscan-limit` | `nmap 192.168.1.1 -O --osscan-limit`   | If at least one open and one closed TCP port are not found it will not try OS detection against host |
| `-O --osscan-guess` | `nmap 192.168.1.1 -O --osscan-guess`   | Makes Nmap guess more aggressively                                                                   |
| `-O --max-os-tries` | `nmap 192.168.1.1 -O --max-os-tries 1` | Set the maximum number x of OS detection tries against a target                                      |
| `-A`                | `nmap 192.168.1.1 -A`                  | Enables OS detection, version detection, script scanning, and traceroute                             |


# Version IT-connect


## 1. Présentation  
Je vous propose dans ce chapitre un court récapitulatif des nombreuses commandes et cas d’usage de Nmap afin que vous puissiez rapidement retrouver et réutiliser ces commandes dans votre usage quotidien.

## 2. Nmap : CheatSheet IT-Connect  
Voici donc un pense-bête ou “cheatsheet” des commandes vues dans le cours. N’hésitez pas à revenir sur cette page si vous avez oublié une commande !

### 2.1 Scan de port
```
# Affichage de la version de Nmap installée
nmap –version

# Scan des ports ouverts spécifiques sur une seule adresse IP
nmap --open -p 80 192.168.1.18

# Scan des ports TCP sur une sélection choisie de ports
nmap 192.168.1.19 -p 80
nmap 192.168.1.19 -p 22,80,1000-2000,3389

# Scan des services UDP sur une adresse IP 
nmap -sU 192.168.1.19

# Scan des services UDP sur des ports spécifiques
nmap -sU 192.168.1.19 -p 161,23

# Scan des services TCP des 100 premiers ports les plus couramment utilisés
nmap 192.168.1.19 --top-ports 100

# Scan de tous les ports sur une adresse IP 
nmap 192.168.1.19 -p-

# Scan de plusieurs sous-réseaux avec spécification des ports à scanner
nmap 192.168.0.0/24 192.168.1.0/24 -p 22

# Scan d'un sous-réseau avec exclusion d'une adresse IP spécifique et scan de tous les ports
nmap 192.168.0.0/24 --exclude 192.168.0.4 -p-
```
### 2.2 Découverte des hôtes actifs
```
# Scan sur des CIDR ou plage IP
nmap 192.168.0.0/24
nmap 192.168.0.0/24 192.168.1.0/24
nmap 192.168.1.2 192.168.1.3 192.168.1.10-20
nmap 192.168.0.0/24 192.168.1.3 192.168.1.10-20

# Scan de découverte des hôtes actifs (Ping Scan) sur un réseau
nmap -sP 192.168.1.0/24

# Scan de découverte des hôtes actifs sans scan de ports
nmap 192.168.1.0/24 -sn

# Scan de découverte des hôtes actifs (Ping Scan) sur un réseau local avec différentes techniques de sondage
nmap -sn -PP -PS22,3389,445,139 -PA80 192.168.1.0/24

# Scan des hôtes spécifiés dans un fichier texte
nmap -iL /tmp/mesCibles.txt

# Scan réseau avec exclusion d'une adresse IP spécifique
nmap 192.168.1.0/24 --exclude 192.168.1.140

# Scan d'un sous-réseau avec exclusion d'un autre sous-réseau
nmap 10.0.0.0/16 --exclude-host 10.0.100.0/24
```
### 2.3 Détection de version
```
# Activer la détection de version
nmap 192.168.1.0/24 -sV

# Détection de version + traces avancées
nmap 192.168.1.0/24 -sV –version-trace

# Détection de version avec probres de rarity 2 maximum
nmap 192.168.1.0/24 -sV --version-intensity 2

# Détection de version avec tous les probes
nmap 192.168.1.0/24 -sV --version-intensity 9

# Activer la détection de système d'exploitation
nmap -O 10.10.10.0/24
```
### 2.4 Les scripts NSE : recherche de vulnérabilité
```
# Activer l'utiliser des scripts NSE de catégorie "default"
nmap -sC 10.10.10.152

# Scan de tous les ports TCP et scripts NSE
nmap -sC -p- 10.10.10.152

# Affichage de l'aide en fonction du nom des scripts
nmap –script-help=ftp-*

# Affichage de l'aide en fonction de la catégorie
nmap --script-help=discovery

# Utilisation des scripts NSE d'une catégorie choisie
nmap --script default 10.10.10.152
nmap --script discovery 10.10.10.152

# Filtre d'inclusion/exclusion des catégories sur les scripts NSE
nmap --script “discovery and safe” 10.10.10.152
nmap --script “not intrusive and not dos” 10.10.10.152
nmap --script “vuln and not intrusive and not dos” 10.10.10.152
nmap --script “(http and vuln) and not intrusive and not dos” 10.10.10.152

# Exécution d'un script NSE précie
nmap --script ftp-anon -p 21 10.10.10.152
nmap --script ftp-anon 10.10.10.152

# Passage d'argument à un script NSE
nmap --script ssh-brute --script-args userdb=/tmp/userlist,passdb=/tmp/passlist 10.10.10.245 192.168.1.19
```
### 2.5 Gestion de la sortie Nmap
```
# Enregistrement dans un fichier texte 
nmap 10.10.10.0/24 -sV -oN nmap_scan_10.10.10.0_24.txt

# Enregistrement dans un fichier texte au format condensé
nmap 10.10.10.0/24 -sV -oG nmap_scan_10.10.10.0_24.gnmap

# Enregistrement dans un fichier XML
nmap 10.10.10.0/24 -sV -oX nmap_scan_10.10.10.0_24.xml
```
### 2.6 Optimisation des performances
```
# Scan de détection de version avec un débit maximal de 300 paquets par seconde
nmap -sV 10.10.10.0/24 --max-rate 300

# Scan de détection de version avec exécution de scripts par défaut, aucune tentative de réessaie et un délai d'attente maximal de 15 minutes par hôte
nmap -sV -sC 10.10.10.0/24 --max-retries 0 --host-timeout 15m

# Scan de détection de version avec les 2000 premiers ports les plus couramment utilisés, une vitesse de scan agressive (T4), et une sortie de débogage
nmap 10.10.10.0/24 -sV --top-ports 2000 -T4 -d
```
### 2.7 Les types de scan TCP
```
# Scan TCP SYN (rapide, peu discret)
nmap -sS 192.168.1.15

# Scan TCP Connect (classique)
nmap -sT 192.168.1.15

# Scan TCP FIN (discret)
nmap -sF 192.168.1.15

# Scan TCP XMAS
nmap -sX 192.168.1.15

# Scan TCP Null
nmap -sN 192.168.1.15

# Scan TCP ACK (détecter un pare-feu)
nmap -sA 192.168.1.15
```
J’espère que ces différentes commandes vous serviront. Bien sûr, n’oubliez pas de modifier la cible des scans dans votre contexte et de vous référer au contenu du cours pour être sûr de maîtriser les tests que vous réalisez.

## 3. Conclusion
Nous avons fini notre cours sur Nmap ! J’espère que son contenu vous a plu et qu’il vous a permis de maîtriser cet outil complet et puissant. Bien sûr, je vous conseille de manipuler l’outil dans un environnement maîtrisé (Hack The Box, VulnHub, VM) avant de l’utiliser en conditions réelles.

Il y a encore beaucoup à dire sur le fonctionnement interne de l’outil ainsi que nombre de fonctionnalités à explorer. Cependant, nous avons parcouru les bases (et même un peu plus) et cela est largement suffisant pour être plus confiant sur l’utilisation de Nmap et l’interprétation de ses résultats.


https://www.it-connect.fr/chapitres/nmap-cheatsheet-recapitulatif-des-commandes/