# 10 commandes pour configurer le réseau sous Windows avec PowerShell

## Sommaire 
[Tableau](#1.-Tableau-récapitulatif)  
[Obtenir la liste des interfaces réseau](#2.-Obtenir-la-liste-des-interfaces-réseau)  




## 1. Tableau récapitulatif


## 2. Obtenir la liste des interfaces réseau

```
Get-NetAdapter
```

Cette commande est capable de lister les adaptateurs Ethernet (RJ45 et Wi-Fi), mais aussi les adaptateurs Bluetooth. La liste retournée contient un ensemble de propriétés correspondantes à des caractéristiques de chaque interface réseau (nom, statut, adresse MAC, vitesse de connexion, etc.).

Pour obtenir la liste de toutes les interfaces réseau actives, nous pouvons filtrer la liste de cette façon :

```
Get-NetAdapter | Where-Object { $_.Status -eq "Up" }
```


## 3) Renommer une interface réseau

```
Rename-NetAdapter -Name Ethernet0 -NewName LAN
```

## 4) Activer, désactiver ou redémarrer une interface réseau

Avec PowerShell, nous allons pouvoir activer ou désactiver une interface réseau, mais aussi redémarrer une interface réseau. Windows contient les trois cmdlets suivants prévus à cet effet :

- **Enable-NetAdapter** : pour activer une interface réseau
- **Disable-NetAdapter** : pour désactiver une interface réseau
- **Restart-NetAdapter** : pour redémarrer une interface réseau

Désactiver l'interface réseau

```
Disable-NetAdapter -Name LAN
```

Activer l'interface réseau

```
Enable-NetAdapter -Name LAN
```

Redémarrer l'interface réseau

```
Restart-NetAdapter -Name LAN
```

`LAN` peux etre remplacé par le nom de l'interface ciblé

Verifier si l'action est passé

```
(Get-NetAdapter -Name LAN).Status
```

## 5) Obtenir la configuration IP d'une interface

Le cmdlet "Get-NetIPConfiguration", dont l'alias est "gip", est une alternative à la célèbre commande MS-DOS "ipconfig".
```
Get-NetIPConfiguration
Get-NetIPConfiguration -All
```


Si vous trouvez que ce cmdlet ne retourne pas assez d'informations, sachez que vous pouvez ajouter le paramètre "-Detailed".

```
Get-NetIPConfiguration -Detailed
```  
ou  
```
gip -Detailed
```  

Il permet d'afficher des propriétés supplémentaires relativement intéressantes, dont celles-ci :

- **NetProfile.NetworkCategory** : type de réseau, ce qui permet de savoir si l'on est sur un réseau public, privé ou de domaine.
- **NetProfile.IPv4Connectivity** : état de la connectivité IPv4, permet de savoir si la machine a accès à Internet via cette interface.
- **NetIPv4Interface.DHCP** : état du DHCP sur l'IPv4.
- **NetIPv6Interface.DHCP** : état du DHCP sur l'IPV6.
- **DNSServer** : l'adresse IP du serveur DNS.

En complément de ce cmdlet, nous pouvons utiliser "Get-NetIPAddress" qui présente l'avantage de lister toutes les adresses IP configurées sur la machine locale, en IPv4 et IPv6, ainsi que pour la boucle locale.

```
Get-NetIPAddress
```

Nous pouvons même générer un tableau récapitulatif de cette façon :

```
Get-NetIPAddress | Sort-Object -Property InterfaceAlias | Format-Table InterfaceAlias, IPAddress, AddressFamily
```

## 6) Définir une adresse IPv4

Ceci implique d'utiliser ce cmdlet avec un ensemble de paramètres :

- Le paramètre **-InterfaceAlias** ou **-InterfaceIndex** pour préciser le nom de l'interface ou le numéro d'index de l'interface à configurer. Il est impératif de cibler l'interface par son nom ou le numéro d'index. Nous pouvons récupérer cette information avec le cmdlet **Get-NetAdapter**.
- Le paramètre **-IPAddress** pour indiquer l'adresse IPv4 à associer sur la carte réseau.
- Le paramètre **-PrefixLength** pour préciser la longueur du masque de sous-réseau (au format CIDR).
- Le paramètre **-DefaultGateway** pour préciser la passerelle par défaut (routeur)

Prenons un exemple : nous souhaitons définir l'adresse IP "192.168.14.50/24" sur la carte réseau "LAN". La passerelle par défaut sera "192.168.14.2". Voici la commande complète à exécuter :

```
New-NetIPAddress -InterfaceAlias LAN -IPAddress 192.168.14.50 -PrefixLength 24 -DefaultGateway 192.168.14.2 -AddressFamily IPv4
```


L'adresse IP sera immédiatement définie sur la carte réseau, et associée à deux magasins, "ActiveStore" et "PersistentStore". L'adresse IP sera donc persistante même après un redémarrage de la machine.

Par la suite, si vous souhaitez changer l'adresse IP sur cette interface, vous devez la supprimer, puis ajouter une nouvelle adresse IP. Ainsi, pour utiliser l'adresse IP "192.168.14.51" au lieu de "192.168.14.50", nous devons utiliser ces cmdlets :

```
Remove-NetIPAddress -InterfaceAlias LAN -IPAddress 192.168.14.50
New-NetIPAddress -InterfaceAlias LAN -IPAddress 192.168.14.51
```


## 7) Définir un serveur DNS sur l'interface réseau

Pour définir des serveurs DNS nous devons utiliser deux cmdlets supplémentaires :

- **Get-DnsClientServerAddress** : pour obtenir la liste des serveurs DNS configurés sur chaque interface réseau de la machine.  
- **Set-DnsClientServerAddress** : pour définir une liste de serveurs DNS sur une interface réseau.  
Pour utiliser le premier cmdlet, il vous suffit de l'appeler sans préciser de paramètres (on peux néanmoins ajouter des paramètres).

```
Get-DnsClientServerAddress
```

La commande ci-dessous permet de définir les serveurs DNS ayant les adresses IP "192.168.14.10" et "192.168.14.11" sur l'interface nommée **"LAN"**.  

```
Set-DnsClientServerAddress -InterfaceAlias LAN -ServerAddresses ("192.168.14.10","192.168.14.11")
```

## 8) Définir un suffixe DNS

En complément des adresses IP des serveurs DNS, il est fréquent de définir un suffixe DNS sur l'interface réseau connectée à un réseau d'entreprise, notamment en environnement Active Directory. Pour effectuer cette configuration, nous pouvons utiliser le cmdlet "Set-DnsClient".

L'exemple ci-dessous permet de définir le suffixe DNS "mon-reseau.local" sur l'interface nommée **"LAN"** :

```
Set-DnsClient -InterfaceAlias LAN -ConnectionSpecificSuffix mon-reseau.local
```

## 9) Tester la résolution de noms

Le cmdlet PowerShell "Resolve-DnsName" est une alternative à la commande "nslookup" qui va nous permettre d'effectuer de la résolution de noms.  

Voici quelques exemples d'utilisations.

- Résoudre le nom d'hôte **"google.fr"**

```
Resolve-DnsName google.fr
```

- Résoudre le nom d'hôte "google.fr" en sollicitant le serveur DNS "8.8.8.8"
```
Resolve-DnsName google.fr -Server 8.8.8.8
```

- Obtenir des informations sur le MX (messagerie) du domaine "google.fr"
```
Resolve-DnsName google.fr -Type MX
```

- Résoudre le nom d'hôte "google.fr" en s'appuyant uniquement sur les données présentes dans le cache DNS local
```
Resolve-DnsName it-connect.tech -CacheOnly
```

- Résoudre plusieurs noms d'hôtes avec une seule commande, en se concentrant sur les enregistrements IPv4 (type A) 
```
"google.com", "google.fr" | Resolve-DnsName -Type A
```

Pour IPv6 faire type AAAA
```
"google.com", "google.fr" | Resolve-DnsName -Type AAAA
```

## 10) Effectuer un test de connectivité

Plutot que la commande **Ping** nous pouvons utiliser la cmdlet **Test-Connection**

```
Test-Connection 1.1.1.1
```
Il est possible d'effectuer un ping vers plusieurs machines.

```
Test-Connection 1.1.1.1,8.8.8.8,google.fr
```
Nous pouvons aussi ajouter un compteur.
```
Test-Connection 1.1.1.1,8.8.8.8,google.fr -Count 1
```

## 11) Tester un port

Grâce au cmdlet **"Test-NetConnection"** de PowerShell, nous allons pouvoir effectuer un test sur un port spécifique (uniquement en TCP). Ceci permettra de déterminer si un port est ouvert ou non.  

Pour utiliser le cmdlet "Test-NetConnection", nous devons préciser deux paramètres :  

- **ComputerName** : le nom ou l'adresse IP de la cible.
- **Port** : le numéro de port à tester

```
Test-NetConnection -ComputerName google.fr -Port 443
```

Enfin, sachez que ce cmdlet supporte aussi le nom de certains services, ce qui évite de préciser le numéro de port.   
Pour effectuer un test sur le port "80", nous pouvons préciser le paramètre **"-CommonTCPPort"** avec la valeur **"HTTP"**

```
Test-NetConnection -ComputerName 1.1.1.1 -CommonTCPPort HTTP
```
Terminons par un bonus : si vous souhaitez afficher la liste de tous les ports sur lesquels écoute un serveur (ou un poste de travail), vous pouvez utiliser le cmdlet **"Get-NetTCPConnection"** de cette façon :
```
Get-NetTCPConnection -State Listen
```






## Sources

https://www.it-connect.fr/chapitres/powershell-10-commandes-pour-configurer-le-reseau-sous-windows/
