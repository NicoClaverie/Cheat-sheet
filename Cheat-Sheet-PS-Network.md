# 10 commandes pour configurer le réseau sous Windows avec PowerShell


## Obtenir la liste des interfaces réseau

```Get-NetAdapter```

Cette commande est capable de lister les adaptateurs Ethernet (RJ45 et Wi-Fi), mais aussi les adaptateurs Bluetooth. La liste retournée contient un ensemble de propriétés correspondantes à des caractéristiques de chaque interface réseau (nom, statut, adresse MAC, vitesse de connexion, etc.).

Pour obtenir la liste de toutes les interfaces réseau actives, nous pouvons filtrer la liste de cette façon :

```Get-NetAdapter | Where-Object { $_.Status -eq "Up" }```


## Renommer une interface réseau

```Rename-NetAdapter -Name Ethernet0 -NewName LAN```

## Activer, désactiver ou redémarrer une interface réseau

Avec PowerShell, nous allons pouvoir activer ou désactiver une interface réseau, mais aussi redémarrer une interface réseau. Windows contient les trois cmdlets suivants prévus à cet effet :

- **Enable-NetAdapter** : pour activer une interface réseau
- **Disable-NetAdapter** : pour désactiver une interface réseau
- **Restart-NetAdapter** : pour redémarrer une interface réseau

Désactiver l'interface réseau

```Disable-NetAdapter -Name LAN```

Activer l'interface réseau

```Enable-NetAdapter -Name LAN```

Redémarrer l'interface réseau

```Restart-NetAdapter -Name LAN```

`LAN` peux etre remplacé par le nom de l'interface ciblé

Verifier si l'action est passé

```(Get-NetAdapter -Name LAN).Status```

## Obtenir la configuration IP d'une interface

Le cmdlet "Get-NetIPConfiguration", dont l'alias est "gip", est une alternative à la célèbre commande MS-DOS "ipconfig".
```Get-NetIPConfiguration```  
```Get-NetIPConfiguration -All```


Si vous trouvez que ce cmdlet ne retourne pas assez d'informations, sachez que vous pouvez ajouter le paramètre "-Detailed".

```Get-NetIPConfiguration -Detailed```  
ou  
```gip -Detailed```  

Il permet d'afficher des propriétés supplémentaires relativement intéressantes, dont celles-ci :

- **NetProfile.NetworkCategory** : type de réseau, ce qui permet de savoir si l'on est sur un réseau public, privé ou de domaine.
- **NetProfile.IPv4Connectivity** : état de la connectivité IPv4, permet de savoir si la machine a accès à Internet via cette interface.
- **NetIPv4Interface.DHCP** : état du DHCP sur l'IPv4.
- **NetIPv6Interface.DHCP** : état du DHCP sur l'IPV6.
- **DNSServer** : l'adresse IP du serveur DNS.

En complément de ce cmdlet, nous pouvons utiliser "Get-NetIPAddress" qui présente l'avantage de lister toutes les adresses IP configurées sur la machine locale, en IPv4 et IPv6, ainsi que pour la boucle locale.

```Get-NetIPAddress```

Nous pouvons même générer un tableau récapitulatif de cette façon :

```Get-NetIPAddress | Sort-Object -Property InterfaceAlias | Format-Table InterfaceAlias, IPAddress, AddressFamily```

## Définir une adresse IPv4

Ceci implique d'utiliser ce cmdlet avec un ensemble de paramètres :

- Le paramètre **-InterfaceAlias** ou **-InterfaceIndex** pour préciser le nom de l'interface ou le numéro d'index de l'interface à configurer. Il est impératif de cibler l'interface par son nom ou le numéro d'index. Nous pouvons récupérer cette information avec le cmdlet **Get-NetAdapter**.
- Le paramètre **-IPAddress** pour indiquer l'adresse IPv4 à associer sur la carte réseau.
- Le paramètre **-PrefixLength** pour préciser la longueur du masque de sous-réseau (au format CIDR).
- Le paramètre **-DefaultGateway** pour préciser la passerelle par défaut (routeur)

Prenons un exemple : nous souhaitons définir l'adresse IP "192.168.14.50/24" sur la carte réseau "LAN". La passerelle par défaut sera "192.168.14.2". Voici la commande complète à exécuter :

```New-NetIPAddress -InterfaceAlias LAN -IPAddress 192.168.14.50 -PrefixLength 24 -DefaultGateway 192.168.14.2 -AddressFamily IPv4```


L'adresse IP sera immédiatement définie sur la carte réseau, et associée à deux magasins, "ActiveStore" et "PersistentStore". L'adresse IP sera donc persistante même après un redémarrage de la machine.

Par la suite, si vous souhaitez changer l'adresse IP sur cette interface, vous devez la supprimer, puis ajouter une nouvelle adresse IP. Ainsi, pour utiliser l'adresse IP "192.168.14.51" au lieu de "192.168.14.50", nous devons utiliser ces cmdlets :

```Remove-NetIPAddress -InterfaceAlias LAN -IPAddress 192.168.14.50```
```New-NetIPAddress -InterfaceAlias LAN -IPAddress 192.168.14.51```


## Définir un serveur DNS sur l'interface réseau

Pour définir des serveurs DNS nous devons utiliser deux cmdlets supplémentaires :

- **Get-DnsClientServerAddress** : pour obtenir la liste des serveurs DNS configurés sur chaque interface réseau de la machine.  
- **Set-DnsClientServerAddress** : pour définir une liste de serveurs DNS sur une interface réseau.  
Pour utiliser le premier cmdlet, il vous suffit de l'appeler sans préciser de paramètres (on peux néanmoins ajouter des paramètres).

```Get-DnsClientServerAddress```

La commande ci-dessous permet de définir les serveurs DNS ayant les adresses IP "192.168.14.10" et "192.168.14.11" sur l'interface nommée "LAN".  

```Set-DnsClientServerAddress -InterfaceAlias LAN -ServerAddresses ("192.168.14.10","192.168.14.11")```








https://www.it-connect.fr/chapitres/powershell-10-commandes-pour-configurer-le-reseau-sous-windows/
